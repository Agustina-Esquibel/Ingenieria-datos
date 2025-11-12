---
title: "Reduciendo el ruido: cómo PCA y Feature Selection revelan las variables clave del valor inmobiliario"
date: 2025-11-12
---

## Contexto
Esta práctica aborda el desafío de **reducir la complejidad de los datos sin perder su esencia predictiva**, aplicando dos estrategias complementarias:  
**PCA (Análisis de Componentes Principales)** y **Feature Selection**.  

A partir del dataset **Ames Housing**, se busca identificar **qué variables explican realmente el precio de una vivienda**, diferenciando entre ruido estadístico y señales valiosas.  
El objetivo es descubrir cómo distintas técnicas —desde transformaciones lineales hasta selección basada en modelos— pueden mejorar la precisión del modelo y, al mismo tiempo, hacerlo más interpretable y eficiente.  

El enfoque combina rigor técnico con una mirada de negocio, mostrando que **reducir variables no significa perder información**, sino concentrar la atención en los factores que más impacto tienen en el mercado inmobiliario.

---

## Objetivos  
- Aplicar **PCA** para reducir dimensionalidad y analizar la varianza explicada.  
- Evaluar distintos métodos de **Feature Selection** (Filter, Wrapper, Embedded).  
- Comparar el impacto de cada método sobre las métricas de rendimiento (RMSE y R²).  
- Identificar las **features más robustas** y su relevancia en la predicción del precio de venta.  
- Reflexionar sobre los **trade-offs** entre precisión, interpretabilidad y costo computacional.

---

## Actividades  

1. **Preparación y preprocesamiento de datos**  
   - Carga y limpieza del dataset *Ames Housing* (1.460 observaciones, ~80 features).  
   - Imputación de valores faltantes (`median` y `most_frequent`).  
   - Codificación de variables categóricas con *Label Encoding*.  
   - Escalado de variables mediante `StandardScaler`.  

2. **Aplicación de PCA (Análisis de Componentes Principales)**  
   - Estandarización de datos + PCA con distintos valores de `n_components`.  
   - Análisis de la **varianza explicada acumulada** y generación de *scree plots*.  
   - Selección de componentes por umbral de varianza (80%, 90%, 95%).  
   - Interpretación de los *loadings* para entender qué combinaciones de features explican mejor la varianza del precio.  

3. **Filter Methods**  
   - Implementación de `SelectKBest` con **F-test (f_regression)** y **Mutual Information (mutual_info_regression)**.  
   - Selección de top-k features (k = 20, 30, 40) y comparación de desempeño con *Random Forest Regressor*.  
   - Identificación de features más influyentes según correlación y relevancia estadística.  

4. **Wrapper Methods**  
   - Aplicación de **Forward Selection**, **Backward Elimination** y **Recursive Feature Elimination (RFE)**.  
   - Evaluación de precisión mediante *cross-validation* (5-fold).  
   - Comparación de tiempos de ejecución y número de features seleccionadas.  

5. **Embedded Methods**  
   - Entrenamiento de modelos con **LassoCV**, **RidgeCV** y **Random Forest**.  
   - Análisis de coeficientes no nulos (Lasso) y *feature importance* (Random Forest).  
   - Visualización de las 10 variables más relevantes según importancia del modelo.  

6. **Comparación global de resultados**  
   - Consolidación de resultados en una tabla resumen de RMSE, R² y cantidad de features.  
   - Detección de *features consistentes* (presentes en múltiples métodos).  
   - Discusión sobre el equilibrio entre performance, interpretabilidad y tiempo de cómputo.  

---

## Desarrollo  

El desarrollo se realizó de manera incremental, iniciando con el preprocesamiento y escalado del dataset.  
Posteriormente, se aplicaron los tres enfoques principales de reducción de dimensionalidad:

1. **Filter Methods:** rápidos y estadísticamente interpretables.  
2. **Wrapper Methods:** más precisos pero de alto costo computacional.  
3. **Embedded Methods:** integran la selección de variables en el proceso de entrenamiento del modelo.  

Cada método fue evaluado mediante validación cruzada (5-fold) sobre métricas de **RMSE** y **R²**, considerando además la cantidad de features seleccionadas y el tiempo de ejecución.

Los resultados mostraron que el método **Mutual Information (Filter)** ofreció el mejor balance entre velocidad y precisión, mientras que **Forward Selection (Wrapper)** alcanzó un RMSE similar con menos variables, aunque con mayor tiempo de cómputo.  
El modelo **Random Forest (Embedded)** se destacó por su estabilidad y facilidad para interpretar la importancia relativa de las variables.

---

## Evidencias  

---

## Insights clave  

- **Mutual Information** fue el método más eficiente, combinando bajo error y alta velocidad.  
- **Wrapper Methods** (Forward/RFE) ofrecen gran precisión, pero son sensibles al tamaño del dataset.  
- **PCA** es útil para reducir colinealidad, pero sacrifica interpretabilidad.  
- **Lasso** demostró capacidad para eliminar variables redundantes sin afectar la performance.  
- La combinación **Filter + Wrapper** podría ofrecer el equilibrio ideal entre rendimiento y costo.

---

## Reflexión  

Esta práctica consolidó el entendimiento de cómo la **reducción de dimensionalidad** puede mejorar tanto la eficiencia como la generalización de los modelos de predicción.  
Mientras **PCA** actúa como un filtro matemático que condensa información, los métodos de **Feature Selection** permiten conservar variables interpretables y útiles desde el punto de vista del negocio.

El ejercicio demostró que la selección de características no solo es una cuestión técnica, sino también estratégica: elegir qué información conservar implica decidir **qué aspectos del problema son realmente relevantes**.  
Además, se evidenció que el mejor método depende del contexto: **los Filter Methods son ideales para datasets grandes y exploratorios**, mientras que los **Wrapper y Embedded Methods** son preferibles cuando se busca máxima precisión en modelos finales.

---

## Notebook en Google Colab  
📓 El notebook completo con el desarrollo de esta práctica puede consultarse en el siguiente enlace:  

---

## Referencias  
- [Scikit-learn: Feature Selection](https://scikit-learn.org/stable/modules/feature_selection.html)  
- [Principal Component Analysis – Documentation](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html)  
- [Feature Engineering & Selection – Kuhn & Johnson, 2020](https://bookdown.org/max/FES/)  

---

## Navegación  
⬅️ [Volver a Unidad Temática 3](../main.md)  
➡️  
📓 [Índice del Portafolio](../../portfolio/index.md)
