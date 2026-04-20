# Propuesta D — City OS: The Swarm (Colaborativo)

## Concepto

> Los organizadores proveen y proyectan en pantalla gigante una simulación en tiempo real (UI) del mapa de la ciudad de Tunja. La ciudad está viva pero al borde del colapso. Los equipos no construyen aplicaciones web tradicionales; escriben **motores algorítmicos (Agentes/Bots)** que se conectan por WebSockets a la simulación central. Cada equipo asume el control exclusivo de un subsistema crítico de la ciudad y deben colaborar (y no estorbarse) para mantener la ciudad funcionando.

---

## Tagline sugerido

**"La ciudad no duerme. Tus algoritmos tampoco."**

---

## Los 4 Subsistemas (Asignados a los equipos)

Cada equipo recibe credenciales para operar uno de estos servicios. Si hay 8 equipos, habrá 2 "empresas" compitiendo por cada sector, corriendo en la misma ciudad.

1. **Traffic Control (Semáforos y Vías):** Controlan los tiempos de los semáforos en las intersecciones clave. Su objetivo es mantener el flujo (throughput) global de la ciudad alto y evitar embotellamientos.
2. **Ride-Hailing (Taxis / Uber):** Reciben peticiones de pasajeros generadas aleatoriamente. Su algoritmo debe despachar el carro más cercano, calcular la ruta óptima y cobrar. Su objetivo es maximizar la ganancia y minimizar el tiempo de espera del usuario.
3. **Logistics (Rappi / Entregas):** Reciben pedidos de comida de restaurantes a casas. Sus motos ignoran un poco el tráfico, pero tienen un SLA (Service Level Agreement) estricto: si la pizza llega fría (tarde), pierden puntos.
4. **Mass Transit (Transporte Público):** Manejan buses de alta capacidad. Deben diseñar y operar rutas dinámicas basadas en los mapas de calor de la demanda ciudadana. Son lentos, generan tráfico, pero mueven a muchas personas a la vez.

---

## Mecánica del evento (5 horas)

### Fase 1 — Conexión y Exploración del Grafo (1 hora)

**14:00–15:00**
Los organizadores encienden el "City OS". La pantalla muestra el grafo de la ciudad vacío.
Los equipos reciben la documentación de los WebSockets y la topología del grafo (Nodos y Aristas con pesos/distancias).
- **El reto aquí:** Lograr conectarse al servidor, parsear el JSON masivo del mapa y lograr que al menos 1 vehículo se mueva de un Nodo A a un Nodo B usando un algoritmo básico de Pathfinding (ej. Dijkstra o A*).

### Fase 2 — La Simulación Inicia (2 horas)

**15:00–17:00**
La ciudad empieza a generar demanda (usuarios pidiendo viajes, comida, tráfico civil).
Los algoritmos de los equipos empiezan a tomar decisiones en tiempo real.
- **La complejidad "Tick-Rate":** El servidor avanza la simulación cada 200ms. Los equipos reciben el estado actual y tienen solo ~100ms para enviar las nuevas instrucciones de sus flotas. Algoritmos ineficientes causarán que sus vehículos se queden paralizados.
- **El Efecto Mariposa:** Si Uber manda muchos carros por la misma avenida, saturan la arista (calle). La velocidad baja a casi cero. El equipo de *Traffic Control* debe detectarlo y darle luz verde prolongada a esa avenida, o el equipo de *Rappi* perderá sus tiempos de entrega.

### Fase 3 — El Caos (1.5 horas)

**17:00–18:30**
Los organizadores activan el **"Chaos Engine"** desde su panel de control. Envían eventos globales que obligan a los algoritmos a recalcular dinámicamente:
- ⛈️ **Clima extremo:** Lluvia torrencial. Las velocidades máximas de todas las calles se reducen un 40%.
- 🚧 **Accidente:** Un nodo crítico (ej. la Glorieta Norte) se bloquea. Los algoritmos de enrutamiento tienen que descubrir la calle cerrada y recalcular cientos de rutas simultáneamente.
- 🎓 **Salida de la UPTC:** Un pico masivo de cientos de peticiones de transporte concentradas en un solo nodo.

### Fase 4 — Code Freeze y Pitches (30 min)

**18:30–19:00**
Se congela el código, pero la simulación sigue corriendo en pantalla durante los pitches.
Cada equipo tiene **5 minutos** para explicar:
1. Qué estructura de datos o algoritmo usaron (ej. "Usamos A* con heurística de tráfico en tiempo real").
2. Cómo manejaron la concurrencia y la restricción de tiempo del servidor.
3. Qué evento de caos destruyó su algoritmo y cómo intentaron arreglarlo.

---

## El Mercado de Datos (Colaboración Forzada y Asimetría)

La verdadera genialidad técnica de este hackathon radica en la **Asimetría de Información**. El servidor central (City OS) NO entrega la misma información a todos los equipos, obligándolos a construir un ecosistema de microservicios en vivo para sobrevivir:

1. **La Ceguera del Transporte:** Los equipos de *Ride-Hailing (Uber)*, *Logistics (Rappi)* y *Mass Transit (Buses)* reciben las coordenadas de sus clientes y la topología base del mapa (las calles y distancias). Sin embargo, el servidor central les miente por omisión: les dice que todas las calles están siempre vacías.
2. **El Monopolio de los Datos:** El único equipo que recibe la telemetría en tiempo real de cuántos vehículos hay en cada calle y dónde están los embotellamientos es el equipo de **Traffic Control (Semáforos)**.
3. **El Mercado de APIs:** Si Uber o Rappi intentan calcular sus rutas óptimas (usando algoritmos como A* o Dijkstra) asumiendo que las calles están vacías, enviarán toda su flota directamente a los peores trancones de la ciudad, arruinando sus tiempos de entrega y perdiendo el juego. 
4. **Negociación en Vivo:** Para evitar el colapso, los equipos de transporte tienen que levantarse de sus mesas y negociar con *Traffic Control*. *Traffic Control* debe programar y exponer rápidamente una API REST o WebSocket secundaria. Los otros equipos deben consumir esta API en tiempo real para inyectar los "pesos de congestión" reales en sus propios grafos de memoria antes de calcular las rutas.
5. **Trueques y Contratos:** Los equipos pueden hacer acuerdos estratégicos (ej. *Traffic Control* dice: "Te doy acceso a mi API de tráfico con latencia de 50ms, pero a cambio, el algoritmo de tus buses debe priorizar las avenidas principales para ayudarme a mejorar mi métrica de descongestión").

Esta dinámica transforma una competencia de programación individual en una red de **Sistemas Distribuidos Interdependientes**. Si el equipo de *Traffic Control* despliega una API ineficiente, o si cambia el formato JSON sin avisar, tumba los algoritmos de todas las demás empresas, colapsando la simulación.

---

## Puntuación

El puntaje es una mezcla entre el éxito individual de la "empresa" y la salud de la ciudad.

| Criterio | Peso | Descripción |
|---|---|---|
| **Rendimiento Individual (Métricas)** | 40% | Dinero ganado (Uber/Rappi), SLA de entregas, o pasajeros movidos (Buses). El propio sistema lo calcula automáticamente. |
| **Salud de la Ciudad (Puntaje Global)** | 30% | Si la ciudad entra en un *"Gridlock"* (trancón total donde nadie se mueve), todos pierden estos puntos. Obliga a los equipos a no ser egoístas. |
| **Ingeniería Algorítmica y Pitch** | 30% | El jurado evalúa la elegancia del código, la eficiencia del Pathfinding y el manejo de los WebSockets. |

---

## Infraestructura necesaria (Organizadores)

Este formato es espectacular pero requiere un desarrollo previo robusto por parte de la organización:
- [ ] **El Motor (Game Server):** Un backend (ej. Node.js, Go o Elixir) que mantenga el estado de la ciudad, aplique las reglas físicas (capacidad de calles) y despache los WebSockets a alto rendimiento.
- [ ] **La UI del Mapa:** Un frontend visual (ej. usando Canvas, WebGL, o Three.js) que consuma el estado del servidor y dibuje la ciudad, los carritos moviéndose y los semáforos en tiempo real. Proyectado en pantalla grande.
- [ ] **SDKs / Clientes Base:** Proveer plantillas de código en Python y Node.js que ya incluyan la conexión básica por WebSocket para que los participantes no pierdan la primera hora peleando con la red y se enfoquen en la lógica.

---

## Por qué funciona para el 30° aniversario UPTC

- Es un espectáculo visual absoluto. Las autoridades, jurados y espectadores no están viendo "código aburrido", están viendo un videojuego programado en vivo.
- Pone a prueba la **verdadera ciencia de la computación**: estructuras de datos complejas, optimización algorítmica y procesamiento asíncrono, alejándose de los típicos CRUDs de aplicaciones web.
- Demuestra que la ingeniería colaborativa a nivel de sistemas distribuidos es clave para las ciudades inteligentes del futuro (Smart Cities).