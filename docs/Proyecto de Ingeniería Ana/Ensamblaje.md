# Reporte de Práctica: Diseños en SolidWorks, Uniones Mecánicas y Bisagras Vivas

**Institución:** Universidad Iberoamericana Puebla  
**Departamento:** Ingenierías / Mecatrónica  
**Asignatura:** Proyectos de Ingeniería  
**Ubicación:** Instituto de Diseño e Innovación Tecnológica (IDIT)  
**Supervisión Académica:** Mtro. Oliver Ochoa (Coordinador de Carrera)  

---

## 1. Objetivos

* **General:** Desarrollar habilidades de diseño CAD en SolidWorks orientadas a manufactura por corte láser, aplicando conceptos de ensamble mecánico macho-hembra, compensación de Kerf y flexibilidad mediante patrones de bisagras vivas.
* **Específicos:**
  1. Diseñar piezas cuadradas paramétricas con almenas y pestañas de ensamble a presión (*press-fit*).
  2. Analizar los diferentes tipos de uniones mecánicas (ensambles a tope, a media madera, por almenas/dientes y uniones tipo chaveta).
  3. Comprender el concepto de **Kerf** y calcular el *offset* dimensional requerido para garantizar el ajuste exacto de las piezas.
  4. Explorar los diversos patrones de **bisagras vivas** (*lattice hinges*) para otorgar flexibilidad a materiales rígidos (MDF/acrílico) según su geometría.

---

## 2. Marco Teórico y Conceptos Clave

### A. Tipos de Uniones Mecánicas para Corte Láser
* **Uniones Dentadas (Almenas / Pestañas):** Acoplamientos macho-hembra en los bordes de los perfiles que distribuyen los esfuerzos de corte a lo largo del ensamble.
* **Uniones T-Slot (Con Perno o Cuña):** Aseguran las caras tridimensionales utilizando un sujetador mecánico o cuña de presión.
* **Compensación de Kerf:** El haz láser sublima un ancho de material (típicamente entre $0.10\text{ mm}$ y $0.20\text{ mm}$). En SolidWorks se aplica un *offset* hacia el exterior en los contornos macho para que el ensamble no quede holgado.

### B. Patrones de Bisagras Vivas (Living Hinges)
Las bisagras vivas consisten en cortar patrones de celosía intercalados en una lámina rígida. La flexibilidad, el ángulo de doblado y la resistencia estructural cambian según el patrón seleccionado:
* **Líneas Paralelas Intercaladas (Estándar):** Otorga un radio de curvatura amplio y flexión uniforme.
* **Patrón Ondulado / Diamante:** Distribuye la tensión en múltiples direcciones, ideal para curvaturas complejas u orgánicas (como la estructura de una ballena articulada).
* **Patrón de Panal (Hexagonal):** Brinda mayor rigidez torsional manteniendo cierta capacidad de flexión.

---

## 3. Desarrollo Experimental y Análisis de Evidencias CAD

Bajo la supervisión del Mtro. Oliver Ochoa, se desarrollaron los modelos paramétricos en SolidWorks analizando las cotas y la tolerancia de encaje.

### Figura 1: Disposición y Plano de Ensambles 2D
Se trazó la plantilla de placas cuadradas alineadas, incorporando almenas y pestañas en los bordes para optimizar el espacio de corte y preparar la fabricación en lote.

![Vista de Plano y Disposición de Piezas](Imagenes/WhatsApp Image 2026-09-18 at 08.44.51.jpeg)
*Figura 1: Proyección en plano 2D con la disposición organizada de los cuadrados dentados y pestañas de ensamble.*

---

### Figura 2: Extrusión Paramétrica de la Pieza
Se realizó la operación de extrusión considerando el espesor nominal de la lámina de trabajo ($3.00\text{ mm}$), permitiendo validar el volumen tridimensional de la pieza individual.

![Modelado 3D de Pieza Extruida](piezas.png)
*Figura 2: Pieza extruida tridimensionalmente en SolidWorks lista para pruebas de ensamble.*

---

### Figura 3: Acotado y Tolerancias en Croquis
Se definieron las variables geométricas del croquis: base cuadrada de $50.00\text{ mm}$, profundidad de pestaña de $3.00\text{ mm}$ (igual al espesor del material) y ancho de almena de $6.00\text{ mm}$, aplicando el *offset* de Kerf.

![Croquis Acotado en SolidWorks](Imagenes/WhatsApp Image 2026-09-18 at 08.45.08.jpeg)
*Figura 3: Detalle de cotas paramétricas en el croquis 2D ($50.00\text{ mm}$ de lado y $6.00\text{ mm}$ por pestaña).*

---

### Figura 4: Perspectiva 3D y Verificación de Uniones
Se inspeccionó el sólido en perspectiva isométrica para verificar que el relieve de los dientes no presentara colisiones antes de la simulación del ensamble tridimensional.

![Vista Isométrica Tridimensional](Imagenes/WhatsApp Image 2026-09-18 at 08.45.01.jpeg)
*Figura 4: Vista en perspectiva 3D mostrando los relieves dentados de la cara de ensamble.*

---

## 4. Resumen de Parámetros y Resultados

| Etapa de Diseño | Operación en SolidWorks | Propósito Técnico |
| :--- | :--- | :--- |
| **Geometry Base** | Croquis de $50.00 \times 50.00\text{ mm}$ | Establecer la dimensión estructural de la cara plana |
| **Pestañas / Almenas** | Cortes/Extrusiones de $6.00\text{ mm}$ | Generar la unión mecánica macho-hembra |
| **Ajuste por Kerf** | Offset exterior de $+0.09\text{ mm}$ | Evitar holguras y lograr ensamble a presión (*press-fit*) |
| **Living Hinges** | Patrón de cortes intercalados | Permitir la curvatura de piezas rígidas para formas complejas |

---

## 5. Conclusiones

* Se aprendió a modelar geométricamente componentes en SolidWorks considerando de origen las limitaciones y tolerancias del proceso de manufactura sustractiva por láser.
* La adecuada selección del patrón de bisagra viva permite transformar láminas rígidas planas en volúmenes tridimensionales flexibles y orgánicos.
* Las sesiones supervisadas por el Mtro. Oliver Ochoa permitieron comprender la relación fundamental entre la teoría del modelado CAD, las tolerancias físicas (Kerf) y el ensamblaje mecánico real.
)";

    reporte.close();
    
    std::cout << "============================================================" << std::endl;
    std::cout << " ¡EXITO! Reporte generado como 'Reporte_SolidWorks_Uniones_Bisagras_IDIT.md'" << std::endl;
    std::cout << " Puedes abrirlo y previsualizarlo directamente en VS Code." << std::endl;
    std::cout << "============================================================" << std::endl;   
