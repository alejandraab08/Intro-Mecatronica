# Práctica EXTRA: Generación de Pulso Fijo (555 Monoestable)

## 📋 Lista de Entregables

- [x] **Fotos del montaje:** Evidencia fotográfica de la implementación en protoboard.
- [x] **Tabla de medición vs. teoría:** Completada con % de error e interpretaciones.
- [x] **Mini-video ($\le 60\text{ s}$):** Grabación mostrando la onda en el osciloscopio y el comportamiento del LED con voz en off.
- [x] **Bitácora de errores:** Sección 4 del presente reporte.

---

## 1. 📐 Fundamento Teórico

En la configuración **monoestable**, el temporizador 555 genera un único pulso de salida de duración fija ($T$) cuando recibe un pulso de disparo negativo **(Trigger)**.

La duración del pulso depende exclusivamente del tiempo de carga del capacitor $C$ a través de la resistencia $R_A$:

$$T = 1.1 \cdot R_A \cdot C$$

---

### 2 Montaje en Protoboard
![Protoboard](../imagenes/fotomono.jpeg){loading=lazy}

---

## 3. 📊 Tabla de Medición vs. Teoría

| Parámetro | Valor Teórico | Valor Medido | Error Relativo (%) |
| :--- | :---: | :---: | :---: |
| **Tiempo de Pulso ($T$)** | $5.164\text{ s}$ | $5.400\text{ s}$ | $4.57\%$ |

*Fórmula de Porcentaje de Error:*

$$\% \text{ Error} = \left| \frac{\text{Valor Medido} - \text{Valor Teórico}}{\text{Valor Teórico}} \right| \times 100$$

$$\% \text{ Error} = \left| \frac{5.400 - 5.164}{5.164} \right| \times 100 \approx 4.57\%$$

### Explicación de las Diferencias (Margen de Error)
* **Precisión en la toma del tiempo:** La medición del tiempo real se realizó con un cronómetro y también analizando el video grabado de la práctica, por lo que no es $100\%$ precisa.
* **Error humano (error de dedo):** Al medir manualmente el tiempo desde el video (iniciar y detener el cronómetro), existe un margen de imprecisión atribuible al tiempo de reacción o "error de dedo" al hacer clic.
* **Tolerancia de componentes:** Las variaciones naturales en los valores reales de la resistencia y del capacitor respecto a sus valores nominales también influyen en la pequeña diferencia observada.

---
## 4. 🛠️ Bitácora de Errores

* **¿Qué falló?:**  
  Al presionar el botón de disparo al principio, el LED/pulso en la salida se apagaba de forma casi inmediata, lo cual no nos dejaba observar el retardo deseado. Esto ocurrió porque inicialmente utilizamos una resistencia muy baja ($R_A = 1\text{ k}\Omega$), produciendo un pulso extremadamente corto e imperceptible:
  
  $$T = 1.1 \cdot (1000\ \Omega) \cdot (10\ \mu\text{F}) \approx 0.011\text{ s} \quad (11\text{ ms, imperceptible visualmente})$$

* **¿Cómo lo encontramos?:**  
  Verificamos las conexiones físicas del circuito con el diagrama e identificamos que la configuración del temporizador estaba bien armada. Al no ver el resultado esperado, consultamos con el profesor (Osorio), quien afortunadamente se encontraba en el salón y nos ayudó observando el circuito. Nos explicó que debíamos aumentar el valor de la resistencia $R_A$ para ampliar la constante de tiempo $RC$.

* **¿Cómo lo resolvimos?:**  
  Sustituimos la resistencia de $1\text{ k}\Omega$ por una de $47\text{ k}\Omega$. Al elevar la resistencia, el tiempo de pulso aumentó a aproximadamente $0.5\text{ s}$, logrando un intervalo claramente visible desde que se soltaba el pulsador hasta que el LED se apagaba.

---
## 5. Video

> **Nota 1:** El primer video es de cuando nuestro circuito seguía "erróneo" (no estaba mal conectado pero el valor de las resistencias hacia que nuestros cambios fueran inmediatos y por lo tanto imposibles de percibir a simple vista).
> **Nota 2:** Mis videos por alguna razón no se reproducen bien, ya hemos intentado arreglar el problema pero persiste.


## 5.1 Explicación Videos

En este video mostramos la implementación del temporizador 555 en modo monoestable, cuya función es generar un pulso de duración fija al recibir un disparo manual.

Al principio probamos con $R_A = 1\text{ k}\Omega$, pero el pulso duraba milisegundos y no se apreciaba. Corregimos aumentando la resistencia a $47\text{ k}\Omega$, lo que hizo visible el retardo.

---
## 6. 📝 Conclusión

En esta práctica se comprobó exitosamente el funcionamiento del temporizador 555 en configuración monoestable para la generación de un pulso de duración fija mediante la activación por un botón. Se evidenció cómo la constante de tiempo dependerá directamente de los valores del circuito $RC$, ya que al corregir el valor de la resistencia de $1\text{ k}\Omega$ a $47\text{ k}\Omega$ el retardo pasó de ser imperceptible a tener un intervalo claramente visible. Asimismo, el porcentaje de error de $4.57\%$ entre el valor teórico ($5.164\text{ s}$) y el medido ($5.4\text{ s}$) demostró ser completamente aceptable, respaldando la utilidad de este circuito en aplicaciones reales de retardos y filtrado antirrebote por hardware.