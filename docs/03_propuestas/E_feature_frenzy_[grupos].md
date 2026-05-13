# Propuesta E — Feature Frenzy: El Brief que Muta

## Concepto

> Al inicio recibes un brief de producto simple. Cada hora, los organizadores añaden un nuevo requisito — a veces técnico, a veces de negocio, a veces absurdo. Tienes que adaptarte sin tirar lo que ya construiste. Al final, el pitch es la historia de cómo sobreviviste a los cambios.

---

## Tagline sugerido

**"Los requisitos siempre cambian. Los buenos ingenieros también."**

---

## Por qué es diferente

No se trata de construir rápido — se trata de construir **de forma que aguante el cambio**. El producto del primer requisito raramente sobrevive intacto al cuarto. Los equipos que ganan son los que tomaron decisiones de arquitectura que les dieron flexibilidad. El pitch no es "mira lo que hice" — es "mira cómo lo hice sobrevivir a 4 requisitos".

---

## Mecánica del evento

### Fase 0 — Brief inicial (15:00–15:15)

Se revela el **Requisito 0**: un brief de producto simple y razonable.

**Ejemplo de Requisito 0:**
> *"Construyan una herramienta para que los estudiantes de la UPTC registren y compartan sus horarios de clase con sus compañeros."*

Los equipos tienen total libertad de stack y arquitectura. IA permitida.

**Regla de oro desde el inicio:**
> Lo que construyas en la próxima hora tiene que ser extendible. No hagas algo que no puedas cambiar.

---

### Fases de desarrollo + requisitos (15:15–19:30)

Cada **hora exacta**, los organizadores revelan un nuevo requisito en pantalla. Todos los equipos lo ven al mismo tiempo. El requisito es acumulativo — no reemplaza al anterior, lo extiende.

#### Requisito 1 — 15:15 (primer bloque de 1h)
Funcionalidad base.

*Ejemplo:* "El sistema debe permitir a un estudiante crear un horario y compartir el link con otro."

#### Requisito 2 — 16:15 (segunda hora)
Restricción técnica inesperada.

*Ejemplo:* "Los horarios deben seguir funcionando sin conexión a internet."  
*O:* "El backend no puede usar base de datos relacional."  
*O:* "Debe correr en un dispositivo con menos de 512MB de RAM."

#### Requisito 3 — 17:15 (tercera hora)
Cambio de audiencia o modelo de negocio.

*Ejemplo:* "Ahora el sistema también lo usan los profesores para revisar disponibilidad de sus estudiantes."  
*O:* "El producto debe ser monetizable. Los usuarios premium pueden hacer X."  
*O:* "El cliente principal ya no son estudiantes — son los padres de familia."

#### Requisito 4 — 18:15 (cuarta hora)
El twist absurdo-pero-realista.

*Ejemplo:* "Agrega una funcionalidad con IA generativa que sea útil de verdad — no un gimmick."  
*O:* "El sistema debe integrarse con el sistema académico de la UPTC (solo hay un endpoint público documentado)."  
*O:* "El producto debe funcionar por WhatsApp además de por web."

---

### Congelamiento y pitches (19:30–20:40)

Cada equipo tiene **10 min:**

| Tiempo | Contenido |
|---|---|
| 2 min | Demo del producto final funcionando en URL pública |
| 4 min | Pitch narrativo: "el brief original era X, luego llegó Y, luego Z, así sobrevivimos" |
| 2 min | "¿Qué decisión técnica del inicio les salvó? ¿Qué decisión los hizo sufrir?" |
| 2 min | Preguntas del jurado |

---

## Puntuación

| Criterio | Peso | Descripción |
|---|---|---|
| Requisitos implementados | 30% | ¿Cuántos de los 4 requisitos están funcionando? (7.5% c/u) |
| Producto en URL pública | 20% | ¿Está desplegado y corre? Si no → penalización severa |
| Calidad del pitch narrativo | 25% | ¿La historia del proceso es convincente y honesta? |
| Decisiones arquitectónicas | 15% | ¿La estructura del código permitió adaptarse? (jurado pregunta) |
| Fun factor — ¿el Requisito 4 sorprendió? | 10% | Puntaje subjetivo del jurado |

---

## Roles naturales para equipos de 3 personas

| Perfil | Qué hace |
|---|---|
| **Técnico 1** | Arquitectura base, decisiones que impactan la adaptabilidad futura |
| **Técnico 2** | Implementación de features, integración de cada nuevo requisito |
| **Comunicación** | Lee los requisitos primero, analiza el impacto, coordina la respuesta del equipo, construye la narrativa para el pitch |

El perfil de comunicación tiene un rol de **product manager en tiempo real**: cuando llega un nuevo requisito, es quien primero lo analiza y discute con el equipo qué implica, qué hay que tirar, qué hay que adaptar.

---

## Los requisitos secretos

Los organizadores preparan los requisitos **antes del evento** pero no los revelan. Deben diseñarlos para que sean:

1. Coherentes — el sistema sigue siendo uno solo
2. Dolorosos pero no imposibles — en 1h se puede implementar algo
3. Progresivos — el Requisito 4 es el más difícil/absurdo
4. Independientes del stack — cualquier equipo puede responder sin importar su tecnología

**Banco de requisitos de ejemplo (organizadores preparan 2–3 opciones por slot y eligen en el día):**

| Slot | Opción A | Opción B | Opción C |
|---|---|---|---|
| R2 | Sin base de datos relacional | Debe funcionar offline | Latencia < 100ms |
| R3 | Añadir monetización | Cambiar audiencia objetivo | Modo multilenguaje (ES/EN) |
| R4 | Integrar IA generativa real | Añadir canal WhatsApp | API pública documentada |

---

## Infraestructura necesaria (organizadores)

- Brief inicial redactado (1 párrafo, no más)
- 4 requisitos preparados y guardados en secreto
- Pantalla para revelar cada requisito a la hora exacta (puede ser un slide)
- Guía de deploy (Railway / Vercel) para que los equipos puedan hacer CD desde el inicio

---

## Por qué funciona para el 30° aniversario UPTC

- Simula la realidad de producto mejor que cualquier hackathon clásico — los requisitos siempre cambian
- La IA tiene un rol natural en el Requisito 4 si así se diseña
- El pitch es narrativo y emocional — la historia del proceso importa tanto como el resultado
- No favorece solo al equipo más rápido — favorece al que mejor pensó la arquitectura inicial
- Funciona con cualquier stack, cualquier perfil, cualquier nivel de experiencia

---

## Variante: "Requisito en sobre cerrado"

En lugar de revelar los requisitos en pantalla, cada equipo recibe el mismo sobre cerrado. Lo abren a la hora exacta. Crea el ritual de "todos abren al mismo tiempo" — genera un momento dramático cada hora.
