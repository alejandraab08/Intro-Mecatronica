# Reporte: Modelado y Ensamble Digital de un Cubo 

**Institución:** Universidad Iberoamericana Puebla  
**Materia:** Proyecto de Ingeniería I 

---

## 1. Introducción al Modelado por Ensambles

El ensamblaje por piezas consiste en diseñar componentes individuales que posteriormente se unen mediante relaciones de posición. Este enfoque replica el proceso real de manufactura y montaje (como el de corte láser), permitiendo analizar el ajuste y la interacción entre piezas antes de la fabricación de las piezasñ.

---

## 2. Trazo de Caras Base

Para iniciar con el diseño de las caras individuales del cubo, primero se dibujó a mano (en papel) un cubo y se le puso pequeñas dentaduras simulando los "dientes" de las caras para el ensamblaje. Esto es útil porque al hacer un primer boceto a mano, es más sencillo darse cuenta cómo tienen que embonar las piezas antes de dibujarlo en CAD (SolidWorks).

---

## 3. Generación de Operaciones 3D en Componentes

Cada cara del cubo se dibujó con sus ranuras y se transformó a una pieza tridimensional para su ensamble de la siguiente manera:

1. **Extrusión de saliente:** Asignación del grosor uniforme del material (3mm) a cada una de las seis paredes del cubo.
2. **Cortes y preparaciones de borde:** Generación de ranuras  en las orillas para garantizar el ensamble de la caja.
3. **Guardado de componentes:** Almacenamiento individual de cada cara para su posterior importación al entorno de ensamble (también hecho en SolidWorks).

---

## 4. Proceso de Ensamble y Relaciones de Posición

Una vez creadas todas las partes, se procedió a la integración de las seis caras dentro de la parte de ensambles de SolidWorks:

- **Fijación de la cara base:** La primera cara que entra al plano la fijamos para que cuando agreguemos relaciones, nuestras demás piezas no se muevan.
- **Aplicación de relaciones de posición: (para este ejercicio solo son 2)**
  * *Coincidente:* La más importante en mi opinión. Alineación de caras y bordes para unir los extremos correspondientes.
  * *Perpendicular y Paralelo:* Ángulo de $90^\circ$ entre las paredes laterales para estructurar la forma del cubo.


---

## 5. Desarrollo de la Práctica

1. Se definieron las dimensiones del cubo y el diseño de ranuras en los bordes de cada cara.
2. Se modelaron y guardaron por separado las caras que componen la estructura.
3. Se importaron las piezas al entorno de ensamble y se aplicaron las relaciones de posición necesarias hasta cerrar la geometría del cubo sin interferencias.

---
## 6. Fotos
![Foto1](../imagenes/c(1).png){loading=lazy}
![Foto2](../imagenes/c(2).png){loading=lazy}
![Foto3](../imagenes/c(3).png){loading=lazy}

--- 

## 7. **Conclusión**

En esta práctica se consolidó el flujo de trabajo de ensamble de piezas en SolidWorks. A través de la creación individual de cada cara y el uso preciso de relaciones de posición, se comprendió cómo interactúan las piezas independientes dentro de un espacio tridimensional, asegurando un ajuste correcto, exacto y alineado a los requerimientos de un proceso de manufactura real.