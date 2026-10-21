# Reporte de Práctica: Diseño de Mecanismos Articulados Print-in-Place y Manufactura Aditiva en Prusa MK4S

**Institución:** Universidad Iberoamericana Puebla  
**Departamento:** Ingenierías / Mecatrónica  
**Asignatura:** Proyectos de Ingeniería  
**Ubicación:** Laboratorio de Manufactura e Impresión 3D  
**Supervisión Académica:** Mtro. Oliver Ochoa  
**Software Utilizado:** SolidWorks 3D CAD / PrusaSlicer  
**Equipo de Manufactura:** Impresora 3D Prusa MK4S (Tecnología FDM/FFF)  

---

## 1. Objetivos

* **General:** Diseñar y manufacturar un mecanismo articulado con geometría compleja (*Print-in-Place*) utilizando SolidWorks y la impresora 3D Prusa MK4S, garantizando articulación mecánica funcional directamente desde la cama de impresión sin ensambles posteriores.
* **Específicos:**
  1. Dominar el uso avanzado de planos constructivos y geometría de referencia en SolidWorks para generar uniones articuladas internas en múltiples direcciones.
  2. Aplicar principios de tolerancias dimensionales en modelado CAD para evitar la fusión por soldadura térmica entre eslabones móviles adyacentes.
  3. Configurar los parámetros de rebanado (*slicing*) en PrusaSlicer para optimizar el peso, tiempo de impresión y consumo de filamento, ajustando el relleno (*infill*) al 5%.
  4. Operar la impresora 3D Prusa MK4S, comprendiendo la preparación de la cama caliente, la nivelación automática (*mesh bed leveling*) y el control de deposición del material.

---

## 2. Marco Teórico y Principios de Diseño *Print-in-Place*

### A. Metodología *Print-in-Place* (PiP)
El diseño *Print-in-Place* permite fabricar mecanismos articulados totalmente funcionales en un solo ciclo de impresión aditiva. La clave del éxito de este método reside en la gestión estricta de las **tolerancias de aire (clearance)** entre piezas móviles:
* **Holgura Recomendada:** Se requiere una separación libre de entre $0.30\text{ mm}$ y $0.50\text{ mm}$ entre las aristas de las bisagras macho y hembra.
* **Geometría de Cuelgue (Overhangs):** Las juntas se diseñan con ángulos autosoportados (menores a $45^\circ$) o uniones tipo esferoide/anillo cerrado para evitar la necesidad de soportes internos que bloqueen el movimiento.

### B. Densidad de Relleno (*Infill Density*) y Optimización Estratégica
En piezas decorativas o articuladas sin carga estructural crítica, el Relleno al **5%** (con patrón giroide o de rejilla) aporta suficientes apoyos internos para las capas superiores (*top solid layers*) reduciendo drásticamente:
1. El peso total del componente.
2. El gasto ineficiente de filamento PLA/PETG.
3. El tiempo de residencia del extrusor por capa, evitando sobrecalentamiento en zonas delgadas.

---

## 3. Desarrollo Experimental y Descripción de Evidencias CAD / Manufactura

Bajo la instrucción del Mtro. Oliver Ochoa, se modeló un pulpo articulado utilizando planos oblicuos y revolucionados en SolidWorks para definir cada eslabón de los tentáculos.

### Figura 1: Acotamiento de Tolerancias y Diámetros de Eslabón
Se observa la vista en planta del perfil del tentáculo. Se utilizaron círculos concentricos acotados ($\varnothing 6.50\text{ mm}$, $\varnothing 5.50\text{ mm}$, $\varnothing 3.50\text{ mm}$) para garantizar que la bisagra interna mantenga la separación radial requerida antes de extruir el siguiente segmento.

![Croquis de tolerancias en SolidWorks](../Imagenesana/patapulpo.png)
*Figura 1: Verificación de diámetros y distancias de separación entre articulaciones en el croquis 2D.*

---

### Figura 2: Detalle de Holgura Interna y Planos de Referencia
Se aprecian las cotas de precisión ($\varnothing 6.50\text{ mm}$, $\varnothing 5.50\text{ mm}$, $\varnothing 2.80\text{ mm}$) y la disposición del `Plano 2`. Estos planos desfasados permitieron proyectar el ángulo de caída de cada tentáculo manteniendo las articulaciones aisladas en el espacio 3D.

![Detalle de plano de referencia y cotas](../Imagenesana/patapulpo2.png)
*Figura 3: Trabajo con geometría de referencia (`Plano 2`) para la creación de uniones en serie.*

---

### Figura 3: Modelo Tridimensional Completo en SolidWorks
Captura en pantalla del ensamble unibody del pulpo articulado en SolidWorks. Se aprecian múltiples planos de referencia (`Plano 4`, `Plano 6`, `Plano 12`) utilizados para proyectar la simetría y curvatura de los 8 tentáculos alrededor de la cabeza.

![Modelo 3D del pulpo en SolidWorks](../Imagenesana/pulposolid.png)
*Figura 2: Renderizado e inspección de planos constructivos para el pulpo articulado.*

---

### Figura 4: Impresión Aditiva en Prusa MK4S
El modelo fue exportado a formato `.STL`, procesado en PrusaSlicer con relleno al 5% y enviado a la impresora **Prusa MK4S**. En la pantalla LCD se observa el avance del proceso (98%) y la distribución plana de los tentáculos sobre la cama de impresión de PEI rugoso.

![Impresora 3D Prusa MK4S en proceso](../Imagenesana/pulpoimpre.png)
*Figura 4: Fabricación aditiva del mecanismo Print-in-Place en la Prusa MK4S.*

---

### Figura 5: Pieza Finalizada y Articulada
Muestra la pieza retirada de la base de impresión. Gracias al control del *infill* al 5% y al cálculo exacto de holguras en SolidWorks, la pieza resultó liviana, rígida en la cabeza y con flexibilidad fluida e independiente en cada una de sus extremidades sin requerir limpieza adicional.

![Pieza final impresa y articulada](../Imagenesana/pulplisto.png)
*Figura 5: Resultado final del pulpo articulado impreso en una sola pieza.*

---

## 4. Resumen de Parámetros de Impresión

| Parámetro | Configuración en PrusaSlicer / Prusa MK4S | Propósito |
| :--- | :--- | :--- |
| **Material** | Filamento PLA Rojo ($1.75\text{ mm}$) | Buena adherencia y rigidez dimensional |
| **Densidad de Relleno** | **5% (Giroide / Grid)** | Reducción de peso, costo y tiempo de fabricación |
| **Altura de Capa** | $0.20\text{ mm}$ (Quality) | Balance óptimo entre acabado superficial y velocidad |
| **Soportes** | Desactivados (*None*) | Geometría 100% autosoportada por diseño |
| **Temperatura Extrusor/Cama** | $215^\circ\text{C} / 60^\circ\text{C}$ | Fusión uniforme sin deformación en primeros estratos |

---

## 5. Conclusiones

* La metodología *Print-in-Place* permite optimizar los procesos de manufactura al eliminar las etapas de ensamblado manual y tolerado posterior.
* El dominio de la geometría de referencia (planos desfasados y angulados) en SolidWorks es esencial para construir modelos con movimientos complejos tridimensionales.
* La calibración de parámetros en PrusaSlicer (especialmente la reducción del relleno al 5%) demostró que es posible obtener piezas funcionales y ligeras sin comprometer la integridad estructural ni la estética de la pieza final.
//holasubirepooooonoswsporknosesube