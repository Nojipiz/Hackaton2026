# Propuesta C — Terrible Ideas, Brutal Reality

## Concepto

> Cada equipo propone una idea de startup intencionalmente mala. Los demás equipos actúan como "el mundo real" y le imponen restricciones brutales. Luego tienes que construirla de todas formas. IA permitida — pero tienes que entender lo que shipeas.

---

## Tagline sugerido

**"Si sobrevive a las restricciones, merece existir."**

---

## Mecánica del evento (4 horas)

### Fase 1 — Bad Pitch Round (30 min)

Cada equipo tiene **2 minutos** para pitchear su idea terrible.

Reglas del pitch:
- La idea debe ser real pero obviamente flawed
- Más confianza = mejor
- El jurado puntúa qué tan *convencidamente mala* suena

**Ejemplos de calibración:**
- "Duolingo pero para aprender a mentir"
- "Tinder para conseguir compañeros de grupo en UPTC"
- "Blockchain para el carnet universitario"
- "App de domicilios solo para pisos impares"
- "IA que le escribe los correos al profesor pidiendo prórroga"

---

### Fase 2 — Constraint Attack (30 min)

Después de cada pitch, los otros equipos atacan con restricciones.

**Cada equipo puede imponer:**
- 1 restricción técnica
- 1 restricción de negocio

**Restricciones técnicas válidas (ejemplos):**
- Sin base de datos
- Debe funcionar offline
- Tiempo de respuesta < 200ms globalmente
- Solo puede usar tecnologías de 2010 o antes
- El frontend solo puede ser texto plano

**Restricciones de negocio válidas (ejemplos):**
- Debe monetizar desde el día 1
- El usuario objetivo tiene más de 60 años
- El modelo de negocio no puede ser publicidad
- Debe funcionar sin internet del usuario
- Costo de operación mensual < $5 USD

**Reglas de restricciones:**
- ✅ Deben ser realistas y dolorosas
- ✅ Deben simular una condición real del mercado o la infra
- ❌ No pueden hacer la idea técnicamente imposible
- ❌ No pueden contradirse entre sí de forma absurda

Los organizadores tienen veto si una restricción es inútil o imposible.

---

### Fase 3 — Build Phase (2 horas)

Los equipos construyen su idea terrible con todas las restricciones encima.

**AI está explícitamente permitida:**
- Generación de código: ✅
- Generación de UI: ✅
- Boilerplate: ✅
- Que ChatGPT haga todo y no entiendas nada: ❌ (el jurado pregunta en el pitch)

**Deploy obligatorio:**
- El producto debe estar en una URL pública al momento del pitch
- Railway (BE) / Vercel (FE) — plantillas disponibles
- Si no hay link: puntaje técnico = 0

---

### Fase 4 — Demo + Final Pitch (1 hora)

Cada equipo tiene **12 min:**

| Tiempo | Qué pasa |
|---|---|
| 3 min | El speaker abre el link en pantalla — el jurado lo prueba en vivo |
| 4 min | Pitch: cómo evolucionó la idea, cómo manejaron las restricciones |
| 3 min | Preguntas del jurado (incluyendo preguntas técnicas al equipo) |
| 2 min | Deliberación express entre pitches |

**El pitch debe responder:**
1. ¿Qué era la idea original?
2. ¿Qué restricciones recibieron y cuáles fueron las más brutales?
3. ¿Qué decisiones técnicas tomaron por culpa de las restricciones?
4. ¿Esto podría ser un negocio real? ¿Por qué sí o por qué no?

---

## Puntuación

| Criterio | Peso | Descripción |
|---|---|---|
| Producto funcionando en URL pública | 25% | ¿Existe? ¿Corre? |
| Manejo de restricciones | 25% | Soluciones creativas > hacks chapuceros |
| Pitch y narrativa | 25% | ¿Convence? ¿Es honesto sobre los trade-offs? |
| Fun factor / absurdidad bien ejecutada | 15% | El jurado lo decide subjetivamente |
| Calidad técnica percibida | 10% | El jurado pregunta, el equipo responde |

---

## Roles naturales para equipos de 3 personas

| Perfil | Qué hace |
|---|---|
| **Técnico 1** | Arquitectura, backend, deploy |
| **Técnico 2** | Frontend, UI, integración IA |
| **Comunicación / ventas** | Lidera el pitch, define la narrativa, elige qué restricciones atacar con más drama |

El perfil de ventas tiene un rol clave desde la Fase 1: vender la idea con la mayor confianza posible aunque sea terrible.

---

## Preparación requerida (organizadores)

- [ ] Lista de 10–15 ideas "semilla" para equipos que se bloqueen con la Fase 1
- [ ] Lista de restricciones técnicas y de negocio válidas (referencia para el jurado)
- [ ] Plantillas de repo para deploy rápido (Railway + Vercel)
- [ ] Guía de IA permitida: qué herramientas, qué límites
- [ ] Jurado briefeado: deben hacer al menos 1 pregunta técnica por equipo

---

## Por qué funciona para el 30° aniversario UPTC

- Celebra que en ingeniería, las restricciones son lo que define la solución
- El pitch absurdo rompe el hielo y nivela el campo — no gana solo el que codea más rápido
- AI como herramienta legítima refleja el estado actual de la industria
- 3 personas es el tamaño perfecto: uno piensa, uno construye, uno vende
- Memorable: los asistentes van a recordar "la app de domicilios para pisos impares" por años

---

## Variante: "El Giro Final"

A los 30 min del build phase, los organizadores revelan un **twist obligatorio** para todos:

- "Ahora todos deben agregar un componente de IA generativa"
- "El producto debe funcionar sin JavaScript"
- "Deben cobrar en créditos universitarios ficticios"

Obliga a pivotear a mitad del camino — simula el caos real de un producto.
