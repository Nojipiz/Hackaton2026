# Tipos de Hackathon — Análisis para el 30° Aniversario UPTC

## Contexto de evaluación

- **Duración disponible:** Exactamente 5 horas (ej. 14:00–19:00, con pitches hasta las 20:00)
- **Participantes:** 15–20 personas, 3–5 equipos (Equipos de 3-4 personas máximo)
- **Perfil:** Mixto (Ingenieros Backend/Frontend + Perfiles de Producto/Ventas/Comunicación)
- **Objetivo diferencial:** Romper el molde del "hackathon aburrido de hacer un CRUD". Mostrar la evolución de la ingeniería de software (Sistemas Distribuidos, IA, Trabajo Colaborativo en Red).

---

## Formatos Evaluados y Evolucionados

En base a los formatos tradicionales, hemos diseñado dos grandes macrotendencias para este evento de 5 horas: **Hackathones Grupales (Competitivos)** y **Hackathones Colaborativos (Sistemas Interdependientes)**.

### Macrotendencia 1: Hackathones Grupales (Competitivos)
*Cada equipo construye su propio producto aislado y compite contra los demás para ver quién tiene la mejor solución, el mejor pitch o la mejor arquitectura.*

#### 1. Startup Arena / Shark Tank (Propuesta B)
- **Mecánica:** Los equipos reciben 5 problemas reales de la región (Boyacá/Tunja). Tienen 5 horas para construir un MVP funcional y presentarlo ante un jurado de "inversionistas" que tienen un presupuesto ficticio (ej. $1,000,000,000 COP) para repartir.
- **Por qué funciona:** Es el formato perfecto para integrar perfiles técnicos (que programan a toda velocidad) y perfiles de producto/ventas (que preparan el modelo de negocio, el ROI y el pitch deck).
- **Espectáculo:** La competencia final por el "dinero" de los inversionistas genera muchísima tensión.

#### 2. Constraint Attack / Brutal Reality (Propuesta C)
- **Mecánica:** Los equipos proponen ideas de startup intencionalmente malas o absurdas (ej. "Tinder para buscar grupo de tesis en la UPTC"). Los *otros equipos* les imponen restricciones técnicas y de negocio brutales (ej. "No puedes usar bases de datos relacionales" o "Debes monetizar el día 1"). Tienen que construirlo de todas formas.
- **Por qué funciona:** Nivela el campo de juego. No gana el que programa más rápido, sino el más creativo y resiliente para sortear restricciones absurdas. 
- **Espectáculo:** Las presentaciones finales son hilarantes pero técnicamente impresionantes.

#### 3. Feature Frenzy (Propuesta E)
- **Mecánica:** Se da un brief inicial súper simple. Pero *cada hora exacta*, los organizadores revelan un nuevo requerimiento obligatorio en pantalla (a veces técnico, a veces un cambio de negocio, a veces un twist absurdo).
- **Por qué funciona:** Simula la vida real del ingeniero de software: los requerimientos del cliente siempre cambian. Gana el equipo que diseñó la arquitectura más flexible y no el que "hardcodeó" todo en la primera hora.
- **Espectáculo:** La alarma sonando cada hora revelando un requerimiento que destruye el código de los equipos genera pura adrenalina.

---

### Macrotendencia 2: Hackathones Colaborativos (Ecosistemas Vivos)
*Nadie gana solo. Todos los equipos (la sala entera) deben construir piezas de software que se conectan entre sí para formar un único mega-sistema. Si un equipo falla, el sistema entero sufre.*

#### 4. Startup Ecosystem Builder (Propuesta A)
- **Mecánica:** Se plantea un macro-problema de ciudad (ej. Plataforma Inteligente de Transporte para Tunja). Toda la sala hace una sesión de System Design. Luego, cada equipo construye solo un microservicio (Ej. Equipo 1 hace la API de Pagos, Equipo 2 la API de Rutas). 
- **La magia:** Los servicios de los equipos tienen que comunicarse entre sí por Internet (APIs) en tiempo real durante el evento.
- **Por qué funciona:** Enseña arquitectura de microservicios y contratos de API. Si el equipo de Pagos cambia su respuesta JSON sin avisar, tumba la aplicación del equipo de Rutas. 
- **Espectáculo:** Hay un dashboard global proyectado viendo qué servicios están "Up" (verdes) y cuáles están caídos o fallando en sus integraciones.

#### 5. City OS: The Swarm / Simulación Multi-Agente (Propuesta D)
- **Mecánica:** Los organizadores proyectan el mapa en vivo de Tunja. Los equipos no hacen interfaces web; escriben algoritmos (bots) en Python/Node que se conectan por WebSockets al mapa. Un equipo controla los semáforos, otro una flota de Uber, otro los camiones de Rappi. 
- **La magia:** Asimetría de información. El equipo de Uber no sabe dónde hay trancones, *solo* el equipo de Semáforos lo sabe. Uber tiene que negociar físicamente en la sala con el equipo de Semáforos para que les expongan una API con los datos de tráfico en vivo, o sus algoritmos de rutas colapsarán.
- **Por qué funciona:** Es ingeniería de software *hardcore*: WebSockets, algoritmos de grafos (A*), concurrencia extrema y sistemas distribuidos.
- **Espectáculo:** Literalmente parece un videojuego en pantalla gigante donde los autos se mueven basados en el código que los estudiantes están escribiendo en tiempo real, sufriendo eventos de caos (ej. "Accidente en la glorieta").

---

## Conclusión del Análisis para las 5 horas

Para el contexto del **30° aniversario de la Escuela de Ingeniería de Sistemas y Computación (UPTC)**, el evento debe ser memorable. 

Cualquiera de las **5 Propuestas Finales (`03_propuestas/`)** logra este objetivo, pero requieren distintos niveles de preparación:

- **Menos esfuerzo técnico para organizadores:** Propuestas **B** (Shark Tank) y **C** (Terrible Ideas). Solo requieren buenos jurados y creatividad.
- **Esfuerzo medio (Infraestructura):** Propuesta **E** (Feature Frenzy). Requiere muy buena planeación de los requerimientos sorpresa.
- **Alto esfuerzo técnico (Para lucirse):** Propuestas **A** (Ecosistema) y **D** (City OS). Requieren que los organizadores construyan bots de tráfico, servidores de WebSockets o interfaces gráficas de simulación *antes* del evento, pero garantizan un espectáculo de ingeniería sin precedentes en la región.
