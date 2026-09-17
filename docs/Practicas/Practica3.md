# Práctica 3: Motor DC, Puente H & Servomotor (ESP32)

> **Asignatura:** Introducción a Mecatrónica  
> **Hardware ocupado:** ESP32 DevKit V1, Puente, Motor DC, Servomotor, Generador, Protoboard y jumpers.  
> **Software ocupado:** Tinkercad

---

## 🎯 Objetivo General

Implementar el control de actuadores mecatrónicos mediante un microcontrolador ESP32, abarcando el control de sentido de giro y velocidad mediante modulación por ancho de pulso (PWM) en un motor DC, la medición de consumo de corriente en régimen transitorio y permanente, y el posicionamiento preciso de un servomotor mediante cálculo de ciclo de trabajo (*duty*).

---

## 📋 Lista de Entregables

- [x] **1. Control del Motor DC (Dirección y PWM):** Inversión de giro y variador de velocidad por PWM con al menos 3 niveles distintos, identificando el punto crítico de PWM mínimo de arranque.
- [x] **2. Prueba de Carga y Medición de Corriente:** Registro experimental con multímetro en serie del pico de corriente de arranque vs. en giro libre.
- [x] **3.  Control Posicional de Servomotor:** Barrido y control angular preciso en 3 posiciones (0°, 90° y 180°) respaldado con la fundamentación matemática del *duty cycle*.
- [x] **Bitácora de errores:** Análisis de fallas que tuvimos  y sus respectivas soluciones.
- [x] **Evidencia Multimedia:** Fotografías de las conexiones y mini-video demostrativo del funcionamiento.
- [x] **Conclusión:** Resumen de la práctica.

---

## 1. 📐 Fundamento Teórico

1. **Etapa de Potencia y Driver TB6612FNG:**  
   Los pines GPIO del ESP32 entregan un máximo de 3.3V y corrientes muy bajas (~12 mA por pin), insuficientes para mover un motor DC directamente. Se utiliza el puente H integrando MOSFETs (TB6612) para conmutar la polaridad aplicada a la carga (dirección mediante lógica de control IN1/IN2) y aislar el circuito lógico de la corriente consumida por la etapa de potencia. Es imperativo mantener una **malla de tierra común (GND unificado)** entre la fuente externa y el ESP32 para fijar la misma referencia de voltaje.

2. **Modulación por Ancho de Pulso (PWM) y PWM Mínimo:**  
   El periférico PWM permite aproximar una señal analógica variando el ciclo de trabajo (*Duty Cycle*) de una señal cuadrada digital de alta frecuencia. En un motor DC, el voltaje promedio aplicado determina el par y la velocidad. Existe un **PWM mínimo de arranque**, que corresponde al ciclo de trabajo mínimo necesario para vencer el par de fricción estática e inductancia propia de los devanados del motor.

3. **Análisis de Consumo Eléctrico (Corriente de Arranque vs. Giro Libre):**  
   Al aplicar voltaje a un motor detenido, la fuerza contraelectromotriz (FCEM) es nula, provocando una demanda de corriente máxima limitada únicamente por la resistencia interna de la bobina. A medida que el rotor acelera, la FCEM aumenta proporcionalmente a la velocidad, reduciendo la corriente efectiva a un valor de régimen permanente (*giro libre*).

4. **Control Posicional del Servomotor (SG90):**  
   Los servomotores utilizan una señal PWM estandarizada a una frecuencia típica de 50 Hz (periodo de 20 ms). La posición angular (0° a 180°) se controla modificando la anchura del pulso activo, que comúnmente varía entre 0.5 ms (0°) y 2.5 ms (180°).

---

## 2. 🔌 Lista de Materiales y Esquema de Conexión

* **ESP32 DevKit V1:** Procesador y generador de señales PWM.
* **Driver TB6612FNG:** Puente H MOSFET de alta eficiencia.
* **Motor DC TT con caja reductora:** Carga inductiva principal.
* **Servomotor SG90:** Actuador posicional de precisión.
* **Potenciómetro 10 kΩ:** Divisor de tensión para entrada analógica.
* **Fuente externa de alimentación (6V - 9V / Pilas):** Alimentación independiente para la etapa de potencia (VMot).
* **Multímetro digital:** Configurado en escala de Amperios DC para medición en serie.

---

## 3. 🧪 Desarrollo de las Prácticas

### Práctica 1: Dirección y Velocidad (Motor DC)

* **Descripción:** Se implementó el control de un motor DC a través del puente H TB6612 accionado por el ESP32. Mediante dos pines digitales (IN1 e IN2) se define el sentido de giro (CW / CCW / Freno). La velocidad se gestiona mediante un pin habilitador (PWM/PWMa) configurado con el periférico `ledc` del ESP32. Se varió el ciclo de trabajo en tres escalones programados (ej. 30%, 65% y 100%). Durante la caracterización inicial, se identificó experimentalmente el **PWM mínimo de arranque** incrementando gradualmente el ciclo de trabajo desde 0 hasta romper la inercia del motor.

### Práctica 2: Prueba de Carga y Medición de Corriente

* **Descripción:** Se interrumpió la línea positiva de la fuente de alimentación externa que alimenta el motor para intercalar las puntas del multímetro configurado en medición de corriente directa. Se registraron dos estados críticos:
  1. **Corriente de arranque (*Inrush/Stall Current*):** Pico instantáneo de corriente demandado en el milisegundo exacto en que el motor pasa del reposo al movimiento.
  2. **Corriente en giro libre (*No-load Current*):** Valor en estado estable mientras el motor gira a máxima velocidad nominal sin carga mecánica en el eje.
* **Comparativa:** La corriente de arranque resultó considerablemente mayor a la corriente de giro libre debido a la ausencia de fuerza contraelectromotriz al inicio del movimiento y al esfuerzo necesario para vencer la inercia y fricción estática del sistema mecánico.

### Práctica 3: Control Posicional de Servomotor

* **Descripción:** Se conectó la línea de señal del servomotor SG90 a un pin GPIO configurado para PWM a 50 Hz. Se programó una rutina de control para llevar el eje de forma secuencial a las posiciones de 0°, 90° y 180°. 
* **Cálculo de *Duty Cycle*:**
  Tomando como referencia un periodo total $T = 20\text{ ms}$ (50 Hz) y una resolución de 16 bits ($2^{16} = 65536$ cuentas):
  * **Posición 0° ($T_{\text{ON}} = 0.5\text{ ms}$):**  
    $$\text{Duty}\% = \left(\frac{0.5\text{ ms}}{20\text{ ms}}\right) \times 100 = 2.5\% \quad \longrightarrow \quad \text{Valor Registros} = 65536 \times 0.025 = 1638\text{ cuentas}$$
  * **Posición 90° ($T_{\text{ON}} = 1.5\text{ ms}$):**  
    $$\text{Duty}\% = \left(\frac{1.5\text{ ms}}{20\text{ ms}}\right) \times 100 = 7.5\% \quad \longrightarrow \quad \text{Valor Registros} = 65536 \times 0.075 = 4915\text{ cuentas}$$
  * **Posición 180° ($T_{\text{ON}} = 2.5\text{ ms}$):**  
    $$\text{Duty}\% = \left(\frac{2.5\text{ ms}}{20\text{ ms}}\right) \times 100 = 12.5\% \quad \longrightarrow \quad \text{Valor Registros} = 65536 \times 0.125 = 8192\text{ cuentas}$$

### EXTRA: Control Analógico Vía ADC

* **Descripción:** Se conectó un potenciómetro de 10 kΩ a una entrada analógica del ESP32 (ADC1). El código toma el valor leído de 12 bits (0 - 4095) y utiliza la función de mapeo proporcional `map()` para escalar dicho rango al rango del PWM (0 - 255 u 0 - 1023 según la resolución configurada). De este modo, la velocidad del motor DC se ajusta de manera fluida y en tiempo real mediante el giro físico de la perilla, reemplazando las velocidades fijas parametrizadas por software.

---

## 🛠️ Bitácora de Errores y Soluciones

| Problema observado | Causa raíz técnica | Solución aplicada |
| :--- | :--- | :--- |
| **El motor hace un zumbido pero no gira en valores bajos de PWM.** | El valor de PWM aplicado genera un voltaje promedio inferior al necesario para vencer el par de fricción estática del motor. | Se determinó la umbral del **PWM mínimo de arranque** y se limitó por software el rango inferior de salida para no operar por debajo de este valor. |
| **Comportamiento errático del servomotor o reinicios del ESP32 (Brownout).** | Se alimentaron los actuadores directamente de los pines del ESP32/USB, generando caídas de voltaje severas por consumo de corriente. | Se separó la alimentación: fuente externa dedicada para motores/servo y **unión estricta de las tierras (GND común)** entre circuitos. |
| **El motor gira en un solo sentido sin responder a las señales.** | Pin de activación/standby (`STBY`) del driver TB6612 flotante o desconectado. | Se conectó el pin `STBY` permanentemente a 3.3V para habilitar los canales lógicos del circuito integrado. |

---

## 📝 Conclusiones

* La utilización de un puente H como el **TB6612** resulta indispensable para desacoplar de forma segura la etapa de control digital del ESP32 de los picos de corriente y el ruido inductivo generados por los motores de corriente directa.
* La caracterización experimental del consumo eléctrico confirmó que la corriente de arranque es significativamente mayor que la de giro libre, un factor crítico que se debe considerar al dimensionar fuentes de alimentación y protecciones térmicas en proyectos mecatrónicos.
* El uso de periféricos PWM en el ESP32 permite una flexibilidad muy alta tanto para el control de velocidad mediante modulación por ancho de pulso como para la generación de pulsos de temporización exacta en servomotores mediante el cálculo preciso del ciclo de trabajo (*duty cycle*).