#include <iostream>
#include <fstream>
#include <string>

int main() {
    std::ofstream reporte("Reporte_Cortadora_Laser.md");

    if (!reporte.is_open()) {
        std::cerr << "Error al crear el archivo del reporte." << std::endl;
        return 1;
    }

    reporte << R"(# Reporte de Práctica: Operación de Cortadora Láser Industrial

**Institución:** Universidad Iberoamericana / Departamento de Mecatrónica  
**Equipo:** Cortadora Láser CAMFive (Modelo CFL-CMA1390T)  
**Software:** SmartCanvas  

---

## 1. Objetivos

* **General:** Comprender y aplicar el protocolo seguro de encendido, configuración y operación de la cortadora láser industrial CAMFive.
* **Específicos:**
  1. Familiarizarse con el entorno del software SmartCanvas y sus requerimientos de hardware (llave dongle USB).
  2. Ejecutar la correcta importación de vectores en formato `.DXF` manteniendo el control de escala y unidades.
  3. Configurar los parámetros de trabajo (potencia máxima/mínima y velocidad) según el material a procesar.
  4. Implementar las medidas de seguridad obligatorias durante el procedimiento.

---

## 2. Descripción del Procedimiento y Evidencia de Video

* **Video 1 (00:00 - 01:24) - Encendido y Componentes del Equipo:**  
  Se acciona el interruptor de encendido general y la llave de seguridad. Se identifican los dos cabezales de corte y se verifica el cierre de la tapa superior (condición obligatoria para operación segura).

* **Video 2 (00:00 - 00:32) - Verificación de Licencia y Software:**  
  Se conecta la memoria USB (llave dongle). Sin esta llave, el software SmartCanvas no inicializa el control del equipo.

* **Video 3 (00:00 - 01:42) - Manipulación Vectorial en SmartCanvas:**  
  Carga de geometrías vectoriales (piezas con ensamble, textos y patrones flex). Uso de herramientas de edición: texto, rotación, escalado y distribución.

* **Video 4 (00:00 - 00:29) - Importación y Escala de Archivos:**  
  Exportación en formato `.DXF` desde software CAD (p. ej., SolidWorks). En SmartCanvas se selecciona `File > Import` asegurando que las unidades (milímetros) coincidan para evitar errores dimensionales.

* **Video 5 (00:00 - 00:11) - Parámetros de Corte y Grabado:**  
  En la tabla de capas (*Layer Parameters*), se asignan valores de potencia máxima/mínima (*Max/Min Power*) y velocidad (*Work Speed*) según el material.

---

## 3. Resumen de Pasos y Parámetros

| Etapa | Operación | Requisito / Parámetro |
| :--- | :--- | :--- |
| **1. Seguridad** | Encendido físico y verificación | Tapa cerrada y llave activada |
| **2. Software** | Validación de licencia | Conexión de Dongle USB |
| **3. Importación** | Carga de geometría CAD | Archivo `.DXF` en milímetros (mm) |
| **4. Configuración** | Asignación de capa | Potencia Máx/Mín (%) y Velocidad (mm/s) |

---

## 4. Conclusiones

El correcto seguimiento de esta metodología garantiza la preservación de la máquina industrial y la seguridad del operador. La verificación estricta de las unidades de importación en formato `.DXF` y la adecuada asignación de velocidad y potencia por capa permiten obtener piezas precisas y con acabados de calidad industrial.
)";

    reporte.close();
    std::cout << "Reporte generado exitosamente como 'Reporte_Cortadora_Laser.md'." << std::endl;
    return 0;
}
