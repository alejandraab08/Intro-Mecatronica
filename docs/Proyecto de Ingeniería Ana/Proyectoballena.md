# Reporte de Práctica: Prototipado y Ensamble 3D de Ballena mediante Corte Láser CO₂ y Compensación de Kerf

**Institución:** Universidad Iberoamericana Puebla  
**Departamento:** Ingenierías / Mecatrónica  
**Asignatura:** Proyectos de Ingeniería  
**Integrantes del Equipo:** Ana Paola Gomez J. y Alejandra Aguirre B.  
**Material:** MDF (Espesor nominal: 2.6 mm)  
**Herramientas y Software:** SolidWorks, EDrawings, Cortadora Láser CO₂  

---

## 1. Introducción y Objetivos

El presente trabajo documenta la conceptualización, modelado y manufactura de una estructura tridimensional articulada tipo rompecabezas con forma de ballena. El propósito principal fue aplicar el ciclo completo de diseño asistido por computadora (CAD) y manufactura sustractiva por láser CO₂, transformando láminas planas de MDF de 2.6 mm en un volumen ensamblable mediante uniones por interferencia a presión (*press-fit*), sin el uso de adhesivos.

---

## 2. Metodología de Conceptualización y Bocetaje

El proceso de desarrollo se estructuró en tres fases iniciales antes del modelado virtual:

1. **Bocetaje Manual:** Se dibujaron las geometrías principales del espécimen (columna central, costillas/secciones transversales, aletas pectorales, estructura caudal y cabeza).
2. **Dimensionado Proporcional:** Se definieron escalas funcionales para conservar las proporciones morfológicas de la ballena y permitir su estabilidad mecánica.
3. **Planteamiento de Juntas:** Se proyectó un sistema de acoplamiento por ranuras acopladas (*press-fit*), optimizado para ensamblarse únicamente mediante fricción y geometría.

---

## 3. Modelado CAD en SolidWorks y Compensación de Kerf

La transferencia de los bocetos al entorno 3D en SolidWorks exigió un análisis riguroso de la sangría del haz (*Kerf*).

### Análisis del Kerf
El *Kerf* representa el ancho de material sublimado/removido por la energía térmica del láser durante la trayectoria de corte (estimado en **0.15 mm** para este proceso). 

Para garantizar un ajuste *press-fit* firme (evitando holguras flojas o fracturas por sobredimensión), se aplicó la siguiente regla de compensación en el croquizado:
* **Contornos Externos (Perímetros):** Se incrementó su dimensión dimensionalmente sumando el offset del Kerf (+0.15 mm).
* **Contornos Internos (Ranuras / Aberturas):** Se redujo la apertura de las ranuras restando la tolerancia del Kerf (-0.15 mm) en relación con el grosor real del MDF (2.6 mm).

> *Analogía de compensación:* En una geometría anular o tipo dona, el perímetro exterior debe dimensionarse mayor al nominal, mientras que el agujero central debe acotarse menor.

---

## 4. Prototipado Inicial y Diagnóstico de Fallas

Se exportaron los planos a formato vector `.DXF` para ejecutar la primera prueba de manufactura láser. Durante la integración física se detectaron las siguientes anomalías:

* **Discrepancias Asimétricas:** Errores manuales en el trazado inicial provocaron desalineaciones en piezas que requerían simetría exacta.
* **Calibración de Potencia y Velocidad:** Un desajuste en la energía entregada sobrequemó los cantos del MDF, fragilizando las secciones delgadas y generando roturas al ensamblar.
* **Nivelación del Equipo:** La falta de calibración focal y de plano horizontal en la mesa de trabajo ocasionó zonas con corte incompleto y otras con sobrecombustión.

---

## 5. Optimización del Diseño y Manufactura Definitiva

Tras la evaluación del primer prototipo, se realizaron las correcciones necesarias en SolidWorks:

1. **Reajuste de Cotas y Simetrías:** Se aplicaron relaciones geométricas y herramientas de simetría de croquis para corregir los puntos de interferencia.
2. **Re-manufactura por Láser:** Se ajustaron los parámetros de potencia/velocidad y la distancia focal de la cortadora CO₂.
3. **Ensamblaje Final:** Las piezas refinadas encajaron de manera precisa y consistente, logrando una estructura limpia, rígida y autosoportada a presión.

---

## 6. Evidencias Audiovisuales y Fotográficas

![ballenauno](../imagenes/ba%20(1).jpeg)
![ballenados](../imagenes/ba%20(2).jpeg)

| *Figura 1: Vista general del modelo 3D ensamblado a presión.* | *Figura 2: Detalle de la estructura de costillas y columna vertebral en MDF.* |
![bouno](../imagenes/bo%20(1).png)
![bodos](../imagenes/bo%20(2).png)

*Figura 3: Croquizado vector en SolidWorks con ranuras de compensación.* | *Figura 4: Verificación de tolerancias y geometría de piezas en software.* |

---

## 7. Conclusiones

La realización de este proyecto permitió dominar el flujo metodológico entre la conceptualización manual, el diseño asistido por computadora y la manufactura aditiva/sustractiva. La correcta integración de la compensación de Kerf y la iteración técnica tras la primera prueba resultaron fundamentales para obtener un modelo tridimensional rígido, estéticamente limpio y funcionalmente preciso.

[zipballena](../Imagenesana/whale.zip)
