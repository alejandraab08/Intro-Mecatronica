# Proyecto: Ballena en Corte Láser

---

## 📋 Información General

* **Proyecto:** Ensamble de Ballena 3D
* **Material:** MDF (*2.6mm*)
* **Integrantes del equipo:** Ana Paola Gomez J. y Alejandra Aguirre B.
* **Programas:** SolidWorks, EDrawings, 
* **Maquinaria:** Cortadora Láser CO₂

---

## 1. 💡 Introducción

El objetivo de este proyecto fue diseñar y fabricar un modelo tridimensional y ensamblable de nuestra elección a partir de láminas planas de MDF (en este caso una ballena), utilizando diseño asistido por computadora con SolidWorks y corte láser.

---

## 2. Inspiración y Conceptualización

Primero, mi compañera y yo buscamos referencias de ensamblaje/rompecabezas 3D para obtener la inspiración necesaria. Una vez decidido el diseño deseado (la ballena), pasamos a la fase inicial del diseño que es el análisis.

1. **Boceto a mano:** Dibujamos las piezas principales en papel (espina, costillas/cuerpo, aletas, cola, cabeza, etc).
2. **Estimación de proporciones:** Nos imaginamos las medidas generales del modelo para mantener una escala funcional antes de pasar nuestras ideas a modelos en computadora.
3. **Mecanismo de ensamble:** Planteamos un sistema de ranuras tipo *press-fit* (usando presión) que permitiera armar el modelo sin necesidad de resistol ni pegamentos.

---

## 3.  Diseño CAD en SolidWorks y Tolerancias (Kerf)

Llevamos los bocetos que hicimos en papel al entorno de SolidWorks.

### Consideración del Kerf!!!!!
Uno de los factores más importantes en el diseño para corte láser es el **Kerf** (el grosor del material que el rayo láser quema (se "come") al cortar). Para asegurar que las uniones ajustaran con el método **press-fit** sin quedar flojas ni demasiado apretadas, compensamos las dimensiones de las ranuras considerando el grosor del MDF (2.6 mm) y un **Kerf de 0.15 mm**. Ya que el kerf elimina 0.15 mm extras cada vez que corta el material, lo que tuvimos que hacer fue considerar y sumar esa medida a los contornos de la figura, y a las ranuras/hoyos le restamos los 0.15mm

> **Nota:** Si utilizamos de ejemplo la forma de una dona, el perímetro de la figura tendría que ser mayor a lo deseado y el hoyo menor.


---

## 4.  Primer Corte y Pruebas de Ensamblaje

Pasamos los planos a formato .DXF que es el que se ocupa para el corte láser y realizamos la primera prueba.

### Errores 
Al intentar armar el primer prototipo, identificamos varios problemas en nuestra ballena:

* **Puntos de interferencia:** Gracias al error humano, ciertas piezas que debían ser símetricas no lo fueron en nuestro primer corte. Esto lo arreglamos usando la herrmaienta de simetría en SolidWorks para nuestro segundo intento.
* **Potencia:** No ajustamos correctamente la potencia y la velocidad de la cortadora láser, lo que provocó que ciertas piezas se quemaran de más y por lo tanto se rompieran.
* **Calibración del equipo:** Nos faltó calibrar la máquina, lo cual causó que unas piezas quedaran quemadas, otras bien y que otras ni siquiera se hayan cortado (no pasó el láser).
---

## 5. Rediseño y Resultado Final

Regresamos al modelo en SolidWorks para hacer los ajustes necesarios:

1. **Modificación de cotas:** Se corrigieron las medidas de las piezas y se aplicaron simetrías.
2. **Segundo corte:** Volvimos a enviar las piezas a la cortadora láser.
3. **Ensamble:** Las piezas encajaron perfectamente a presión, logrando una estructura limpia y con muy buenas uniones press-fit.

---
## 6. Fotos y Evidencias
![Foto1](../imagenes/ballena (1).png){loading=lazy}
![Foto2](../imagenes/ballena (2).png){loading=lazy}
![Foto3](../imagenes/ballena (3).png){loading=lazy}
![Foto4](../imagenes/ballena (4).png){loading=lazy}

## Conclusión

Este proyecto nos permitió experimentar por completo el proceso diseño y corte láser: desde la idea y boceto en papel, hasta el uso de tolerancias, diseño por computadora y prototipado. El ajuste correcto del Kerf y la corrección tras el primer intento fueron claves para conseguir una **ballena ensamblable** precisa y bonita.