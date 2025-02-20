# Eddies-NeurOST

# 🌊 **Detección de Remolinos en el Golfo de California con NeurOST y Deep Learning**

Este repositorio contiene el código, documentación y modelos desarrollados para la **detección de remolinos en el Golfo de California** utilizando datos satelitales del producto **NeurOST** y métodos de detección basados en **procesos físicos y aprendizaje profundo**.

---

## 📌 **Contenido del Repositorio**
- 📄 `notebooks/` → Notebooks de Jupyter con experimentos y análisis.
- 📂 `data/` → Datos del producto **NeurOST** utilizados en el estudio.
- 📝 `docs/` → Documentación sobre la metodología y referencias científicas.
- 📜 `models/` → Pesos y arquitecturas de los modelos entrenados.
- 🏷️ `README.md` → Información sobre el proyecto.

---

## 🛰 **Datos Utilizados: Producto NeurOST**
Los datos utilizados en este estudio provienen del **producto NeurOST**, que proporciona información de alta resolución espacial y temporal sobre la altura del nivel del mar (**SSH**) proveniente de SST y SSH DUACS (Martin et al., 2024). Se trabaja con resolución de **1 km diario**, lo que permite analizar la variabilidad de los remolinos a mesoescala.

🔹 **Variables Principales:**
- **SLA** (Sea Level Anomaly) – Anomalía del nivel del mar.
- **ADT** (Absolute Dynamic Topography) – Topografía dinámica absoluta.
- **Corrientes geostróficas** – Calculadas a partir de SLA y ADT.
- **Gradientes de vorticidad** – Para estimar estructuras de remolinos.

Estos datos han sido preprocesados y enmascarados para **eliminar regiones de NaNs**, evitando interferencias en los modelos.

---

## 📊 **Metodologías Utilizadas**
Este proyecto emplea una combinación de **métodos físicos clásicos** y **modelos de Deep Learning** para la detección y caracterización de remolinos oceánicos.

### **1️⃣ Métodos Basados en Física**
Se implementaron tres métodos tradicionales ampliamente utilizados en la literatura:

- **Método de contornos cerrados de SLA (CHE11)**: Detección de remolinos basada en la identificación de contornos cerrados en la anomalía del nivel del mar (**SLA**), siguiendo la metodología propuesta por Chelton et al. (2011).
  
- **Método de geometría de velocidades (NEN10)**: Utiliza la disposición de los vectores de velocidad geostrófica para inferir la existencia de estructuras coherentes de remolinos, basado en Nencioli et al. (2010).

- **Método combinado de Okubo-Weiss y contornos cerrados (HAL13)**: Un enfoque híbrido propuesto por Halo et al. (2013), que evalúa la vorticidad relativa y la deformación del flujo para identificar remolinos.

### **2️⃣ Métodos Basados en Deep Learning**
Además de los métodos físicos, se implementaron modelos de **redes neuronales convolucionales** para mejorar la precisión en la detección de remolinos:

- **U-Net estándar**: Implementación clásica para la segmentación de remolinos basada en datos de SLA y ADT.
- **ADUNet (Attention Dual U-Net)**: Versión mejorada de U-Net con módulos de atención para captar mejor los patrones de los remolinos.
- **3D-U-Res-Net**: Modelo que incorpora estructuras tridimensionales para analizar la evolución vertical de los remolinos.
- **EddyNet**: Modelo específico para la segmentación de remolinos en mapas altimétricos.

Estos modelos fueron entrenados con **895 datos etiquetados** y optimizados para evitar la interpolación en regiones sin datos válidos.


