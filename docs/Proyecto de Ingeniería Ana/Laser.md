# Reporte de Práctica: Operación de Cortadora LáserKerfustrial, Gestión de Kerf e Importación CAD

**Institución:** Universidad Iberoamericana Puebla  
**Departamento:** Ingenierías / Mecatrónica  
**Asignatura:** Proyectos de Ingeniería  
**Ubicación:** Instituto de Diseño e Innovación Tecnológica (IDIT)  
**Equipo:** Cortadora Láser Industrial CAMFive (Modelo CFL-CMA1390T)  
**Software:** SmartCanvas / SolidWorks  

---

## 1. Objetivos

* **General:** Operar la cortadora láser industrial CAMFive desde el protocolo de encendido hasta la ejecución del trabajo, comprendiendo la influencia del Kerf y las propiedades del material en la precisión dimensional.
* **Específicos:**
  1. Identificar el protocolo de encendido, uso de la llave de seguridad, enclavamiento de la tapa y requerimiento del Dongle USB para el software SmartCanvas.
  2. Analizar el desglose procedimental de los videos de la práctica (encendido, validación, edición de vectores, importación `.DXF` y asignación de parámetros por capa).
  3. Comprender el concepto de **Kerf** (sangría de quemado) y su relación directa con el espesor, densidad y punto de sublimación/combustión del material.
  4. Documentar el flujo de trabajo mediante el análisis de evidencias visuales e importación de vectores CAD.

---

## 2. Marco Teórico: El Kerf y su Relación con el Material

El **Kerf** es el ancho del material que el haz láser remueve o sublima al realizar un corte. No es una constante fija; varía según la física del proceso y las propiedades del material procesado:

* **Relación con el Tipo de Material:**
  * **MDF y Maderas:** Requieren mayor potencia debido a su densidad orgánica, lo que genera un Kerf más amplio ($0.15\text{ mm} - 0.22\text{ mm}$) por quemado de fibras.
  * **Acrílico (PMMA):** El láser funde y vaporiza el polímero dejando un borde pulido. Su Kerf es más estrecho y definido ($0.10\text{ mm} - 0.15\text{ mm}$).
  * **Polimeros y Cartones:** Tienen puntos de sublimación bajos; un exceso de potencia ensancha el Kerf descontroladamente.
* **Importancia Dimensional:** Si se diseña un ensamble macho-hembra de $3.00\text{ mm}$ sin compensar el Kerf en el CAD (*offset* exterior), las piezas quedarán holgadas y no mantendrán un ajuste a presión (*press-fit*).

---

## 3. Desglose del Procedimiento Basado en Evidencia en Video

### Video 1: Encendido Físico y Verificación de Componentes (00:00 - 01:24)
Se inicia el protocolo girando la llave de seguridad y accionando el interruptor general. Se revisa la estructura de los dos cabezales de corte y se verifica que la tapa superior esté totalmente cerrada. La máquina cuenta con un sensor interlock de seguridad que impide la emisión del haz láser si la tapa se encuentra abierta.

### Video 2: Validación de Licencia y Comunicación con SmartCanvas (00:00 - 00:32)
Se inserta la memoria USB de protección (llave Dongle) en la estación de trabajo. Al iniciar SmartCanvas, el programa autentica la licencia física. Sin este hardware, el software no habilita la comunicación ni el control de la cortadora industrial CAMFive.

### Video 3: Manipulación Vectorial y Edición en Galería (00:00 - 01:42)
Dentro del área de trabajo de SmartCanvas, se organizan vectores de piezas con ensambles, textos y patrones de flexibilidad. Se ejecutan transformaciones básicas como escalado, rotación, duplicación y organización de mapas de corte.

### Video 4: Importación Correcta de Archivos `.DXF` (00:00 - 00:29)
Se accede al menú `File > Import` para cargar el diseño exportado desde SolidWorks. Se enfatiza la verificación de las unidades de importación en **milímetros (mm)** para evitar errores de escala global en la geometría.

### Video 5: Asignación de Parámetros por Capas de Color (00:00 - 00:11)
En el panel *Layer Parameters*, se asignan valores de velocidad (*Work Speed*) y potencia (*Max/Min Power*) según el color del trazo: asignando baja potencia y alta velocidad para grabado/marcado, y mayor potencia con menor velocidad para corte completo.

---

## 4. Análisis de Evidencias e Imágenes del Repositorio

### Figura 1: Disposición 2D de Placas Dentadas
Muestra la organización en plano de piezas cuadradas con almenas. Se observa la estrategia de acomodo para optimizar el área del material y minimizar el desperdicio.

![Disposición 2D de Piezas](Imagenes/WhatsApp Image 2026-09-18 at 08.44.51.jpeg)
*Figura 1: Organización vectorial en plano 2D de placas dentadas para corte eficiente.*

---

### Figura 2: Extrusión y Simulación del Espesor
Representación en 3D de la pieza extruida a $3.00\text{ mm}$. Permite visualizar el espesor real del material antes de enviar el archivo al software de control láser.

![Pieza 3D Extruida](Imagenes/WhatsApp Image 2026-09-18 at 08.45.17.jpeg)
*Figura 2: Modelo 3D con extrusión simulada del volumen del material.*

---

### Figura 3: Croquis Acotado y Tolerancia por Kerf
Muestra las cotas paramétricas ($50.00\text{ mm}$ de contorno y $6.00\text{ mm}$ por diente). En esta etapa se define el *offset* de compensación para absorción del Kerf.

![Croquis Paramétrico Acotado](Imagenes/WhatsApp Image 2026-09-18 at 08.45.08.jpeg)
*Figura 3: Detalle de acotación paramétrica para control de dimensiones.*

---

### Figura 4: Isométrico 3D de uniones
Vista tridimensional en perspectiva que permite validar los relieves de los dientes y pestañas donde el haz láser realizará las trayectorias de corte vertical.

![Vista Isométrica Tridimensional](Imagenes/WhatsApp Image 2026-09-18 at 08.45.01.jpeg)
*Figura 4: Vista tridimensional de la pieza con relieve dentado.*

---

## 5. Resumen de Parámetros y Protocolo

| Etapa | Operación Clave | Condición / Parámetro |
| :--- | :--- | :--- |
| **1. Seguridad** | Verificación de encendido | Llave activada y Tapa protectora cerrada |
| **2. Software** | Verificación de licencia | Dongle USB conectado en la PC |
| **3. Importación** | Carga de vectores CAD | Formato `.DXF` configurado en milímetros (`mm`) |
| **4. Ajuste Kerf** | Compensación en trazado | Offset de $+0.08\text{ mm}$ a $+0.10\text{ mm}$ según material |
| **5. Ejecución** | Configuración por capas | Control de Potencia (Max/Min %) y Velocidad ($\text{mm/s}$) |

---

## 6. Conclusiones

* La operación de la cortadora láser CAMFive requiere el estricto cumplimiento de protocolos físicos (enclavamiento de tapa) y digitales (llave Dongle USB).
* El **Kerf** no es un defecto, sino una variable física predecible. Su correcta compensación en el software CAD es indispensable para garantizar el ensamble perfecto de piezas.
* La adecuada asignación de velocidad y potencia en SmartCanvas previene la sobrecombustión en materiales densos como MDF o la deformación térmica en polímeros.
)";

    reporte.close();
    
    std::cout << "============================================================" << std::endl;
    std::cout << " ¡EXITO! Reporte generado como 'Reporte_Cortadora_Laser_Industrial_IDIT.md'" << std::endl;
    std::cout << " Puedes abrirlo y previsualizarlo directamente en VS Code." << std::endl;
    std::cout << "============================================================" << std::endl;