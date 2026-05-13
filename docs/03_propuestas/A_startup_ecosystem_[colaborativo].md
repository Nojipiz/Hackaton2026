# Propuesta A — Startup Ecosystem Builder

## Concepto

> Todos los equipos participan primero en una sesión de **System Design colaborativo** para diseñar la arquitectura de un único producto (ej: una plataforma para resolver un problema de la región). Luego, cada equipo se convierte en una "startup" encargada de construir uno de los microservicios core. Los servicios se integran en vivo. La competencia se centra en el pitch final: el ganador es el equipo que presente la mejor propuesta de valor, demostrando que su componente es la pieza más vital del ecosistema construido.

---

## Tagline sugerido

**"Construyendo juntos el próximo gran producto."**

---

## Por qué es un ecosistema colaborativo

Todos los equipos trabajan en la construcción de un único producto final (ej: una plataforma de transporte urbano para Tunja, o un sistema de gestión académica). El desafío inicial consiste en realizar un **System Design colaborativo** donde se define la arquitectura y los microservicios necesarios. Luego, cada equipo asume la responsabilidad de construir uno de esos microservicios.

La competencia no es técnica entre servicios, sino de **visión y producto**: al final, cada equipo presenta su "pitch" defendiendo por qué su componente es el corazón del producto y cómo su implementación técnica aporta el mayor valor al sistema completo.

---

## Mecánica del evento (5 horas)

### Fase 1 — Setup, Acuerdos y Diseño del ecosistema (45 min)

**14:00–14:30 — Problemática y System Design colaborativo:**

Los organizadores revelan el gran problema a resolver. **Ejemplos de problemas para el System Design:**

| Categoría              | Problema a resolver                                                                                                                         | Posible Producto Final                                                 |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| **Movilidad**          | Rutas, horarios y aglomeración en transporte público / terminales de Tunja (A nivel de toda la ciudad, integrando semáforos, buses y taxis) | Plataforma inteligente de tráfico y movilidad ciudadana                |
| **Educación**          | Gestión académica estudiantil UPTC extendida a toda la red universitaria (múltiples sedes, biblioteca departamental, convenios)             | Red universitaria unificada y portal de servicios educativos de Boyacá |
| **Comercio Local**     | Digitalización de pequeños negocios y cadena de suministro de todo el centro histórico y zonas comerciales de Tunja                         | Sistema logístico y marketplace B2B/B2C para la economía de la ciudad  |
| **Economía Agrícola**  | Un "Uber Eats" directo para todas las plazas de mercado de Boyacá y conexión con agricultores regionales                                    | Plataforma departamental agro-logística "Del Campo a la Puerta"        |
| **Gestión de Riesgos** | Información ciudadana y coordinación de recursos durante emergencias a nivel municipal (terremotos, inundaciones, red de agua)              | Centro de comando ciudadano y app de emergencias en tiempo real        |

Se abre una sesión express de **System Design en pizarra con todos los equipos** para dividir la solución en microservicios independientes pero interconectados.

| Rol ejemplo (asignado tras el diseño) | Qué expone                             |
| ------------------------------------- | -------------------------------------- |
| AuthService                           | Login, tokens, validación de identidad |
| PaymentsService                       | Procesar cobros, verificar saldo       |
| Logistics/RoutesService               | Cálculos de rutas y tiempos            |
| AnalyticsService                      | Eventos, métricas, reportes            |
| StorageService                        | Subir archivos, recuperar datos        |

**14:30–14:45 — Acuerdo de Contratos (API Contracts):**

Antes de tirar código, todos los equipos acuerdan las **interfaces** de comunicación:
- Rutas de API (ej. `POST /auth/login → { token }`)
- Formato de respuestas (JSON estándar acordado)
- Errores esperados (ej. `401`, `404`, estructura del error)

Los organizadores proveen un doc de contratos en blanco. Los equipos lo llenan juntos. Una vez firmado, no se cambia unilateralmente. Si un equipo cambia la interfaz sin avisar, recibe penalización.

**14:45–15:00 — Deploy inicial:**

- Fork de plantilla base (Node.js/FastAPI en Railway)
- Deploy del esqueleto vacío — la URL debe estar viva antes de que empiece el build
- Registro de URLs en doc compartido del árbitro

---

### Fase 2 — Build Phase y Live Ecosystem (3 horas)

**15:00–18:00 — Construcción e integración en vivo**

Cada equipo implementa su API. Requisitos mínimos:

```
GET  /health           → { status: "ok", service: "AuthService" }
POST /[acción principal] → lógica real del servicio
GET  /metrics          → { requests_served: N, uptime_seconds: N }
```

**Dependencias entre servicios:**

- Cada servicio debe hacer al menos **1 llamada real** a otro servicio durante la operación.
- El árbitro hace llamadas periódicas a todos los servicios y publica métricas en pantalla.

**Check-ins del Árbitro (Bot de Tráfico):**
- **16:00:** ¿Tu endpoint base responde? (`GET /health`)
- **17:00:** ¿Tu endpoint principal retorna datos con el formato acordado?
- **18:00:** ¿Pasas las pruebas del generador de tráfico que simulan a otros servicios?

**Tráfico en vivo (Simulación del ecosistema):**

El árbitro (sistema de los organizadores) envía tráfico real a todos los servicios en secuencia a lo largo de toda la fase de construcción, simulando usuarios usando la plataforma en tiempo real. Es responsabilidad de los organizadores desarrollar a la par (o tener preparado) un script generador de tráfico ficticio (bot) que consuma los endpoints principales del ecosistema a medida que los equipos los van desplegando. 

El marcador en pantalla muestra en tiempo real durante todo el evento:

| Equipo          | Uptime | Req/s servidos | Dependientes activos | Puntos |
| --------------- | ------ | -------------- | -------------------- | ------ |
| AuthService     | 99%    | 240            | 3 equipos            | 🟢     |
| PaymentsService | 87%    | 180            | 2 equipos            | 🟡     |
| ...             |        |                |                      |        |

**Reglas del tráfico:**

- Máximo 100 req/s por servicio.
- El árbitro no supera este límite nunca.
- No hay tráfico de equipo a equipo fuera del ecosistema definido.

**AI permitida:**

- Generación de código: ✅
- Scaffolding, boilerplate, tests: ✅
- El árbitro puede pedir que expliques cualquier función en el pitch: actúa en consecuencia

---

### Fase 3 — The Great Integration (45 min)

**18:00–18:45 — Integración final del ecosistema**

Los equipos tienen **45 minutos** para conectar y estabilizar todas las piezas finales del sistema.
- Es el momento de la verdad donde los servicios deben comunicarse según los contratos firmados en la Fase 1.
- Si un servicio no conecta bien o un contrato fue roto, los equipos negocian en vivo — puede haber hotfixes de emergencia.
- Los organizadores y árbitros proyectan en pantalla un diagrama en vivo mostrando qué servicios logran integrarse exitosamente con los demás.

---

### Fase 4 — Demo del Sistema y Pitches Individuales (30 min)

**18:45–19:15 — Demo Final Colectiva (Sistema de Punta a Punta)**

- **La prueba de fuego:** Un organizador intenta usar la plataforma completa (ej: simula un usuario registrándose y pidiendo un viaje).
- Si la plataforma funciona de punta a punta, hay puntaje colectivo para todos.
- Si una pieza falla y bloquea el flujo, el equipo responsable debe admitirlo y explicar qué pasó. No hay segunda oportunidad en esta fase.

**19:15–20:00 — Pitches Individuales**

Cada equipo tiene **5-7 min** para defender su microservicio:

| Tiempo | Contenido                                                                                                                                                                         |
| ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2 min  | Demo técnica: el link abre, el endpoint principal funciona y responde                                                                                                             |
| 3 min  | Pitch del producto: por qué su componente es crítico para resolver el problema general (ej: "Sin nuestro motor de rutas en tiempo real, la plataforma de transporte no funciona") |
| 1 min  | Análisis de Fallos: "Qué le falló al sistema en la integración y qué haríamos diferente" (si aplica) |
| 1 min  | Preguntas del jurado                                                                                                                                                              |

---

## Puntuación

### Puntuación colectiva (aplicada a todos los equipos por igual)

| Criterio                               | Peso | Descripción                                                                                 |
| -------------------------------------- | ---- | ------------------------------------------------------------------------------------------- |
| Sistema funciona de punta a punta      | 20%  | ¿El flujo completo corrió sin errores críticos en la gran integración?                       |

### Puntuación individual (por equipo)

| Criterio                               | Peso | Descripción                                                                                 |
| -------------------------------------- | ---- | ------------------------------------------------------------------------------------------- |
| Integración técnica y Uptime           | 30%  | ¿El servicio funcionó bajo estrés, cumplió los contratos y fue integrado por otros?                  |
| Calidad del pitch y propuesta de valor | 30%  | ¿Convencen de que su componente es el corazón del producto? ¿Entienden el problema general? |
| Diseño colaborativo (System Design)    | 10%  | Aporte a la arquitectura global y capacidad de trabajar con otros equipos                   |
| Implementación técnica                 | 10%  | Manejo de errores, `/health`, `/metrics`, código legible                                    |

**Puntaje final = 20% colectivo + 80% individual**

---

## Roles naturales para equipos de 3 personas

| Perfil             | Qué hace                                                                                                |
| ------------------ | ------------------------------------------------------------------------------------------------------- |
| **Backend**        | Diseña e implementa la API, maneja el deploy en Railway                                                 |
| **Integrador**     | Se encarga de llamar a los servicios de otros equipos, maneja errores de red                            |
| **Ventas / pitch** | Define la propuesta de valor del servicio, lidera el pitch, convence a otros equipos de integrar su API |

El perfil de ventas tiene trabajo real durante el build: **convencer a otros equipos de que llamen tu API** — eso sube el puntaje de dependientes.

---

## Infraestructura necesaria (organizadores)

- Árbitro: script Node.js que llama a todos los `/health` y endpoints principales cada 30s
- Dashboard: tabla simple en pantalla con métricas en vivo (puede ser una web básica)
- Doc compartido: spreadsheet con URLs de cada equipo
- Plantillas base: Node.js + Express o Python + FastAPI listas para Railway

---

## Preparación requerida (organizadores)

- [ ] Preparar 3 problemas reales (ej: movilidad, gestión académica) para presentar al inicio
- [ ] Preparar tablero para la sesión de System Design colaborativo
- [ ] Preparar plantillas de repo con `/health` y `/metrics` ya implementados
- [ ] Preparar el árbitro: script que llama a todos los servicios periódicamente y **generador de tráfico ficticio (bot) simulando uso real de la plataforma.**
- [ ] Preparar el dashboard de métricas en vivo (puede ser tan simple como una web con auto-refresh)

---

## Por qué funciona para el 30° aniversario UPTC

- Enseña System Design y arquitectura de software orientada a servicios en tiempo real
- Fomenta la colaboración extrema entre equipos — todos están construyendo un solo producto final para resolver un problema de la región
- El rol de pitch no es vender "humo", sino defender la importancia de su componente técnico dentro de la arquitectura
- 3 personas caben perfectamente: Backend (construye), Integrador (conecta con otros equipos), Producto/Pitch (entiende la visión completa)

---

## Variante: "El Pivot Forzado"

A mitad del build, el árbitro anuncia que **dos servicios deben fusionarse** (ej: Auth + Payments se convierten en "IdentityPay"). Los equipos afectados tienen 20 min para mergear sus APIs. Simula adquisiciones y reestructuraciones reales.
