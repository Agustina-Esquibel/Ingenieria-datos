---
title: Feature Scaling y Anti-Leakage Pipeline — Escalado ético, reproducible y sin fuga de información
date: 2025-09-17
---

## Contexto

El dataset **Ames Housing (Iowa)** incluye más de 80 variables que describen propiedades inmobiliarias (dimensiones, materiales, ubicación y precio).  
Su riqueza y complejidad lo hacen ideal para estudiar los efectos del **escalado de variables**, la **presencia de outliers estructurales** y el **riesgo de data leakage**, un error común que ocurre al transformar datos antes del *split* entre entrenamiento y prueba.

Esta práctica se centra en la **implementación de un pipeline anti-leakage**, comparando distintos métodos de escalado y evaluando cómo las transformaciones afectan la distribución de las variables y la validez del modelo.

---

## Objetivos

- Detectar variables numéricas con escalas desbalanceadas o sesgos extremos.  
- Comparar los métodos `StandardScaler`, `MinMaxScaler` y `RobustScaler`.  
- Evaluar el impacto del *log transform* en variables fuertemente asimétricas.  
- Diseñar un pipeline reproducible que evite *data leakage*.  
- Reflexionar sobre las implicancias éticas y técnicas del preprocesamiento.

---

## Desarrollo

El análisis se organizó en seis etapas principales:

1. **Exploración inicial:** análisis estadístico y visual de las escalas de las variables más relevantes.  
2. **Selección de columnas:** se priorizaron `SalePrice`, `LotArea`, `GrLivArea`, `TotalBsmtSF`, `GarageArea` y `YearBuilt`.  
3. **Transformación logarítmica:** aplicada a columnas con sesgo positivo pronunciado.  
4. **Comparación de métodos de escalado:** `StandardScaler`, `MinMaxScaler` y `RobustScaler`.  
5. **Pipeline anti-leakage:** implementación reproducible y libre de contaminación entre *train* y *test*.  
6. **Evaluación de resultados y documentación:** visualizaciones, métricas y reflexiones críticas.

---

## Evidencias y Resultados

### Distribución de variables numéricas (escala logarítmica)**  

**Observación técnica:**  
El gráfico muestra una diferencia de hasta tres órdenes de magnitud entre `LotArea`, `GrLivArea` y `SalePrice`, con dispersión muy superior al resto.

**Interpretación analítica:**  
Estas variables dominan el rango numérico y pueden “arrastrar” a las demás en algoritmos basados en distancia (KNN, SVM).  
`YearBuilt`, en cambio, mantiene una escala mucho más compacta, sin requerir ajuste.

**Reflexión metodológica:**  
El escalado no es opcional: sin él, las métricas de distancia se vuelven arbitrarias y las correlaciones se distorsionan.

---

### Ratios max/min por variable**  


**Observación técnica:**  
`LotArea` alcanza un ratio de ≈165 y `SalePrice` ≈60. Estas relaciones desbalanceadas confirman la necesidad de normalizar.

**Interpretación analítica:**  
Un rango tan amplio implica que una variación mínima en una variable pequeña podría ser ignorada por completo durante el entrenamiento.  

**Reflexión metodológica:**  
El ratio *max/min* es un indicador simple pero potente de inequidad de escala: si supera 50, el escalado debería ser obligatorio.

---

### Distribuciones individuales de variables sesgadas**  


**Observación técnica:**  
Las variables `LotArea`, `SalePrice` y `GrLivArea` presentan distribuciones con colas largas hacia la derecha (*right-skew*).  

**Interpretación analítica:**  
Estos sesgos indican presencia de valores atípicos, aunque probablemente **estructurales** (casas grandes o lujosas).  

**Reflexión metodológica:**  
Eliminar estos puntos sería una pérdida de información. La solución más ética y técnica es usar un **transformador robusto o logarítmico** para reducir su impacto sin censurarlos.

---

### **Escalas en TRAIN (log-scale)**  

**Observación técnica:**  
El análisis se aplica solo al conjunto de entrenamiento. Las escalas mantienen su coherencia sin incluir datos de validación.

**Interpretación analítica:**  
Esto garantiza que las transformaciones no “vean” datos futuros, preservando la independencia entre *train* y *test*.

**Reflexión metodológica:**  
Separar los conjuntos antes de transformar es esencial para evitar *data leakage*, una práctica éticamente necesaria para resultados confiables.

---

### **Distribuciones antes y después del escalado**  

**Observación técnica:**  
El `StandardScaler` centra la media pero amplifica outliers, el `MinMaxScaler` reduce el rango pero mantiene el sesgo, y el `RobustScaler` logra la mayor estabilidad.

**Interpretación analítica:**  
Las diferencias visuales demuestran cómo cada método responde a la presencia de colas largas.  
`RobustScaler` reduce la varianza sin alterar la estructura de la distribución.

**Reflexión metodológica:**  
Elegir el *scaler* no es una cuestión estética: implica definir qué estadístico (media, rango o mediana) representa mejor a la población.

---

### **Efecto del Log Transform**  

**Observación técnica:**  
Tras aplicar `np.log1p()` sobre `LotArea`, el *skewness* bajó de 2.9 a 0.28 y la curtosis se normalizó.

**Interpretación analítica:**  
La variable deja de concentrar la varianza en pocos valores altos, y la dispersión se vuelve más simétrica y manejable.

**Reflexión metodológica:**  
El orden correcto de transformaciones **Log → Scale** reduce errores de redondeo y produce resultados más reproducibles en pipelines.

---

### **Correlación original vs escalada**  

**Observación técnica:**  
Las correlaciones lineales permanecen casi inalteradas tras el escalado.

**Interpretación analítica:**  
Los *scalers* ajustan la magnitud pero no la relación entre variables, confirmando que la estructura del dataset se preserva.

**Reflexión metodológica:**  
Un buen escalado debe cambiar la escala, no el sentido de la información.  
Esta evidencia valida que el pipeline respeta la integridad de los datos.

---

### **Relación entre área y precio (antes y después del log)**  

**Observación técnica:**  
El logaritmo de `GrLivArea` y `SalePrice` genera una nube más compacta y lineal.

**Interpretación analítica:**  
La linealización mejora la capacidad de ajuste del modelo, especialmente para regresión lineal o Ridge/Lasso.

**Reflexión metodológica:**  
El *log transform* reduce el peso de los valores extremos y mejora la interpretabilidad de la relación área-precio.

---

### Comparación de métodos de escalado**  

| Método | Leakage | R² | MAE | Observaciones |
|---------|----------|------|------|---------------|
| **Con leakage** | ❌ | 0.92 | 14.5k | Métricas infladas por contaminación del test set. |
| **Sin leakage** | ✅ | 0.82 | 17.8k | Resultados realistas, dependientes del orden manual. |
| **Pipeline anti-leakage** | ✅ | 0.83 | 17.6k | Reproducible, estable y éticamente correcto. |

**Observación técnica:**  
El pipeline automatizado produce métricas coherentes y reproducibles.

**Interpretación analítica:**  
El leve descenso del R² (de 0.92 a 0.83) no representa una pérdida, sino la eliminación del sesgo inducido por *leakage*.  

**Reflexión metodológica:**  
El pipeline garantiza integridad, evita errores humanos y asegura que las métricas reflejen la verdadera capacidad predictiva del modelo.

---

## Conclusiones

- Las variables `LotArea` y `GrLivArea` fueron las principales fuentes de distorsión en las distancias numéricas.  
- `RobustScaler` resultó el método más apropiado por su resistencia a *outliers* estructurales.  
- El orden **Log → Scale** mejora la normalidad de las distribuciones y la estabilidad numérica.  
- El pipeline anti-leakage asegura reproducibilidad y trazabilidad, evitando contaminación de datos.  
- Las métricas sin leakage son más bajas, pero **honestas y generalizables**.

 El proceso de *feature scaling* y diseño del pipeline permitió confirmar de manera empírica varios principios clave de la ingeniería de datos moderna:

---

## Reflexión final

- **Limitaciones:** las conclusiones dependen del tipo de modelo. Los efectos del escalado pueden variar en árboles de decisión o redes neuronales.  
- **Decisiones discutibles:** mantener outliers estructurales mejora la generalización, pero puede afectar métricas locales.  
- **Mejoras futuras:** explorar `PowerTransformer` o `QuantileTransformer`, agrupar columnas por tipo y evaluar métricas no lineales.  
- **Ética del preprocesamiento:** evitar *data leakage* no solo mejora la calidad técnica, sino que respeta los principios de transparencia y veracidad de los resultados.  

> *El rigor técnico sin ética es solo automatización de errores.*

---

## Notebook en Google Colab

---

## Referencias

- Kaggle: *Ames Housing Dataset*.  
- Scikit-learn: *Preprocessing, Pipelines & Model Evaluation*.  
- Pandas & Seaborn Documentation.  
- Kurucz, J.F. (2025). *Feature Scaling & Anti-Leakage Pipeline – UCU Ingeniería de Datos*.

---

## Navegación

- [⬅️ Volver a UT2](../main.md)  
- [➡️ Ir a Práctica 7 — Feature Engineering](../practica7/main7.md)
