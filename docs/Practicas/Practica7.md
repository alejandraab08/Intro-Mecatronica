# Práctica de Laboratorio: Control en Lazo Abierto y Lazo Cerrado

**Asignatura:** Introducción a la Mecatrónica  
**Institución:** Universidad Iberoamericana Puebla  

---

## 💡 Conceptos Clave 
Para entender mejor esta práctica, definimos los términos principales en palabras sencillas:

* **Lazo Abierto:** Es cuando le das una orden a una máquina y la ejecuta a ciegas, sin revisar si lo hizo bien o si algo la desvió en el camino.
* **Lazo Cerrado:** Es cuando la máquina tiene un 
sensor que revisa todo el tiempo lo que está haciendo para corregirse sola si se equivoca.
* **PWM :** Es la forma en que le enviamos fuerza o velocidad constante al motor.
* **$Kp$:** La fuerza con la que el sistema reacciona para corregir un error. Si es muy alta, el carrito avanza rápido pero puede pasarse de largo.
* **$Kd$:** Funciona como un freno inteligente. Ayuda a frenar antes de llegar a la meta para no pasarse.
* **$Ki$:** Es la memoria del sistema. Suma los errores que quedaron pendientes al final y empuja un poquito más hasta dejarlo exactamente en la meta.
* **Sobreimpulso:** Qué tanto se pasa el sistema de la meta esperada antes de regresar y detenerse (medido en porcentaje).
* **Tiempo de Establecimiento:** El tiempo total (en segundos) que tarda el sistema en quedarse estable cerca de la meta.
* **Error Permanente:** La diferencia o distancia final que faltó para llegar a la meta deseada.

---

## 1. Objetivos de la Práctica

* **Parte A (Lazo Abierto):** Probar el carrito físico programando movimientos por tiempo (sin sensores que lo corrijan) para ver cuánto se desvía cuando cambia el tipo de piso o cuando le agregamos peso.
* **Parte B (Lazo Cerrado):** Usar el simulador para ajustar las ganancias ($Kp$, $Kd$, $Ki$) paso a paso, logrando que la respuesta sea rápida, no se pase de la meta y no tenga error final.

---

## 2. Parte A · Lazo Abierto (Pruebas Físicas con el Carro)

En esta parte se programó una secuencia fija en el carrito (avanzar 2 segundos, girar 1 segundo y avanzar 2 segundos) manteniendo la misma fuerza en los motores (PWM fijo).

### Tabla de Desviaciones (Mediciones Físicas)

| Condición del Piso / Carga | Intento | Desviación del punto final (cm) | Observaciones simples |
| :--- | :---: | :---: | :--- |
| **Piso de referencia** (Superficie lisa / Sin carga) | 1 | 1.5 cm | Movimiento bastante recto, solo se desvió un poco a la izquierda por pequeña diferencia entre motores. |
| **Piso de referencia** (Superficie lisa / Sin carga) | 2 | 1.8 cm | Repitió casi la misma trayectoria; la mayor parte de la desviación ocurrió al momento de girar. |
| **Otro piso o con carga** (Superficie rugosa o con peso) | 1 | 5.2 cm | Al haber más fricción, los motores batallaron más y el carro avanzó menos distancia en los 2 segundos. |
| **Otro piso o con carga** (Superficie rugosa o con peso) | 2 | 6.0 cm | El peso extra hizo que el carrito se desviara mucho más de la meta que teníamos planeada. |

---

[Ver el video de las pruebas físicas en YouTube](https://www.youtube.com/watch?v=cbQn0WWi4As&t=56s)

---

## 3. Parte B · Lazo Cerrado (Simulación en la Demo)

Siguiendo la receta recomendada, ajustamos las ganancias en este orden estricto: **primero $Kp$, después $Kd$ y al final $Ki$**.

### Tabla de Sintonización (Simulador)

| Intento | $Kp$ | $Ki$ | $Kd$ | Sobreimpulso (%) | Tiempo de establecimiento (s) | Error permanente | Explicación sencilla de lo que pasó |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :--- |
| **1** | 2.0 | 0.0 | 0.5 | 12.5% | 4.2 s | 0.2 | El sistema respondió rápido pero se pasó de la meta un $12.5\%$ antes de regresar. |
| **2** | 1.5 | 0.1 | 1.2 | 3.1% | 2.8 s | 0.0 | Al aumentar $Kd$ frenó a tiempo (solo $3.1\%$ de sobreimpulso) y $Ki$ eliminó el error final. |

---
![Foto1](../imagenes/wow (1).png){loading=lazy}
![Foto1](../imagenes/wow (2).png){loading=lazy}
---

## 4. Reto Extra y Elección de Parámetros Finales

* **Requisito solicitado:** Sobreimpulso menor a $5\%$ y tiempo de establecimiento menor a $5\text{ segundos}$.
* **Valores finales elegidos:** $Kp = 1.5$, $Ki = 0.1$, $Kd = 1.2$.
* **Resultados logrados:**
  * **Sobreimpulso:** $3.1\%$ *(Cumple al ser menor que $5\%$)*.
  * **Tiempo de establecimiento:** $2.8\text{ s}$ *(Cumple al ser menor que $5\text{ s}$)*.
  * **Error permanente:** $0.0$ *(Quedó exactamente en la meta)*.

### Justificación 
Elegimos esta combinación porque los tres componentes se ayudan entre sí:
1. Con $Kp = 1.5$ logramos que el sistema arranque con buena velocidad hacia la meta.
2. Agregando $Kd = 1.2$, el sistema detecta qué tan rápido se acerca y aplica un "frenado inteligente", evitando que se pase de largo y bajando la sobreoscilación a solo $3.1\%$.
3. Finalmente, $Ki = 0.1$ le da un último empujoncito al final para corregir cualquier desfase, garantizando que el error permanente siempre sea lo más cercano a cero ($0.0$).

---

## 5. Conclusiones

1. **Lazo Abierto (Carro Físico):** Comprobamos que trabajar a ciegas (por puros tiempos) no funciona bien en el mundo real. Cuando cambiamos el tipo de piso o pusimos peso sobre el carrito, la desviación del punto final aumentó hasta 3 veces más ($6.0\text{ cm}$). Esto pasa porque el carro no tiene forma de saber que se está desviando para corregirse.
2. **Lazo Cerrado (Simulador):** La retroalimentación constante permite que el sistema mida su error en cada instante y se corrija solo. La receta de sintonización ($P \rightarrow D \rightarrow I$) nos enseñó cómo balancear la velocidad de llegada, evitar golpes o pasadas de largo y asegurar que llegue exactamente al lugar deseado.