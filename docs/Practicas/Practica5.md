# Reporte de Práctica: Comunicación Inalámbrica vía Bluetooth

## 1. Objetivos
* **Establecer un enlace inalámbrico bidireccional:** Configurar el microcontrolador ESP32 mediante la librería `BluetoothSerial.h`, verificando el emparejamiento con una terminal móvil y la monitorización de datos en tiempo real.
* **Análisis de latencia y bloqueo de la CPU:** Evaluar el impacto de las funciones bloqueantes (`delay()`) en el ciclo principal (`loop()`), analizando el comportamiento de respuesta.

---

## 2. Esquema de Conexión Eléctrica
La interfaz de salida utiliza un LED conectado a una salida digital (GPIO) con su respectiva resistencia limitadora de corriente para prevenir un drenaje excesivo de corriente desde el puerto I/O del ESP32.


* **GPIO 2:** Salida digital configurada en modo `OUTPUT` (asociada opcionalmente al LED interno del módulo).
* **Resistencia ($R$):** $220\,\Omega$ a $330\,\Omega$ (limita la corriente a $\sim 8\text{–}12\text{ mA}$, respetando el límite máximo de $12\text{ mA}$ por pin en el ESP32).
* **Conexión a ground:** Cátodo del LED conectado a `GND`.

---

## 3. Código (Arduino)

El desarrollo del código se estructuró mediante la librería de Bluetooth de la ESP32.

![Foto1](../imagenes/jiji (1).png){loading=lazy}
![Foto1](../imagenes/jiji (2).png){loading=lazy}
![Foto1](../imagenes/jiji (3).png){loading=lazy}
---

## 5.  Resultados

Durante la realización de la práctica, el código fue desarrollado y cargado utilizando **Arduino IDE** y al momento de realizar las pruebas de comunicación, no fue posible realizarlas directamente con el Monitor Serial de la computadora, por lo cual se tuvo que recurrir al uso de un **teléfono Android**. 

A través del celular, mediante una aplicación de Bluetooth Serial, nos conectamos al ESP32 y enviamos los comandos (`ON` y `OFF`) de manera inalámbrica.

* **Prueba sin delay (`activarDelayLatencia = false`):** Al transmitir los comandos desde la aplicación del celular Android, la respuesta del LED fue inmediata y tan pronto como se enviaba la orden, el pin del ESP32 cambiaba de estado sin ningún retraso perceptible.
* **Prueba con delay (`activarDelayLatencia = true`):** Al activar la función `delay(1000)` en el programa, la recepción de los comandos enviados desde el celular presentó un desfase. 

![video](../imagenes/blutuvi.mp4){loading=lazy}

---

## 6. Conclusiones

En esta práctica aprendimos exitosamente cómo configurar y utilizar las funciones de comunicación Bluetooth del ESP32 dentro de Arduino. Comprendimos el funcionamiento de este tipo de códigos para recibir datos de forma inalámbrica, así como la manera correcta de procesar cadenas de texto para controlar pines de salida y responder a comandos desde un dispositivo móvil.