#include <iostream>
#include <fstream>
#include <string>

int main() {
    std::ofstream reporte("Reporte_Corte_y_Soldadura.md");

    if (!reporte.is_open()) {
        std::cerr << "Error al crear el archivo del reporte." << std::endl;
        return 1;
    }

    reporte << R"(# Reporte de Práctica: Corte, Esmerilado, Soldadura y Manejo de Generador

**Institución:** Universidad Iberoamericana Puebla  
**Departamento:** Ingenierías / Mecatrónica  

---

## 1. Objetivos

* **General:** Desarrollar habilidades prácticas en el manejo de herramientas de taller mecánico y soldadura, asegurando la correcta alineación y el cumplimiento de las normas de seguridad.
* **Específicos:**
  1. Utilizar la cortadora para la división precisa de perfiles metálicos.
  2. Aplicar técnicas de limado y esmerilado para la eliminación de rebabas y la preparación de biseles en las piezas cortadas.
  3. Operar el equipo de soldadura y el generador de corriente, verificando las conexiones eléctricas industriales.
  4. Unir los perfiles metálicos a 90° e inspeccionar la calidad del cordón de soldadura obtenido.

---

## 2. Equipo de Protección Personal (EPP) y Herramientas

### Equipo de Protección Personal
* Careta para soldar con sombra adecuada.
* Guantes de carnaza para soldadura y manipulación de metales calientes.
* Batas/mangas de algodón resistentes al fuego y botas de casquillo.
* Pechera de cuero.

### Herramientas y Maquinaria
* **Corte y Desbaste:** Tronzadora/cortadora de disco abrasivo, limas metálicas para desbaste fino.
* **Medición y Alineación:** Escuadra combinada Truper y regla metálica.
* **Equipo Eléctrico y Soldadura:** Generador/fuente de potencia, clavijas y conexiones industriales trifásicas, máquina de soldar por arco, mesa de trabajo perforada para fijación.

---

## 3. Desarrollo Experimental

### Paso 1: Preparación del Área y Conexión Eléctrica
Se inspeccionaron las instalaciones del taller de la Ibero Puebla, asegurando la correcta conexión de la alimentación principal mediante conectores industriales de seguridad tipo NEMA y cortinas de protección UV para soldadura.

![Conexión de Alimentación Industrial](Imagenes/IMG_9380.jpg)
*Figura 1: Conexión trifásica de seguridad para el equipo de soldadura.*

---

### Paso 2: Selección de Herramientas de Medición y EPP
Se alistaron los instrumentos de medición (escuadra de inglete Truper, regla) y el EPP completo para el manejo de herramientas de corte y desbaste.

![Herramientas y EPP](Imagenes/IMG_2204.jpg)
*Figura 2: Equipo de medición, limas y careta en las instalaciones del taller.*

---

### Paso 3: Corte de Perfiles Metálicos
Se sujetó firmemente el perfil PTR en la prensa de la tronzadora y se realizaron los cortes a $45^\circ$ y $90^\circ$, verificando la velocidad de avance para evitar el sobrecalentamiento excesivo del material.

![Corte con Tronzadora](Imagenes/IMG_9380_video.jpg)
*Figura 3: Proceso de corte de perfil metálico con disco abrasivo.*

---

### Paso 4: Esmerilado, Limado y Ensamble
Las rebabas resultantes del corte fueron removidas con limas metálicas para lograr un ajuste perfecto a $90^\circ$. La alineación precisa de las piezas cortadas se verificó mediante la escuadra Truper sobre la mesa de trabajo perforada.

|<img src="Imagenes/IMG_9376.jpg" width="400" alt="Piezas en Mesa de Trabajo"> | <img src="Imagenes/IMG_9373.jpg" width="400" alt="Detalle de Alineación"> |
| :---: | :---: |
| *Figura 4: Presentación de piezas cortadas sobre la mesa de soldadura.* | *Figura 5: Verificación de escuadra y alineación de perfiles.* |

---

### Paso 5: Soldadura por Arco
Se aplicaron puntos de fijación (*tack welds*) en la unión a $90^\circ$ y posteriormente se depositó el cordón de soldadura definitivo.

![Detalle de la Soldadura](Imagenes/IMG_9373.jpg)
*Figura 6: Inspección visual del cordón de soldadura y zonas con afectación térmica.*

---

## 4. Análisis de Resultados y Observaciones

* **Calidad del Corte:** Los cortes realizados con la tronzadora presentaron bordes rectos, requiriendo un limado moderado para eliminar pequeñas rebabas y favorecer la penetración de la soldadura.
* **Calidad de la Soldadura:**
  * **Aspectos positivos:** Se logró la unión estructural sólida de las piezas a $90^\circ$.
  * **Oportunidades de mejora:** En la muestra inspeccionada se observaron pequeñas porosidades e irregularidades en el cordón causadas por variaciones en la velocidad de avance de la antorcha y la longitud del arco.
* **Seguridad:** El uso de las mamparas de protección de vinil rojo evitó que el deslumbramiento y las chispas afectaran a otras personas en el laboratorio.

---

## 5. Conclusiones

* Se dominó la secuencia de manufactura básica para la conformación de estructuras metálicas: **medición $\rightarrow$ corte $\rightarrow$ desbaste $\rightarrow$ alineación $\rightarrow$ soldadura**.
* La preparación adecuada de las juntas mediante limado y la verificación constante del ángulo con la escuadra son determinantes para garantizar la geometría requerida.
* Se reconoció la importancia de operar los equipos con el EPP reglamentario y bajo las normas de seguridad establecidas en los laboratorios de la Ibero Puebla.
)";

    reporte.close();
    std::cout << "Reporte generado exitosamente como 'Reporte_Corte_y_Soldadura.md'." << std::endl;
    return 0;
}
