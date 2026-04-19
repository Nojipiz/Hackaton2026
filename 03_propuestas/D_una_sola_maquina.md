# Propuesta D — Una Sola Máquina

## Concepto

> Todos los equipos construyen piezas de **un mismo sistema**. Al final del build, las piezas deben conectarse y funcionar juntas. La demo final no es por equipo — es todo el sistema corriendo en vivo. Luego cada equipo hace su pitch explicando su pieza y cómo encajó en el todo.

---

## Tagline sugerido

**"Nadie gana solo. El sistema gana o el sistema falla."**

---

## Por qué es diferente a las otras propuestas

Las otras propuestas son competitivas: cada equipo construye algo aislado y se compara con los demás. Esta es **cooperativa-competitiva**: todos dependen de que el otro entregue. Si tu pieza falla, el sistema entero falla. Si tu API tiene una interfaz rara, los demás no pueden conectarse. El éxito colectivo es el juicio principal — y dentro de eso se evalúa la calidad individual.

---

## El sistema base: "Campus Connect"

*(Ejemplo — los organizadores pueden elegir otro)*

Un sistema para la UPTC con 5 módulos independientes:

| Módulo | Qué hace | Stack sugerido |
|---|---|---|
| **Auth** | Login, sesiones, tokens JWT | Node/Express o FastAPI |
| **Perfil Académico** | Datos del estudiante, materias, horario | cualquier BE |
| **Notificaciones** | Alertas de eventos, recordatorios | cualquier BE |
| **Tablero de Anuncios** | Posts de profesores / admin | cualquier BE |
| **Dashboard FE** | UI que consume todos los demás | React / Vue / cualquier FE |

---

## Mecánica del evento

### Fase 0 — Acuerdo de contratos (15:00–15:30)

Antes de que cada equipo escriba una sola línea de código, todos acuerdan las **interfaces**:

- Rutas de API (ej. `POST /auth/login → { token }`)
- Formato de respuestas (JSON estándar acordado)
- Errores esperados (ej. `401`, `404`, estructura del error)

Los organizadores proveen un doc de contratos en blanco. Los equipos lo llenan juntos en 30 min. Una vez firmado, no se cambia — si tu equipo cambia la interfaz sin avisar, el equipo que depende de ti puede reclamar puntos de penalización.

### Fase 1 — Build independiente (15:30–18:30)

Cada equipo construye su módulo en aislamiento, siguiendo los contratos firmados.

**Puntos de check-in de los organizadores:**
- 16:30: ¿Tu endpoint base responde? (`GET /health`)
- 17:30: ¿Tu endpoint principal retorna datos con el formato acordado?
- 18:30: ¿Pasas los tests de integración básicos del árbitro?

### Fase 2 — Integración (18:30–19:00)

Los equipos tienen **30 minutos** para conectar todas las piezas.

- El equipo de FE integra contra todos los BE
- Los BE se llaman entre sí donde sea necesario (ej. Auth valida tokens para los demás)
- Si algo no conecta, los equipos negocian en vivo — puede haber hotfixes rápidos

Este es el momento más caótico y más emocionante del evento. Los organizadores lo proyectan en pantalla.

### Fase 3 — Demo del sistema completo (19:00–19:30)

Un representante de cada equipo, de pie, frente al sistema en pantalla.

El organizador usa el sistema como un usuario real:

1. Login → Auth
2. Ver perfil → Perfil Académico
3. Revisar anuncios → Tablero
4. Recibir notificación → Notificaciones
5. Todo visible en el Dashboard FE

Si una pieza falla en la demo en vivo, el equipo responsable lo admite y explica. No hay edición.

### Fase 4 — Pitches individuales (19:30–20:40)

Cada equipo tiene 8 min para su pitch individual:

| Tiempo | Contenido |
|---|---|
| 2 min | "Qué era nuestra pieza y por qué importa en el sistema" |
| 3 min | "Las decisiones técnicas que tomamos y por qué" |
| 2 min | "Qué le falló al sistema y qué haríamos diferente" |
| 1 min | Pregunta del jurado |

---

## Puntuación

### Puntuación colectiva (aplicada a todos los equipos por igual)

| Criterio | Peso grupal | Descripción |
|---|---|---|
| Sistema funciona de punta a punta en la demo | 30% | ¿El flujo completo corrió sin errores críticos? |

### Puntuación individual (por equipo)

| Criterio | Peso individual | Descripción |
|---|---|---|
| Módulo propio funciona y pasa tests del árbitro | 25% | Calidad técnica de la pieza |
| Respetó los contratos acordados | 20% | Sin cambios unilaterales, sin sorpresas |
| Pitch — claridad y propuesta de valor del módulo | 25% | ¿Por qué esta pieza es crítica? |

**Puntaje final = 30% colectivo + 70% individual**

---

## Roles naturales para equipos de 3 personas

| Perfil | Qué hace |
|---|---|
| **Técnico 1** | Implementa el módulo BE / la lógica principal |
| **Técnico 2** | Tests, integración con otros módulos, manejo de errores |
| **Comunicación** | Negocia los contratos en Fase 0, lidera el pitch, documenta el módulo |

El perfil de comunicación tiene un rol crítico en la **Fase 0**: es quien negocia las interfaces con los demás equipos. Una interfaz mal negociada es responsabilidad del equipo.

---

## Infraestructura necesaria (organizadores)

- Doc de contratos compartido (Google Doc o Notion) — plantilla preparada
- Árbitro: script que hace requests a todos los módulos con el formato acordado y reporta éxito/fallo
- Sistema base definido antes del evento (qué módulos, qué rutas mínimas)
- Plantillas de repo por módulo (Node, Python, React) listas para fork

---

## Preparación requerida (organizadores)

- [ ] Definir el sistema y los módulos antes del evento
- [ ] Preparar el doc de contratos con las rutas mínimas ya pre-llenadas (los equipos solo agregan detalles)
- [ ] Preparar tests de integración básicos por módulo (el árbitro los corre en el check-in de 18:30)
- [ ] Definir reglas claras para hotfixes en la Fase de Integración

---

## Por qué funciona para el 30° aniversario UPTC

- Simula trabajo real en equipo a escala — la integración es siempre la parte dura
- El momento de integración (18:30–19:00) es el más emocionante y representativo de lo que es ser ingeniero
- El pitch no es "mira lo que hice" — es "mira cómo mi pieza habilita a las demás"
- Celebra la colaboración además de la competencia
- El fallo colectivo enseña más que el éxito individual

---

## Variante: "Integración ciega"

Durante el build, los equipos no pueden ver el código de los demás — solo la especificación de contratos. La integración en Fase 2 es la primera vez que prueban conectarse. Más caos, más realismo.
