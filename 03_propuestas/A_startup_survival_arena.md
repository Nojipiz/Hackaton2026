# Propuesta A — Startup Survival Arena

## Concepto

> Cada equipo construye un microservicio que representa una "startup" dentro de un ecosistema compartido. Los servicios se llaman entre sí. Si tu servicio cae, los equipos que dependían de ti lo sienten. El ganador no es el que destruye a los demás — es el que resulta más crítico para el ecosistema y sobrevive.

---

## Tagline sugerido

**"En el ecosistema, el más dependido gana."**

---

## Por qué no es un ataque entre equipos

Los servicios se llaman entre sí bajo **cuotas estrictas de tráfico**. No hay mecánica de spam ni de intención destructiva — hay dependencias de negocio. Si tu servicio cae, tus "clientes" (otros equipos) quedan expuestos. La presión viene del volumen legítimo del ecosistema, no de ataques.

---

## Mecánica del evento (4 horas)

### Fase 1 — Setup y diseño del ecosistema (45 min)

**14:00–14:20 — Asignación de roles de startup:**

Los organizadores revelan el ecosistema en el que van a operar. Cada equipo recibe un rol de "startup":

| Rol ejemplo | Qué expone |
|---|---|
| AuthService | Login, tokens, validación de identidad |
| PaymentsService | Procesar cobros, verificar saldo |
| NotificationsService | Emails, alertas, mensajes |
| AnalyticsService | Eventos, métricas, reportes |
| StorageService | Subir archivos, recuperar datos |

Los equipos eligen o se les asigna uno. El ecosistema completo tiene sentido como plataforma SaaS ficticia.

**14:20–14:45 — Deploy inicial:**
- Fork de plantilla base (Node.js/FastAPI en Railway)
- Deploy del esqueleto vacío — la URL debe estar viva antes de que empiece el build
- Registro de URLs en doc compartido del árbitro

---

### Fase 2 — Build Phase (2h 15min)

**14:45–17:00 — Construcción del servicio**

Cada equipo implementa su API. Requisitos mínimos:

```
GET  /health           → { status: "ok", service: "AuthService" }
POST /[acción principal] → lógica real del servicio
GET  /metrics          → { requests_served: N, uptime_seconds: N }
```

**Dependencias entre servicios:**
- Cada servicio debe hacer al menos **1 llamada real** a otro servicio durante operación
- El árbitro hace llamadas periódicas a todos los servicios y publica métricas en pantalla

**AI permitida:**
- Generación de código: ✅
- Scaffolding, boilerplate, tests: ✅
- El árbitro puede pedir que expliques cualquier función en el pitch: actúa en consecuencia

---

### Fase 3 — Live Ecosystem (30 min)

**17:00–17:30 — El árbitro activa el ecosistema a plena carga**

El árbitro envía tráfico real a todos los servicios en secuencia, simulando usuarios usando la plataforma. El marcador en pantalla muestra en tiempo real:

| Equipo | Uptime | Req/s servidos | Dependientes activos | Puntos |
|---|---|---|---|---|
| AuthService | 99% | 240 | 3 equipos | 🟢 |
| PaymentsService | 87% | 180 | 2 equipos | 🟡 |
| ... | | | | |

**Reglas del tráfico:**
- Máximo 100 req/s por servicio
- El árbitro no supera este límite nunca
- No hay tráfico de equipo a equipo fuera del ecosistema definido

---

### Fase 4 — Pitches (45 min)

**17:30–18:00 (o hasta las 20:00 según el día)**

Cada equipo tiene **8–10 min:**

| Tiempo | Contenido |
|---|---|
| 2 min | Demo: el link abre, se muestra el endpoint principal funcionando |
| 3 min | Pitch: "somos [X startup], resolvemos [Y problema], así funcionamos" |
| 2 min | "¿Por qué los demás deberían depender de nosotros?" (argumento de ventas técnico) |
| 2 min | Preguntas del jurado |

---

## Puntuación

| Criterio | Peso | Descripción |
|---|---|---|
| Uptime durante el Live Ecosystem | 30% | % de requests del árbitro que respondieron con éxito |
| Número de equipos que integraron su servicio | 20% | Cuántos llamaron tu API durante el build |
| Calidad del pitch y propuesta de valor | 30% | ¿Convence? ¿El equipo entiende lo que construyó? |
| Implementación técnica | 20% | Manejo de errores, `/health`, `/metrics`, código legible |

---

## Roles naturales para equipos de 3 personas

| Perfil | Qué hace |
|---|---|
| **Backend** | Diseña e implementa la API, maneja el deploy en Railway |
| **Integrador** | Se encarga de llamar a los servicios de otros equipos, maneja errores de red |
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

- [ ] Definir el ecosistema de startups (5 roles, 1 por equipo)
- [ ] Escribir la historia del ecosistema (1 párrafo que dé contexto a los participantes)
- [ ] Preparar plantillas de repo con `/health` y `/metrics` ya implementados
- [ ] Preparar el árbitro: script que llama a todos los servicios periódicamente
- [ ] Preparar el dashboard de métricas en vivo (puede ser tan simple como una web con auto-refresh)

---

## Por qué funciona para el 30° aniversario UPTC

- Refleja arquitectura de microservicios real — tema central en la industria
- El rol de ventas es estructuralmente necesario: convencer a otros de integrarte es mecánica del juego
- AI acelera el scaffolding sin reemplazar el pensamiento de diseño
- 3 personas caben perfectamente: BE, integrador, ventas
- Competitivo sin ser destructivo — la presión viene del ecosistema, no del sabotaje

---

## Variante: "El Pivot Forzado"

A mitad del build, el árbitro anuncia que **dos servicios deben fusionarse** (ej: Auth + Payments se convierten en "IdentityPay"). Los equipos afectados tienen 20 min para mergear sus APIs. Simula adquisiciones y reestructuraciones reales.
