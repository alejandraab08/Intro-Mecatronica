# Práctica: Oruga Print-in-Place

**Materia:** Proyecto de Ingeniería I   
**Institución:** Universidad Iberoamericana Puebla
---

## 1. Introducción al Diseño 3D y la Impresión

La impresión 3D te permite fabricar mecanismos articulados mediante la técnica **Print-in-Place** (impresión directa en una sola pieza). Esto significa que el objeto sale de la impresora completamente armado y listo para moverse, sin necesidad de pegar, atornillar o ensamblar partes por separado.

El secreto está en el diseño: se deben dejar pequeños espacios vacíos entre las piezas para que no se fundan ni se peguen entre sí mientras la máquina va depositando el plástico capa por capa.

---

## 2. Tipos de Uniones (Joints) en el Diseño 3D

Al modelar en 3D, las uniones definen cómo se va a mover una parte respecto a otra. A continuación se explican de forma sencilla los tipos de uniones más utilizados:

* **Unión Rígida (Rigid):** Une dos partes de forma fija y total. Ninguna de las piezas se puede mover ni girar.
* **Unión de Bisagra:** Permite que una pieza gire o rote en torno a un eje fijo, como una rueda, una puerta o una bisagra.
* **Unión Slider:** Permite que una pieza se mueva únicamente en línea recta hacia adelante y hacia atrás, como un cajón o un riel.
* **Unión Cilíndrica:** Permite dos movimientos a la vez sobre un mismo eje: girar sobre sí misma y deslizarse a lo largo.
* **Unión Esférica:** Permite que una pieza gire libremente hacia casi cualquier dirección dentro de una cuenca, similar a la articulación del hombro.
* **Unión Planar:** Permite que una pieza se deslice en dos direcciones sobre una superficie plana y además gire sobre ese mismo plano.

---

## 3. Diseño 3D orientados a la Impresión

Para garantizar que un modelo 3D se imprima correctamente y sus mecanismos funcionen desde el primer intento, se deben cuidar ciertos aspectos clave durante el modelado:

1. **Espacio entre piezas:** Si dejas las partes pegadas en el programa 3D, saldrán fundidas en la impresora. Siempre se debe dejar un pequeño espacio de separación entre las caras que se mueven.
2. **Voladizos y Ángulo:** La impresora construye de abajo hacia arriba. Las formas con inclinaciones muy pronunciadas o techos flotantes necesitan apoyarse sobre el plástico de la capa anterior para no caerse o poner soposrtes extras.
3. **Orientación de la pieza:** Colocar el modelo en la postura correcta dentro de la plataforma de la impresora evita el uso excesivo de soportes y hace que las articulaciones tengan mayor suavidad al moverse.

---

## 4. Proyecto de Aplicación: Oruga Articulada Print-in-Place

Como proyecto principal de la práctica, se diseñó y fabricó una **oruga articulada** utilizando el método de impresión en una sola pieza (*Print-in-Place*).

### Proceso de Diseño y Funcionamiento
* **Modelado de la Unión en T:** Para unir las esferas oruga, se diseñó un conector interno en forma de "T" que encaja dentro de la cavidad de la siguiente esfera.
* **Movimiento Revolucionado:** Al aplicar revolución y esquinas redondeadas al eje de la "T", la geometría actúa como una bisagra atrapada. Esto le da a la oruga la libertad de girar y doblarse un poco de forma fluida.
* **Print in place:**** La "T" y la cavidad del adyacente se modelaron juntas dentro del mismo espacio pero manteniendo la separación adecuada. Al imprimirse, la estructura de la "T" queda atrapada mecánicamente dentro de la esfera sin tocarlo directamente, impidiendo que los eslabones se zafen o se separen, pero permitiendo un movimiento articulado inmediato al retirarla de la impresora.

---

## 5. Fotos
![Foto1](../imagenes/o (1).png){loading=lazy}
![Foto1](../imagenes/o (2).png){loading=lazy}
![Foto1](../imagenes/o (3).png){loading=lazy}
![Foto1](../imagenes/oo (1).jpeg){loading=lazy}
![Foto1](../imagenes/oo (2).jpeg){loading=lazy}
---


## 6. Conclusión

El uso de uniones en el diseño 3D expande por completo las posibilidades de la fabricación aditiva. Entender cómo se comportan geometrías como las **uniones en T revolucionadas** permite crear mecanismos complejos como la oruga articulada, logrando piezas funcionales, resistentes y con movimiento real en un solo proceso de impresión *Print-in-Place*, optimizando tiempos de trabajo y eliminando por completo la etapa de armado manual.