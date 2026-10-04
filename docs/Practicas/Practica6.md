# Ficha de Estación - Mecanismos (Introducción a la Mecatrónica)

| Estación | ¿Qué transforma? (vel/par, rot/trasl, cont/inter, cambio de eje) | Relación estimada (cuenta dientes o vueltas) | ¿Reversible o autobloqueante? | ¿Dónde lo has visto en la vida real? | ¿Dónde serviría en el carro o en un proyecto tuyo? |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **A · Diferencial (Crown gear)** | Cambio de eje a 90° / Transforma par y velocidad angular entre ejes perpendiculares. | **1:3** (aprox. 12 dientes en el piñón de entrada vs. 36 dientes en la corona). | Reversible | En el eje de transmisión trasero de camionetas y automóviles de tracción trasera. | En el diferencial motriz para transmitir la fuerza del motor a las ruedas traseras permitiendo diferentes velocidades en curvas. |
| **B · Cicloidal (Cycloidal drive)** | Vel/Par (Reduce alta velocidad a baja velocidad incrementando sustancialmente el par). | **1:10** a **1:11** (basado en el número de pines concéntricos exteriores). | Autobloqueante (por la geometría excéntrica y la alta fricción del contacto). | En articulaciones de brazos robóticos industriales de alta precisión y reductores armónicos. | En la articulación o codo de un brazo robótico articulado para sostener cargas pesadas sin perder posición. |
| **C · Cardán (Universal joint)** | Cambio de eje angular (transmite rotación continua entre ejes desalineados angularmente). | **1:1** (la velocidad angular promedio de entrada es igual a la de salida). | Reversible | En el árbol de transmisión de camionetas 4x4 y en llaves de vaso (dados articulados). | Para acoplar la columna de dirección con la caja de dirección cuando no están alineadas en línea recta. |
| **D · Obturador (Shutter)** | Rot/Trasl (Convierte rotación de la palanca exterior en desplazamiento radial de las hojas). | **N/A** (Mecanismo de diafragma de apertura/cierre de área). | Reversible | En el objetivo/lente de cámaras fotográficas profesionales y proyectores de luz. | En una válvula de admisión de aire variable o en un diafragma regulador de flujo para un proyecto de fluidos. |
| **E1 · Opción 1: Cremallera y Piñón (Rack & Pinion)** | Rot/Trasl (Convierte movimiento de rotación del piñón en movimiento lineal rectilíneo). | **1:1** (Desplazamiento lineal proporcional al paso del piñón por vuelta). | Reversible | En el sistema de dirección de la mayoría de los autos ligeros y portones eléctricos. | En el sistema de dirección del auto de carreras/baja para convertir el giro del volante en desplazamiento de las llantas. |
| **E1 · Opción 2: Cruz de Ginebra (Geneva Drive)** | Cont/Inter (Convierte rotación continua en rotación intermitente/por pasos). | **1:6** (La rueda conducida avanza 1/6 de vuelta (60°) por cada vuelta completa del impulsor). | Autobloqueante (durante la fase de reposo gracias al contorno de bloqueo). | En los mecanismos de avance de película en proyectores de cine antiguos y plataformas giratorias industriales. | En un dispensador o carrusel de herramientas automatizado que requiera posicionarse en estaciones fijas. |
| **E2 · Opción 1: Sin Fín y Corona (Worm Wheel)** | Vel/Par + Cambio de eje a 90° (Reduce drásticamente velocidad e incrementa torque). | **1:20** (1 entrada helicoidal por 20 dientes en la rueda conducida). | Autobloqueante (el piñón sin fín puede mover la rueda, pero la rueda no puede mover al sin fín). | En el mecanismo de elevación de grúas, elevadores y clavijas de afinación de guitarras. | En el sistema del elevador de vidrios eléctrico del auto para evitar que la ventana se caiga por peso propio. |
| **E2 · Opción 2: Engranaje Intermitente (Intermittent Gear)** | Cont/Inter (Convierte rotación continua en rotación pausada o intermitente). | **1:4** (Avance de un cuarto de vuelta intermitente por cada revolución completa). | Reversible (mientras los dientes estén engranados). | En contadores mecánicos, relojes analógicos y bandas de ensamblaje automatizadas. | En un sistema de dosificación paso a paso para alimentar piezas en una línea de producción mecatrónica. |

---

## Registro y Descripción de Videos de los Mecanismos

### 1. Mecanismo Cicloidal 
![video](../Imagenesana/cicloidal.mp4){loading=lazy}
* **Descripción de lo que se ve:** Se observa una vista superior de un reductor cicloidal impreso en 3D. Un disco azul con perfil lobular oscila excéntricamente impulsado por un eje central, haciendo contacto continuo con un rodamiento de pines dentro de un marco negro.

### 2. Cremallera y Piñón
![video](../Imagenesana/transformador.mp4){loading=lazy}
* **Descripción de lo que se ve:** Un piñón azul gira manualmente sobre una base fija y sus dientes enganchan una barra rectilínea dentada (cremallera), desplazándola de manera lineal de izquierda a derecha.

### 3. Engranaje Planetario
![video](../Imagenesana/reductor.mp4){loading=lazy}
* **Descripción de lo que se ve:** Tres engranajes planetarios azules situados a 120° orbitan alrededor de un eje central e interactúan simultáneamente con los dientes internos de un anillo de soporte exterior.

### 4. Cruz de Ginebra / Mecanismo de Ginebra 
![video](../Imagenesana/cruztransformadora.mp4){loading=lazy}
* **Descripción de lo que se ve:** Un manubrio circular azul con una clavija engrana en las ranuras de un disco en forma de estrella de 6 puntas, generando un movimiento de rotación pausado con paradas entre cada avance.

### 5. Tornillo Sin Fín y Corona 
![video](../Imagenesana/reductorchurro.mp4){loading=lazy}
* **Descripción de lo que se ve:** Un tornillo helicoidal (sin fín) azul dispuesto horizontalmente engrana con una rueda dentada plana posicionada a 90°. Al girar manualmente el tornillo, la rueda avanza muy lentamente.

### 6. Engranaje Cónico / Corona 
![video](../Imagenesana/reductor3ruedas.mp4){loading=lazy}
* **Descripción de lo que se ve:** Se aprecia un plato/corona central grande accionado en sus extremos opuestos por dos piñones cónicos acoplados a 90°, demostrando la transmisión de fuerza entre ejes perpendiculares.

### 7. Obturador de Iris 
![video](../Imagenesana/obturador.mp4){loading=lazy}
* **Descripción de lo que se ve:** Una serie de 6 aletas o paletas superpuestas se mueven concéntricamente mediante una pequeña palanca exterior para abrir y cerrar el diámetro central.

### 8. Junta Cardán / Unión Universal 
![video](../Imagenesana/unionuniversal.mp4){loading=lazy}
* **Descripción de lo que se ve:** Dos ejes azules conectados en el centro mediante un conector articulado en forma de cruz (cruceta) que permite rotar ambos ejes incluso cuando se dobla el ángulo entre ellos.

### 9. Engranaje Intermitente 
![video](../Imagenesana/transformarueda.mp4){loading=lazy}
* **Descripción de lo que se ve:** Un disco impulsor grande provisto con sólo un sector parcial dentado hace girar a un piñón más pequeño únicamente durante una fracción de su vuelta, manteniéndolo estático el resto del tiempo.