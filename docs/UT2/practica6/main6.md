---
title: Feature Scaling y Anti-Leakage Pipeline — Escalado ético, reproducible y sin fuga de información
date: 2025-09-17
---

# Contexto y Alcance

El dataset **Ames Housing (Iowa)** contiene más de 80 variables que describen propiedades inmobiliarias (dimensiones, materiales, calidad, ubicación y precio).  
La heterogeneidad en magnitudes —metros cuadrados, años, calidades ordinales, precios— lo convierte en un escenario ideal para estudiar **desbalance de escalas**, **sesgos fuertes**, **outliers estructurales** y riesgos de **data leakage**.

Esta práctica desarrolla un workflow completo para **escalar variables de forma ética, reproducible y libre de fuga de información**, comparando métodos clásicos (Standard, MinMax, Robust) y evaluando sus efectos en la distribución y estabilidad del dataset.

---

# Objetivos

- Diagnosticar variables con escalas y rangos desbalanceados.  
- Comparar `StandardScaler`, `MinMaxScaler` y `RobustScaler`.  
- Evaluar el impacto del `log1p` en variables con fuerte asimetría.  
- Implementar un **pipeline anti-leakage** (fit solo en TRAIN).  
- Analizar implicancias técnicas y éticas del preprocesamiento.

---

# Desarrollo

El análisis se organizó en seis etapas, siguiendo una adaptación ética de CRISP-DM.

---

## 1. Exploración inicial de escalas

Se identificó que las variables:

- **LotArea**  
- **GrLivArea**  
- **TotalBsmtSF**  
- **SalePrice**

presentaban **rangos amplísimos y skew pronunciado**, afectando modelos basados en distancia o gradiente.

---

## 2. Selección de variables relevantes

Se trabajó con:

- `SalePrice`  
- `LotArea`  
- `GrLivArea`  
- `TotalBsmtSF`  
- `GarageArea`  
- `YearBuilt`

Estas concentran la mayor parte de la variabilidad del dataset y son críticas para la predicción.

---

## 3. Transformación logarítmica (log1p)

Aplicada a variables con *skewness* > 1:

- `LotArea`  
- `GrLivArea`  
- `SalePrice`  

**Justificación técnica:** reduce el impacto de valores extremos sin eliminarlos.  
**Justificación ética:** los outliers estructurales representan viviendas reales; removerlos sería falsificar el dataset.

---

## 4. Comparación de métodos de escalado

### **StandardScaler**
- Media 0, varianza 1.  
- Sensible a outliers.

### **MinMaxScaler**
- Rango [0,1].  
- No corrige skew.  
- Altamente sensible a extremos.

### **RobustScaler**
- Centrado en mediana y IQR.  
- Mejor manejo de outliers estructurales.  

**Conclusión:**  
➡ **RobustScaler** produjo la distribución más estable y representativa para Ames Housing.

---

## 5. Pipeline Anti-Leakage

**Regla fundamental:** *primero se separa el dataset; luego se procesan las transformaciones*.

1. `X_train, X_valid, X_test`  
2. `scaler.fit(X_train)`  
3. `scaler.transform(X_valid)`  
4. `scaler.transform(X_test)`

**Motivación ética y técnica:**  
Evita que el modelo incorpore información del futuro, garantizando métricas honestas y reproducibles.

---

# Evidencias

Todas las visualizaciones se generaron en Colab y se incluyen aquí con sus rutas oficiales del repo.

---

### 📊 Distribución de variables numéricas (escala logarítmica)
![Distribución de variables numéricas](Distribuciones_totales.png)

---

### 📊 Ratios max/min por variable
![Ratios max/min por variable](Comparacion_ratios.png)

---

### 📊 Distribuciones individuales de variables sesgadas
![Distribuciones individuales](Distribuciones_individuales.png)

---

### 📊 Escalas en TRAIN (anti-leakage)
![Escalas en TRAIN](Escalas.png)

---

### 📊 Distribuciones antes y después del escalado
![Distribuciones antes y después del escalado](Distribucion.png)

---

### 📊 Efecto del Log Transform
![Efecto del Log Transform](Distribucion.png)

---

### 📊 Correlación original vs escalada
![Correlación original](Correlacion_original.png)  
![Correlación después del escalado](Correlacion_despues.png)

---

### 📊 Relación entre área y precio, antes y después del log
![Relación entre área y precio](Relacion.png)

---

### 📊 Comparación final de métodos de escalado
![Comparación de métodos de escalado](Comparacion_escalado.png)

---

# Insights clave

- `LotArea` y `GrLivArea` son las principales fuentes de distorsión numérica.  
- `RobustScaler` ofrece la mejor estabilidad frente a outliers.  
- El orden **Log → Scale** reduce skew y mejora la normalidad.  
- El pipeline anti-leakage evita métricas infladas y favorece generalización real.  
- Las métricas “más bajas” son en realidad métricas **más honestas**.

---

# Reflexión

El preprocesamiento no es un paso mecánico: es una **decisión analítica y ética**.  
Un mal escalado puede amplificar outliers, ocultar patrones reales o, peor aún, introducir *leakage* que invalida cualquier conclusión del modelo.

Un pipeline anti-leakage, reproducible y documentado, asegura que las métricas reflejen fidelidad con el proceso y transparencia profesional.

> **El rigor técnico sin ética es solo automatización del error.**

---

# Notebook en Google Colab

📓El notebook completo con el desarrollo de esta práctica puede consultarse en el siguiente enlace:

🔗 [**Abrir en Google Colab**] (https://colab.research.google.com/github/Agustina-Esquibel/Ingenieria-datos/blob/main/docs/UT2/practica6/UT2_practica6.ipynb)

---

# Referencias

- Kaggle: *Ames Housing Dataset*  
- Scikit-learn: *Preprocessing, Pipelines & Model Evaluation*  
- Pandas & Seaborn Documentation  
- Kurucz, J.F. (2025). *Feature Scaling & Anti-Leakage Pipeline — UCU Ingeniería de Datos*

---

# Navegación

[⬅️ Volver a UT2](../main.md)  
[➡️ Ir a Práctica 7 — Fairness y Decisiones Éticas](../practica7/main7.md)  
[📓 Índice del Portafolio](../../portfolio/index.md)
