# Práctica 4: Circuito Eléctrico y Conexiones (ESP32)

> **Asignatura:** Introducción a Mecatrónica  

---

## 🎯 Objetivo General

Realizar las conexiones eléctricas del carrito conectando los motores y el servomotor de disparo directamente al ESP32, garantizando una tierra común para todo el sistema.

---

## 📋 Lista de Entregables

- [x] **1. Alimentación y Tierra Común:** Conexión de la batería y unión de tierras (GND).
- [x] **2. Conexión de Motores DC:** Cableado de los motores al driver TB6612FNG y al ESP32.
- [x] **3. Conexión del Servomotor:** Conexión del SG90 para el mecanismo de tiro.
- [x] **Evidencia Multimedia:** Fotografías del circuito ensamblado.
- [x] **Conclusión:** Resumen de la integración del circuito.

---

## 1. 📐 Fundamento Teórico

1. **Driver TB6612FNG:** Actúa como puente entre el ESP32 y los motores DC. Recibe las señales del microcontrolador y entrega la corriente necesaria desde la batería para mover las ruedas.
2. **GND Unificado:** Es obligatorio unir la tierra de la batería con la tierra del ESP32 para que compartan la misma referencia de voltaje y los motores reciban las órdenes correctamente.

---

## 2. 🔌 Explicación General de Conexiones

### 1. Alimentación y Tierra
- **Batería externa:** Alimenta la potencia del driver (`VMot`) para los motores DC.
- **Tierra Común (GND):** Se unió el `GND` de la batería con el `GND` del ESP32 y del driver.

### 2. Conexión de los Motores DC (Tracción)
- **Motores a Salidas:** El motor izquierdo se conectó a `OUT1 / OUT2` y el derecho a `OUT3 / OUT4` del driver TB6612FNG.
- **Driver al ESP32:**
  - **Motor A (Izquierdo):** `PWMA` (Velocidad, GPIO 14), `AIN1` y `AIN2` (Dirección, GPIO 27 y 26).
  - **Motor B (Derecho):** `PWMB` (Velocidad, GPIO 32), `BIN1` y `BIN2` (Dirección, GPIO 25 y 33).
  - **Standby (`STBY`):** Conectado a 3.3V del ESP32 para mantener encendido el driver.

### 3. Conexión del Servomotor SG90 (Pateador)
- **Alimentación (Rojo / Café):** Cable positivo a VCC y negativo a `GND` común.
- **Señal (Naranja):** Conectado al **GPIO 13** del ESP32 para recibir la señal de control PWM que activa el pateo.

---

## 📝 Conclusiones

- La separación de la alimentación de potencia de la lógica protegió al ESP32 de reinicios.
- La unión de tierras (GND) permitió una comunicación limpia entre el ESP32, el driver y el servomotor.