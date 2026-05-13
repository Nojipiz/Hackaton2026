# Requisitos y Logística — Hackathon 30° Aniversario UPTC

## Datos base

| Parámetro | Valor |
|---|---|
| **Evento** | Hackathon 30° Aniversario — Ingeniería en Sistemas y Computación |
| **Institución** | UPTC, Tunja, Colombia |
| **Participantes** | 15–20 personas |
| **Equipos** | 3–5 equipos de **exactamente 3 personas** |
| **Fecha** | Por definir (semestre 2026) |
| **Duración** | **4 horas** (ej. 14:00–18:00) |
| **IA** | Permitida explícitamente (Cursor, Copilot, ChatGPT, Claude, etc.) |

---

## Composición de equipos

**3 personas por equipo — fijo.** Composición sugerida pero no obligatoria:

| Rol | Responsabilidad principal |
|---|---|
| Técnico 1 | Backend, arquitectura, deploy |
| Técnico 2 | Frontend, integración, IA |
| Comunicación | Pitch, narrativa, documentación |

Equipos homogéneos (3 técnicos o 3 comunicadores) también participan — la evaluación reconoce el perfil del equipo.

## Uso de IA

**Explícitamente permitida.** Herramientas válidas:
- Cursor, GitHub Copilot, ChatGPT, Claude, v0, Bolt, etc.

**Regla:** el jurado puede hacer preguntas técnicas durante el pitch. Si nadie del equipo puede explicar el código que shippearon, el puntaje técnico baja. IA como acelerador, no como reemplazo del entendimiento.

---

## Timeline propuesto

```
13:30 – 14:00   Llegada, registro, café — sin actividad formal
14:00 – 14:30   Bienvenida, presentación del reto, formación de equipos
14:30 – 15:00   Setup (repos, cuentas cloud, plantillas, primer deploy vacío)
15:00 – 19:30   Bloque de desarrollo (4h 30min) ← mínimo garantizado
19:30 – 19:40   Congelamiento — sin más commits, preparar pitch
19:40 – 20:40   Pitches en vivo (8–10 min por equipo: demo + pitch + preguntas)
20:40 – 21:00   Deliberación + premiación y cierre — celebración 30 años
```

**Total evento:** ~7.5h | **Desarrollo garantizado:** 4h 30min

---

## Infraestructura técnica

### Para los equipos

| Herramienta | Uso | Por qué |
|---|---|---|
| **Railway** | Deploy BE / full-stack | Deploy desde GitHub en <5min, plan free, sin tarjeta |
| **Vercel** | Deploy FE estático / Next.js | El más rápido para frontend, integración directa con GitHub |
| **Render** | Alternativa a Railway | Más permisivo con stacks menos comunes |
| **GitHub** | Control de versiones + trigger de deploy | Gratis, familiar, necesario para el deploy automático |

### Plantillas preparadas por organizadores

Los organizadores deben tener listas antes del evento:

- [ ] Plantilla BE: Node.js + Express lista para Railway (`railway.json` incluido)
- [ ] Plantilla BE: Python + FastAPI lista para Railway
- [ ] Plantilla FE: React/Vite lista para Vercel (`vercel.json` incluido)
- [ ] Guía de 1 página: "De cero a URL pública en 10 minutos"
- [ ] Canal de Slack / WhatsApp para soporte técnico durante el evento

### Para los organizadores

- Red WiFi estable con capacidad para 20+ dispositivos simultáneos
- Pantalla o proyector para el leaderboard / marcador en tiempo real
- Laptop de backup para el árbitro técnico (según la propuesta elegida)
- Servidor/servicio para el árbitro (Railway gratuito es suficiente)

---

## Jurado

**Composición recomendada:** 2–3 personas

| Perfil | Rol en la evaluación |
|---|---|
| Docente técnico de Ingeniería | Evalúa solidez técnica y arquitectura |
| Profesional de industria (egresado) | Evalúa viabilidad y calidad del producto |
| Perfil de negocio / emprendimiento | Evalúa el pitch y la propuesta de valor |

---

## Criterios de evaluación (pesos sugeridos)

| Criterio | Peso | Descripción |
|---|---|---|
| **Funcionalidad técnica** | 35% | ¿Funciona? ¿Está desplegado? ¿Responde correctamente? |
| **Creatividad / originalidad** | 25% | ¿La solución es interesante? ¿Resuelve algo real? |
| **Pitch y presentación** | 25% | ¿Convence? ¿Es claro? ¿Tiene propuesta de valor? |
| **Trabajo en equipo visible** | 15% | ¿Todos participaron? ¿La demo es coherente con el pitch? |

---

## Premios

A definir por los organizadores. Sugerencias:

- 🥇 Premio principal: certificado + kit de merch UPTC + dinero simbólico o vale
- 🥈 Premio técnico: al equipo con la implementación más robusta
- 🎤 Premio al mejor pitch: al equipo con la presentación más convincente
- 🎲 Premio sorpresa: criterio revelado en el momento (ej. "el equipo más caótico")

---

## Riesgos y plan B

| Riesgo | Plan B |
|---|---|
| WiFi inestable | Hotspot de organizadores como respaldo, demo offline permitida |
| Equipo no logra deploy | Demo local permitida pero con penalización en puntuación |
| Jurado no llega | Un organizador asume el rol, se ajustan los pesos |
| Equipo se queda sin ideas | Organizadores tienen 3 prompts de "rescate" preparados |
