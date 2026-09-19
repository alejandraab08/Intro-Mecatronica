// Comment Ana

#include <iostream>
#include <fstream>
#include <string>

int main() {
    std::ofstream reporte("Reporte_SolidWorks_Kerf_Bisagras.md");

    if (!reporte.is_open()) {
        std::cerr << "Error al crear el archivo del reporte." << std::endl;
        return 1;
    }

    reporte << R"(# Reporte de Práctica: Diseño y Ensamblaje en SolidWorks para Corte Láser

**Institución:** Universidad Iberoamericana / Departamento de Ingeniería / Mecatrónica  
**Asignatura:** Manufactura Avanzada / CAD-CAM  
**Software:** SolidWorks  
**Proyecto:** Modelado de Piezas Ensamblables, Ajuste de Kerf y Bisagras Vivas  

---

## 1. Objetivos

* **General:** Aprender el diseño paramétrico de piezas en SolidWorks orientadas al proceso de manufactura por cortadora láser.
* **Específicos:**
  1. Comprender el concepto de **Kerf** (sangría/ancho del haz láser) y su impacto en las tolerancias mecánicas y el ajuste de ensambles (macho-hembra).
  2. Analizar la técnica de **bisagras vivas** (*lattice hinges* / *kerf bending*) para dotar de flexibilidad a materiales rígidos (como MDF o acrílico).
  3. Desarrollar las bases para la modelación y ensamblaje del proyecto final: una ballena articulada con bisagras vivas.

---

## 2. Conceptos Clave

* **Kerf:** Es la cantidad de material que el haz del láser remueve o sublima al realizar un corte. Si no se compensa este grosor en el croquis CAD, las piezas ensamblables quedarán holgadas.
* **Bisagras Vivas (Living Hinges):** Patrones de cortes intercalados en un material rígido que reducen su rigidez torsional y flexional, permitiendo que se doble sin romperse.

---

## 3. Descripción de las Evidencias (Imágenes Provistas)

|<img src="Imagenes/WhatsApp Image 2026-09-18 at 08.44.51.jpeg" width="400" alt="Disposición de Piezas"> | <img src="Imagenes/WhatsApp Image 2026-09-18 at 08.45.17.jpeg" width="400" alt="Modelado 3D"> |
| :---: | :---: |
| *Figura 1: Muestra la proyección 2D de múltiples placas cuadradas alineadas con almenas (dientes de ensamble).* | *Figura 2: Pieza extruida individual con su correspondiente grosor de material, lista para simular el ensamblaje.* |

|<img src="Imagenes/WhatsApp Image 2026-09-18 at 08.45.08.jpeg" width="400" alt="Croquizado Paramétrico"> | <img src="Imagenes/WhatsApp Image 2026-09-18 at 08.45.01.jpeg" width="400" alt="Perspectiva 3D"> |
| :---: | :---: |
| *Figura 3: Muestra el boceto con cotas definidas ($50.00\text{ mm}$ de lado, $6.00\text{ mm}$ por diente y $3.00\text{ mm}$ de espesor).* | *Figura 4: Vista tridimensional de la pieza con relieve donde se aprecian los bordes dentados mecánicos.* |

---

## 4. Resumen de Pasos y Parámetros

| Etapa | Operación | Parámetro / Resultado |
| :--- | :--- | :--- |
| **1. Croquis 2D** | Definición paramétrica | $50.00 \times 50.00\text{ mm}$, Diente: $6.00\text{ mm}$, Espesor: $3.00\text{ mm}$ |
| **2. Compensación** | Aplicación de Offset por Kerf | $+0.09\text{ mm}$ por borde (Kerf total de $0.18\text{ mm}$) |
| **3. Flexibilidad** | Patrón de Bisagra Viva | Habilitado para otorgar curvatura al cuerpo de la ballena |
| **4. Ensamblaje** | Extrusión y simulación 3D | Verificación de uniones macho-hembra a presión exacta |

---

## 5. Conclusiones

1. El uso de cotas paramétricas en SolidWorks permite adaptar rápida y fácilmente las piezas al grosor real del material a cortar.
2. La consideración del **Kerf** es fundamental en la etapa de modelado; si no se compensa, las holguras provocan que el ensamble quede flojo.
3. La implementación de **bisagras vivas** rompe las limitaciones del corte 2D, permitiendo crear formas volumétricas complejas y orgánicas como la ballena.
)";

    reporte.close();
    std::cout << "Reporte generado exitosamente como 'Reporte_SolidWorks_Kerf_Bisagras.md'." << std::endl;
    return 0;
}
    
