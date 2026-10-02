# Práctica Integral: Sensores Analógicos y Filtrado de Señales (ESP32)

**Materia:** Introducción a Mecatrónica  
**Hardware ocupado:** ESP32, potenciómetro, sensor ultrasónico, sensor fotosensible, protoboard, jumpers.  
**Software ocupado:** Arduino IDE (código)

---

## 📋 Lista de Entregables
1. **Práctica 1 - Potenciómetro:** Escalado de lectura analógica a porcentaje (0-100%) y ángulo de giro (0-180°).
2. **Práctica 2 - Ultrasónico (Calibración):** Registro de 5 puntos contra regla de referencia y cálculo de error.
4. **Práctica 3- Uso de sensor foto sensible:** Detección de impacto/interrupción lumínica con umbral ajustable.
5. **Bitácora de errores:** Análisis de problemas observados y soluciones aplicadas.
6. **Evidencia:** Mini-video y fotos.
7. **Conclusión:** Resumen de la práctica.

---

## 1. 📐 Fundamento Teórico

### Convertidor Analógico a Digital (ADC) y Escalado:
El ESP32 convierte voltajes analógicos de 0 a 3.3 V en valores numéricos mediante su ADC de 12 bits (0 a 4095). Mediante operaciones matemáticas simples de escalado, estas lecturas se transforman a magnitudes físicas legibles como porcentaje o grados de rotación.

### Calibración por Ajuste Lineal:
Los sensores ultrasónicos suelen presentar desfases causados por variaciones de temperatura o reflexiones del entorno. Comparar la medición cruda contra una referencia patrón (como una regla) permite obtener una ecuación lineal de corrección para reducir considerablemente el error de medición.

### Filtro de Promedio Móvil:
El ruido eléctrico y los ecos erráticos generan picos en las lecturas analógicas e intensidades ultrasónicas. El filtro de promedio móvil suaviza la señal promediando las últimas $N$ muestras almacenadas en un arreglo circular:
* **$N$ pequeño ($N = 3$):** Poca atenuación de ruido, respuesta casi instantánea.
* **$N$ mediano ($N = 10$):** Equilibrio ideal entre suavizado y tiempo de respuesta.
* **$N$ grande ($N = 50$):** Señal sumamente estable pero con retardo visible (latencia).

### Detección por Umbral (Threshold):
Permite identificar eventos repentinos (como una sombra rápida o un impacto sobre el haz de luz) comparando la lectura instantánea o la derivada de la señal filtrada contra un valor límite predeterminado.

---

## 3. 🧪 Desarrollo de las 4 Prácticas

### Mini Práctica 1: Potenciómetro (Lectura, Porcentaje y Ángulo)
**Descripción:** Se realiza la lectura del divisor de voltaje mediante la entrada analógica del ESP32. El valor crudo del ADC (0-4095) se transforma mediante fórmulas de proporción en dos valores útiles: porcentaje de apertura (0 a 100%) y ángulo equivalente de rotación (0 a 180°).
![Foto1](../imagenes/poo (2).jpeg){loading=lazy}

---

### Mini Práctica 2: Sensor Ultrasónico (Calibración y Error)
**Descripción:** Se toman lecturas de distancia contra una regla graduada en 5 puntos de prueba. Se calcula el error en cada punto y se genera una recta de calibración simple para corregir las mediciones en tiempo real.

![Foto1](../imagenes/poo (1).jpeg){loading=lazy}

---

### Mini Práctica 4: Sensor fotosensible (LDR)
**Descripción:** Se utiliza la fotoresistencia (LDR) para monitorear la luz ambiental. Al pasar la mano rápidamente o interrumpir el haz de luz, la caída drástica en el valor analógico supera el umbral configurado por software, activando una alerta visual/serie en el sistema.

![Foto1](../imagenes/poo (3).jpeg){loading=lazy}
---

## 4. 🛠️ Bitácora de Errores

* **¿Qué falló?:**  
  En la Mini Práctica 2, la distancia medida tardaba casi un segundo completo en actualizarse cuando se movía el objeto de forma rápida.
* **¿Cómo lo resolvimos?:**  
  Se determinó que era un exceso de muestras para aplicaciones de movimiento rápido, por lo que se estableció un parámetro idóneo para equilibrar estabilidad de lectura y rapidez de respuesta.


---

## 6. 📝 Conclusión
En esta práctica se comprendió de manera clara el flujo de procesamiento de señales analógicas desde su captación física hasta su acondicionamiento digital. Se aprendió a escalar lecturas de ADC a unidades de uso práctico (porcentaje y grados) y a calibrar sensores mediante referencias para reducir errores de medición.

*Se utilizo ia para darle formato a la practica