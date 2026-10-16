# Práctica 2: Diseño y Fabricación del Chasis (SolidWorks e Impresión 3D)

> **Asignatura:** Introducción a Mecatrónica  
> **Hardware ocupado:** Impresora 3D, filamento PLA, chasis impreso (base y tapa con sistema de embonado).  
> **Software ocupado:** SolidWorks.

---

## 🎯 Objetivo General

Diseñar en un entorno CAD (SolidWorks) y fabricar mediante manufactura aditiva (impresión 3D) la estructura del chasis del carrito, conformada por una base y una tapa que embonan perfectamente para proteger y alojar los componentes electrónicos.

---

## 📋 Lista de Entregables

- [x] **1. Diseño CAD en SolidWorks:** Modelado 3D de la base y la tapa del chasis con tolerancias de ajuste.
- [x] **2. Impresión 3D:** Fabricación física de las piezas en filamento PLA utilizando una impresora 3D.
- [x] **3. Ensamblaje de la Base y Tapa:** Verificación del embonado mecánico entre ambas piezas.
- [x] **Evidencia Multimedia:** Fotografías del diseño en SolidWorks y de las piezas impresas ensambladas.
- [x] **Conclusión:** Resumen del proceso de diseño y manufactura del chasis.

---

## 1. 📐 Fundamento Teórico

1. **Modelado CAD y Diseño Paramétrico (SolidWorks):**  
   El diseño asistido por computadora permite crear modelos tridimensionales con medidas exactas y tolerancias controladas. En la mecatrónica, es fundamental modelar las piezas considerando los espacios para la tornillería, el paso de cables y el alojamiento de los componentes electrónicos.

2. **Manufactura Aditiva (Impresión 3D por FDM):**  
   La tecnología de Modelado por Deposición Fundida (FDM) construye piezas capa por capa utilizando filamento termoplástico (como el PLA). Este método permite fabricar geometrías personalizadas y complejas, como sistemas de encaje, guías y soportes estructurales a bajo costo y con buena rigidez mecánica.

3. **Sistemas de Embonado Mecánico:**  
   Para facilitar el mantenimiento y evitar el uso excesivo de tornillos, se diseñan pestañas de ajuste o canales de acoplamiento (macho-hembra) entre la base y la tapa. Esto asegura que ambas partes cierren a presión de forma firme y limpia.

---

## 2. 🛠️ Elementos de Fabricación

- **SolidWorks:** Software para la creación de las piezas virtuales (Base y Tapa).
- **Impresora 3D:** Equipo de fabricación aditiva.
- **Filamento PLA:** Material termoplástico para la impresión.
- **Componentes estructurales:** Base contenedora y tapa superior con sistema de cierre por embonado.

---

## 3. 🧪 Desarrollo de la Práctica

### Parte 1: Diseño en SolidWorks
- **Descripción:** Se realizaron dos modelos principales en SolidWorks. Primero, se diseñó la **base** del chasis con soportes internos para fijar el ESP32, el puente H y las baterías, además de dejar las ranuras para los motores. Segundo, se diseñó la **tapa** superior del carrito, integrando bordes con tolerancias milimétricas diseñados específicamente para acoplarse a presión con la base mediante un sistema de embonado tipo pestaña-ranura.

### Parte 2: Impresión 3D y pintura
- **Descripción:** Los archivos digitales en formato `.sldprt` se exportaron a `.stl` y se procesaron en el software de laminado (*slicer*). Se configuraron los parámetros de impresión (temperatura de extrusión de 200°C para PLA, altura de capa de 0.2 mm y un porcentaje de relleno en red del 20% para garantizar resistencia sin exceso de peso). Finalmente, se imprimieron físicamente la base y la tapa, verificando que el sistema de embonado diseñado en CAD encajara de manera precisa al unir ambas partes.

Para darle una mejor presentación visual al carrito futbolista, se procedió a pintar la estructura impresa en PLA. Se aplicó una capa de pintura en aerosol de manera uniforme sobre la base y la tapa, y se le dio un diseño del rayo mcqueen.

---
## Fotos
![Foto1](../imagenes/kuchow (1).jpeg){loading=lazy}
![Foto1](../imagenes/kuchow (2).jpeg){loading=lazy}
--- 
## 📝 Conclusiones

- El uso de SolidWorks permitió planificar con exactitud las dimensiones y los sistemas de unión antes de la fabricación, evitando errores costosos en el material.
- La impresión 3D facilitó la creación de un chasis personalizado y ligero, demostrando la eficiencia del sistema de embonado entre la base y la tapa para un montaje rápido y sin complicaciones.