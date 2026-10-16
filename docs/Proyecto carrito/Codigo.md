# Práctica 3: Código de Control por Bluetooth y PWM para Carrito Futbolista (ESP32)

> **Asignatura:** Introducción a Mecatrónica  

---

## 🎯 Objetivo General

Implementar el firmware de control en un microcontrolador ESP32 para gestionar la comunicación inalámbrica por Bluetooth (BLE) con un control de Xbox, aplicando rampas de aceleración, modulación por ancho de pulso (PWM) y control de estados no bloqueantes para el mecanismo de tiro mediante un servomotor.

---

## 📋 Lista de Entregables

- [x] **1. Conexión Inalámbrica BLE:** Vinculación del ESP32 con el control de Xbox mediante el protocolo Bluetooth Low Energy.
- [x] **2. Algoritmo de Control Diferencial (Arcade):** Mapeo de las coordenadas de la palanca analógica para el movimiento vectorial de tracción en dos motores.
- [x] **3. Control de Velocidad con Rampas y Niveles:** Programación de perfiles de velocidad variable, modo turbo y aceleración gradual para proteger el sistema mecánico.
- [x] **4. Automatización del Mecanismo de Disparo:** Rutina de estados no bloqueante para el control temporal del servomotor de pateo.
- [x] **Evidencia Multimedia:** Capturas del código fuente compilado y diagrama lógico de flujo de datos.
- [x] **Conclusión:** Resumen de la lógica de programación implementada.

---

## 1. 📐 Fundamento Teórico

1. **Comunicación Inalámbrica BLE (*Bluetooth Low Energy*):**  
   El ESP32 integra conectividad inalámbrica de doble modo (Bluetooth clásico y BLE). Mediante la librería especializada, el microcontrolador actúa como cliente BLE para escuchar y extraer las tramas de datos enviadas por periféricos de mando estándar (como el control de Xbox), leyendo en tiempo real los ejes de las palancas y los estados de los botones.

2. **Control de Tracción Diferencial (Tipo Arcade):**  
   Para dirigir un vehículo de tracción diferencial con dos motores independientes, las coordenadas cartesianas de la palanca analógica ($X, Y$) se combinan matemáticamente. El eje $Y$ determina la velocidad de avance/retroceso, mientras que el eje $X$ introduce la diferencia de velocidad entre la rueda izquierda y la derecha para lograr giros sobre su propio eje o curvas progresivas.

3. **Control de Aceleración por Rampas (*Ramping*):**  
   Cambiar bruscamente la velocidad de un motor de 0 a un valor máximo genera picos de corriente destructivos y desgaste mecánico prematuro. El uso de una función de rampa incrementa el valor del PWM de forma gradual en cada ciclo de tiempo preestablecido, logrando un arranque suave y estable.

4. **Gestión de Estados No Bloqueantes:**  
   Para evitar el uso de la función de pausa total (`delay()`), que congelaría la lectura del control inalámbrico, se implementa una máquina de estados basada en el tiempo transcurrido (`millis()`). Esto permite coordinar la extensión, el golpe y la recarga del servomotor de tiro de manera independiente y fluida sin interrumpir el control del carrito.

---

## 2. 🛠️ Elementos del Software

- **Arduino IDE:** Entorno de desarrollo para compilar y cargar el código en el ESP32.
- **Librería ESP32Servo:** Control de la señal PWM dedicada al posicionamiento del servomotor SG90.
- **Librería BLEGamepadClient:** Interfaz de comunicación para la vinculación con el mando de Xbox.
- **Estructuras de Control Condicional y Temporización:** Gestión de ciclos de control estables a 10 ms (`PERIODO_CONTROL`).

---

## 3. 🧪 Desarrollo del Código y Explicación

### Parte 1: Inicialización y Configuración de Pines (`setup`)
- **Descripción:** Se configuran los canales de comunicación serial para depuración (`Serial.begin(115200)`), se asocian los pines del driver TB6612FNG como salidas digitales, y se configuran las frecuencias de PWM a 20 kHz mediante la API de LEDC del ESP32 para evitar zumbidos audibles en los motores. Finalmente, se inicializa el cliente BLE para buscar el control de Xbox.

### Parte 2: Lectura Inalámbrica y Mapeo de Movimiento (`loop`)
- **Descripción:** En cada iteración del bucle principal, el ESP32 verifica si el control se encuentra vinculado. Si está conectado, lee el estado de la palanca izquierda (`s.leftStickX`, `s.leftStickY`). Mediante la función `calcularObjetivo()`, se procesa una **zona muerta** (`ZONA_MUERTA = 0.12`) para evitar movimientos parásitos causados por el ruido eléctrico del potenciómetro del mando, traduciendo la posición en velocidades independientes para ambos motores.

### Parte 3: Sistema de Velocidades, Turbo y Rampas de Aceleración
- **Descripción:** El usuario puede alternar entre tres niveles de velocidad preconfigurados usando los botones superiores (`LB` y `RB`), o activar la potencia máxima manteniendo presionado el gatillo izquierdo (`LT`) para el modo **Turbo**. Para proteger el hardware, la función `rampa()` limita el incremento máximo de velocidad por ciclo (`PASO_ACEL`), suavizando tanto la aceleración como los cambios de sentido.

### Parte 4: Automatización del Mecanismo de Disparo
- **Descripción:** Al presionar el botón `A` o el gatillo derecho (`RT`), se ejecuta la función `iniciarTiro()`, la cual mueve el servomotor de la posición de reposo ($0^\circ$) a la posición de golpe ($90^\circ$). Un sistema de temporización basado en `millis()` mantiene el brazo extendido durante 120 ms (`TIEMPO_GOLPE`) antes de regresarlo automáticamente y bloquear nuevos disparos durante el tiempo de recarga.

---

## 📝 Conclusiones

- El uso del ESP32 permitió integrar de forma eficiente la conectividad inalámbrica BLE con un control comercial de Xbox, facilitando el manejo ergonómico del carrito futbolista.
- La implementación de rampas de aceleración por software y una frecuencia de PWM de 20 kHz optimizó el rendimiento eléctrico de los motores, evitando tirones mecánicos bruscos y sobrecalentamientos.
- El diseño de una máquina de estados no bloqueante garantizó que el sistema de disparo con servomotor operara en segundo plano de manera simultánea al control de tracción, logrando una respuesta rápida y fluida del robot en la cancha.