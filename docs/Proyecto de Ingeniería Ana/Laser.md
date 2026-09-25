# Reporte de Laboratorio: Puesta en Marcha y Operación de Cortadora Láser Industrial
**Institución:** Universidad Iberoamericana Puebla  
**Departamento:** Ingenierías / Mecatrónica  
**Asignatura:** Proyectos de Ingeniería  
**Ubicación:** Instituto de Diseño e Innovación Tecnológica (IDIT)

---

## 1. Objetivos
* Comprender el protocolo de encendido y operación segura de una cortadora láser de grado industrial (CAMFive CFL-CMA1390T).
* Dominar la interfaz del software *SmartCut*, desde el uso de la llave física de licencia hasta la importación y edición de vectores (`.DXF`) y texto.
* Configurar parámetros de potencia y velocidad según el tipo de capa (corte o grabado).
* Analizar el concepto de *kerf* (sangría de corte), su variación en función del material y su impacto en la precisión dimensional del proyecto.

---

## 2. Marco Teórico: El Kerf y su Relación con los Materiales

El **kerf** (o sangría) es el ancho del material que el haz láser evapora o remueve al momento de realizar un corte. Aunque el láser se percibe como un punto sin grosor, en la práctica el haz focalizado tiene un diámetro finito.

### Factores que afectan el Kerf:
1. **Tipo de Material:** Materiales con mayor conductividad térmica o menor punto de sublimación (como ciertos polímeros o acrílicos) tienden a presentar un kerf ligeramente mayor que materiales densos como el MDF o la madera.
2. **Espesor del Material:** A mayor grosor, se requiere mayor energía o menor velocidad, lo que incrementa la zona afectada por el calor.
3. **Potencia y Velocidad:** Una mayor potencia o velocidad reducida aumentan la cantidad de energía depositada por unidad de longitud, ensanchando la sangría.
4. **Lente y Distancia Focal:** La distancia focal del lente determina el tamaño del punto de enfoque (*spot size*); un punto más pequeño produce un kerf más angosto.

### Importancia en Ingeniería:
En proyectos de ingeniería donde se requieren ensambles a presión (*press-fit*), engranajes o tolerancias estrechas, **no compensar el kerf resulta en piezas holgadas o fuera de especificación**. Si el láser corta exactamente sobre la línea teórica del vector, el resultado final será más pequeño que el diseño original por un valor igual a la mitad del kerf en cada borde ($\frac{kerf}{2}$). Por ello, en el software o en el diseño se debe aplicar un desfase (*offset*) exterior para mantener las dimensiones reales deseadas.

---

## 3. Registro Audiovisual y Descripción de Procedimientos

A continuación se detalla la documentación técnica en video integrada en la estructura del repositorio local.

### Video 1: Inicialización del Software SmartCut e Importación de Archivo
* **Descripción:** En este segmento se muestra la apertura del programa *SmartCut* en la computadora del laboratorio. Se realiza la inserción de la memoria USB que contiene la licencia/llave de permisos para habilitar las funciones de comunicación con la máquina. Posteriormente, se efectúa la importación de un archivo vectorial en formato `.DXF`.

![video1](../../Imagenes/Video1.zip)

---

### Video 2: Ajuste de Unidades, Escalado y Edición de Piezas
* **Descripción:** Demostración de la verificación de unidades dentro del software, asegurando que el espacio de trabajo esté configurado en milímetros ($mm$). Se observa el procedimiento para verificar dimensiones reales de las piezas importadas, así como la duplicación y acomodo de elementos sobre el lienzo de trabajo para optimizar el área del material.

![video2](../../Imagenes/video2.zip)


---

### Video 3: Inserción de Texto y Asignación de Capas de Grabado/Corte
* **Descripción:** Explicación del proceso para agregar texto directamente en la plataforma, edición de tipografías y el procedimiento para clasificar geometrías mediante colores de capa. Esto permite diferenciar operacionalmente qué elementos se procesarán como grabado vectorial y cuáles como corte.

![video3](../../Imagenes/video3.zip)


---

### Video 4: Configuración de Parámetros de Operación (Potencia y Velocidad)
* **Descripción:** Ajuste técnico de la velocidad de desplazamiento ($\frac{mm}{s}$) y el porcentaje de potencia máxima del tubo láser para cada capa de color. Se enfatiza cómo la selección de estos valores determina la profundidad del grabado o la capacidad de atravesar el material de trabajo sin quemar las aristas.

![video4](../../Imagenes/video4.zip)


---

### Video 5: Puesta en Marcha Física de la Cortadora Láser
* **Descripción:** Demostración en la cortadora láser industrial CAMFive (Modelo CFL-CMA1390T). Muestra el encendido del sistema general, el uso de la llave física de seguridad, la calibración y movimiento de los cabezales desde el panel de control, y la indicación obligatoria de mantener la cubierta de protección cerrada durante el envío y ejecución del archivo.


![video5](../../Imagenes/video5.zip)

---

## 4. Conclusiones
* La correcta secuenciación desde la preparación del vector en *SmartCut* hasta el encendido físico de la máquina asegura un proceso eficiente y previene accidentes de laboratorio.
* El análisis del *kerf* es indispensable en la manufactura con láser: el tipo de material impone límites físicos que deben compensarse en el software de diseño para garantizar la precisión dimensional de los componentes.
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
    
   