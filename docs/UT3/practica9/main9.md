---
title: "Codificando la realidad: cómo el encoding categórico mejora la predicción de ingresos en datos del censo"
date: 2025-10-15
---

## Contexto  
Esta práctica explora el impacto del **encoding categórico** en modelos de clasificación, utilizando el dataset **Adult Income (Census 1994)**.  
El objetivo es predecir si una persona supera los 50.000 USD anuales a partir de variables demográficas, laborales y socioeconómicas.

La presencia de variables categóricas con **alta cardinalidad** hace necesario comparar diferentes técnicas de encoding —Label, One-Hot y Target Encoding— evaluando su impacto en la precisión, dimensionalidad y estabilidad del modelo.  
El trabajo sigue una metodología CRISP-DM, con énfasis en *Data Preparation* y la importancia ética del preprocesamiento correcto (evitando leakage).

---

## Objetivos  
- Analizar cardinalidad y complejidad de las variables categóricas.  
- Implementar y comparar múltiples técnicas de codificación.  
- Evitar *data leakage* mediante validación cruzada en Target Encoding.  
- Diseñar un pipeline escalable con ColumnTransformer y branching.  
- Evaluar el impacto de cada método en métricas y eficiencia.  
- Interpretar resultados mediante *feature importance* y *SHAP*.

---

## Actividades  

### 1. Exploración inicial  
Se analizó la cardinalidad de las variables categóricas, clasificándolas en:

- **Baja cardinalidad:** adecuadas para One-Hot.  
- **Alta cardinalidad:** requieren estrategias como Target Encoding.  

### 2. Experimento 1 — Label Encoding  
Ventaja: rápido y compacto.  
Desventaja: introduce artificialmente orden y distancia entre categorías.

### 3. Experimento 2 — One-Hot Encoding  
Adecuado para baja cardinalidad.  
Incrementa dimensionalidad: se controla mediante ColumnTransformer.

### 4. Experimento 3 — Target Encoding  
Justificación técnica: captura relación directa entre la categoría y la probabilidad del target.  
Justificación ética: evita leakage utilizando validación cruzada (KFold).  

### 5. Pipeline híbrido  
Se construyó un pipeline con **branching**, asignando:

- Label Encoding → modelos basados en árboles.  
- One-Hot → baja cardinalidad.  
- Target Encoding → alta cardinalidad.

### 6. Interpretabilidad  
Se aplicaron **feature importance** y **SHAP values** para analizar el peso de variables numéricas y categóricas codificadas.

---

## Desarrollo  

El trabajo siguió una estrategia comparativa controlada: mismo modelo base, mismas métricas, mismo split.  
Cada encoding se probó de forma aislada para evaluar rendimiento, luego se integraron en un pipeline mixto optimizado.  
El Target Encoding se implementó con suavizado (**smoothing**) y validación cruzada, reduciendo varianza en categorías poco frecuentes.

El análisis se complementó con explicabilidad a partir de SHAP, cuantificando cómo cambia la contribución de cada variable cuando se aplican distintos encodings.

---

## Evidencias  

### Cardinalidad de Variables Categóricas  
![Cardinalidad de Variables Categóricas](IMG_4254.png)  
**Conclusión:** La alta cardinalidad de variables como `native-country` y `occupation` justifica el uso de Target Encoding para evitar explosión dimensional.

### Distribución de Education según nivel de ingreso  
![Distribución Education](IMG_4326.png)  
**Conclusión:** La proporción de ingresos altos crece con el nivel educativo, reforzando la relevancia de codificar correctamente la variable `education`.

### Distribución de Occupation según nivel de ingreso  
![Distribución Occupation](IMG_4261.png)  
**Conclusión:** Profesiones técnicas y administrativas muestran mayor proporción de ingresos superiores, indicando que un encoding más expresivo captura mejor estas relaciones.

### Distribución de Relationship según nivel de ingreso  
![Distribución Relationship](IMG_4262.png)  
**Conclusión:** La categoría “Husband” muestra la mayor proporción de ingresos altos; este patrón influye en el comportamiento del modelo si no se codifica correctamente.

### Matriz de Correlaciones – Variables numéricas  
![Matriz de Correlaciones Numéricas](IMG_4258.png)  
**Conclusión:** `education-num`, `age` y `capital-gain` son las variables numéricas más relacionadas con el target; sirven como baseline para comparar la contribución del encoding.

### Matriz de Correlaciones (Top variables)  
![Matriz de Correlaciones Top](IMG_4328.png)  
**Conclusión:** El análisis refinado identifica variables críticas, útiles para priorizar durante la selección de features.

### Importancia de Features – Modelo Final  
![Top 15 Features más importantes](IMG_4257.png)  
**Conclusión:** Tras el pipeline mixto, las variables más influyentes combinan numéricas y categóricas codificadas mediante Target Encoding.

### Importancia y Distribución de Features  
![Distribución Importancia de Features](IMG_4320.png)  
**Conclusión:** La dispersión evidencia qué variables aportan señal estable, validando la combinación de métodos de encoding.

### Comparación de Modelos y Codificación  
![Comparación de Modelos y Encoding](IMG_4252.png)  
**Conclusión operativa:**  
El pipeline mixto logra el mejor balance entre precisión, dimensionalidad y estabilidad, superando a cualquier método aplicado de forma aislada.

---

## Insights clave  

- El encoding categórico influye directamente en el rendimiento y la interpretabilidad.  
- No existe un método universal: depende de cardinalidad, distribución y modelo utilizado.  
- Target Encoding ofrece la mejor relación entre precisión y eficiencia cuando se controla el leakage.  
- Los pipelines híbridos permiten aprovechar lo mejor de cada estrategia.  
- La explicabilidad revela cómo el encoding modifica el peso relativo de las variables.

---

## Reflexión  

El proceso confirma que la representación matemática de las variables categóricas determina, en gran medida, el éxito del modelo predictivo.  
Las decisiones tomadas en esta etapa tienen consecuencias éticas, técnicas y operativas: afectan precision, interpretabilidad y el riesgo de sesgos ocultos.

El encoding categórico se consolida así como una fase estratégica donde convergen estadística, diseño de pipelines y comprensión del dominio.  
Un método adecuado permite transformar datos heterogéneos del mundo real en información estructurada, sin perder significado.

---

## Notebook en Google Colab  
📓 El notebook completo con el desarrollo de esta práctica puede consultarse en el siguiente enlace:  
[Abrir en Google Colab](https://colab.research.google.com/github/Agustina-Esquibel/Ingenieria-datos/blob/main/docs/UT3/practica9/UT3_Practica9.ipynb)

---

## Referencias  
- Category Encoders Library  
- Scikit-learn Preprocessing Documentation  
- Feature Engineering for Machine Learning – O’Reilly  
- Kaggle Target Encoding Guide  

---

## Navegación  
⬅️ Diseñando el valor oculto: Feature Engineering  
➡️ Reduciendo el ruido: PCA y Feature Selection  
📓 Índice del Portafolio
