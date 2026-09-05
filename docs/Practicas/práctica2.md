# Práctica Integral: Entradas y Salidas Digitales (ESP32)

> **Asignatura:** Introducción a Mecatrónica  
> **Hardware ocupado:** ESP32, protoboard, jumpers, LED, botón.
> **Software ocupado:** Arduino IDE (código), WOKWI (esquemáticos) 

---

## 🎯 Objetivo General

Implementar el control de entradas y salidas digitales en un microcontrolador abarcando 4 mini prácticas: parpadeo básico (*Blink*) a 1 Hz sin funciones bloqueantes (`delay()`), control directo de salida por botón mediante `INPUT_PULLUP`, alternancia de estados (*Toggle*) con filtro de antirrebote (*Debounce*) y un contador de presiones comparando lecturas ruidosas vs. filtradas.

---

## 📋 Lista de Entregables

- [x] **Práctica BLINK Salida Digital:** LED externo parpadeando a 1 Hz.
- [x] **Práctica 2 BLINK con Botón:** Encendido del LED únicamente mientras el botón permanece presionado (`INPUT_PULLUP`).
- [x] **Práctica 3 TOGGLE con Antirrebote:** Alternancia de estado del LED con cada pulsación del botón sin el uso de `delay()`.
- [x] **Práctica 4 EXTRA Contador:** Contador en monitor serie comparando presiones con y sin código antirrebote.
- [x] **Bitácora de errores:** Análisis de problemas observados y soluciones aplicadas.
- [x] **Mini-Video y fotos** Evidencia de la práctica 
- [x] **Conclusión:** Resumen de la práctica.

---

## 1. 📐 Fundamento Teórico

1. **Configuración `INPUT_PULLUP`:**  
   Al activar la resistencia de *Pull-Up* interna del microcontrolador en el pin de entrada, el estado lógico en reposo es **ALTO (`HIGH` / 3.3V)**. Cuando se presiona el botón, el pin se conecta directamente a masa (**GND**), cambiando su estado a **BAJO (`LOW` / 0V)**.

2. **Fenómeno del Rebote Mecánico (*Bounce*):**  
   Al accionar nuestro botón, las láminas metálicas internas rebotan entre sí a nivel microscópico durante unos milisegundos. Como la velocidad de procesamiento del microcontrolador es muy alta, este interpreta los rebotes como múltiples pulsaciones individuales.

3. **Temporización No Bloqueante con `millis()`:**  
   A diferencia de `delay()`, que detiene por completo la ejecución del procesador, la función `millis()` devuelve el tiempo transcurrido desde que se encendió la tarjeta, permitiendo ejecutar el antirrebote y el parpadeo en segundo plano sin interrumpir la ejecución del código.


## 3. 🧪 Desarrollo de las 4 Prácticas

### BLINK (Salida Digital a 1 Hz)

 * **Descripción:** Esta práctica se enfoca en el control temporal básico de una **salida digital pura**. A diferencia del parpadeo tradicional con `delay()`, aquí el microcontrolador evalúa constantemente el tiempo transcurrido mediante `millis()`, lo que permite alternar el estado del LED exactamente cada 500 ms (frecuencia de 1 Hz) sin congelar la ejecución de otras instrucciones del sistema.

### BLINK con Botón (Entrada Digital Directa)

 * **Descripción:** A diferencia de la primera práctica, aquí se introduce el uso de una **entrada digital reactiva**. Se aprovecha la resistencia interna de la placa ESP32(`INPUT_PULLUP`), lo que elimina la necesidad de colocar resistencias físicas externas. El LED enciende en tiempo real únicamente mientras el botón permanece presionado (lectura `LOW`), demostrando la respuesta directa de una salida (LED) ante el estado instantáneo de una entrada (botón).

### Mini Práctica 3: TOGGLE con Antirrebote (Memoria de Estado)

 * **Descripción:** Mientras que la Práctica 2 requiere mantener presionado el botón para activar la salida, esta mini práctica implementa la **alternancia de estado (*Toggle*)**. Cada pulsación del botón invierte el estado del LED (de encendido a apagado o viceversa). Además, incorpora un filtro por software de 30 ms con `millis()` para prevenir que las vibraciones mecánicas del botón generen falsos cambios de estado al presionar.

### Mini Práctica 4 (EXTRA): Contador de Presiones Con vs. Sin Antirrebote

 * **Descripción:** Esta prueba fue diseñada para **evidenciar cuantitativamente el efecto del ruido mecánico (rebotes)** mediante el monitor serie. Mientras que la Práctica 3 aplica el filtro de forma transparente para prender y apagar un LED, esta mini práctica registra y cuenta cada pulso recibido al presionar el botón, comparando de forma directa la imprecisión del conteo directo contra la precisión del conteo filtrado.

| Modo de Lectura | Presiones Reales | Conteos Registrados | Error por Rebote |
| :--- | :---: | :---: | :--- |
| **Sin Antirrebote** | 10 | 16 | Presencia de múltiples falsos positivos por ruido mecánico |
| **Con Antirrebote (30 ms)** | 10 | 10 | **0% de error** (Lectura limpia y precisa) |

---

## 4. 🛠️ Bitácora de Errores

* **¿Qué falló?:**  
  En la Mini Práctica 4 (modo sin antirrebote), al presionar el botón una sola vez, la consola sumaba entre 2 y 4 conteos de golpe.

* **¿Cómo lo encontramos?:**  
  Al realizar la prueba de las 10 presiones observando la consola serie a 115200 bauds, notamos que los conteos incrementaban en ráfagas de microsegundos en lugar de sumar uno a uno por cada clic.

* **¿Cómo lo resolvimos?:**  
  Se implementó una ventana de tiempo de 30 ms utilizando la variable `ultimoTiempoRebote` con `millis()`. Con esto, cualquier cambio de voltaje ocurrido dentro de esa ventana fue ignorado hasta que la señal se stabilized.

---

## 5. Mini-Video y fotos
![Fotos](../imagenes/fotoa.jpeg){loading=lazy}
![Fotos](../imagenes/fotob.jpeg){loading=lazy}
![Fotos](../imagenes/fotoc.jpeg){loading=lazy}
![Fotos](../imagenes/fotod.jpeg){loading=lazy}
![Fotos](../imagenes/fotoe.jpeg){loading=lazy}
![Fotos](../imagenes/fotof.jpeg){loading=lazy}
<video width="320" height="240" controls>
  <source src="video1.mp4" type="video/mp4">
</video>
 <video width="320" height="240" controls>
  <source src="video2.mp4" type="video/mp4">
</video>
<video width="320" height="240" controls>
  <source src="video3.mp4" type="video/mp4">
</video>

---

## 6. 📝 Conclusión

Mediante esta práctica se logró dominar la gestión de entradas y salidas digitales en microcontroladores. Se demostró la utilidad de la configuración `INPUT_PULLUP` para simplificar circuitos físicos y la importancia del uso de `millis()` para evitar bloquear el procesador. Finalmente, la comparativa del contador evidenció la necesidad del filtro de antirrebote por software para eliminar el ruido mecánico y garantizar lecturas 100% confiables en cualquier proyecto de electrónica.