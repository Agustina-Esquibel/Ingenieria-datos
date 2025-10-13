---
title: Ames Housing bajo la lupa — Reconstrucción de información faltante con imputación contextual
date: 2025-09-10
---

## Contexto

El conjunto de datos **Ames Housing (Iowa)** contiene información detallada sobre propiedades inmobiliarias: dimensiones, materiales, ubicación, estado y precios de venta.  
Por su amplitud y heterogeneidad, se utiliza con frecuencia para evaluar la calidad de los datos y los efectos del *missing data* en los procesos de modelado predictivo.

En este trabajo se desarrolló un flujo de análisis orientado a **reconstruir información faltante de manera contextual y reproducible**, aplicando técnicas de imputación apropiadas y documentando las decisiones éticas involucradas en cada etapa del proceso.

---

## Objetivos

- Identificar y clasificar los valores faltantes según su mecanismo (MCAR, MAR o MNAR).  
- Analizar el impacto del *missing data* sobre la integridad del dataset y la confiabilidad de los modelos.  
- Implementar estrategias de imputación contextual, adecuadas al tipo y significado de cada variable.  
- Automatizar el proceso de limpieza mediante pipelines reproducibles con *scikit-learn*.  
- Documentar y justificar cada decisión metodológica desde una perspectiva ética y de transparencia.

---

## Desarrollo

El análisis se realizó en **Google Colab**, utilizando librerías como `pandas`, `numpy`, `seaborn`, `matplotlib`, `missingno` y `scikit-learn`.  
El proceso siguió las etapas del modelo **CRISP-DM**, adaptadas al enfoque de calidad y ética en ingeniería de datos.

### 1. Comprensión del problema

Se exploraron los mecanismos de generación de datos faltantes, observando que los valores ausentes no se distribuían aleatoriamente.  
Se detectaron patrones vinculados con la estructura y las características de las viviendas (por ejemplo, la ausencia de datos en “GarageArea” se debía a que muchas propiedades no disponían de garaje).

### 2. Comprensión de los datos

A través de *heatmaps* y matrices de correlación, se confirmó que las variables relacionadas con instalaciones opcionales (piscina, sótano, garaje) presentaban patrones de ausencia sistemáticos.  
Esto permitió clasificar los *missing values* como **MAR (Missing At Random)**, al depender de otras variables observadas.

### 3. Preparación de los datos

Se diseñó una estrategia de imputación combinada:
- Variables numéricas: imputación por **mediana** o **regresión lineal simple**, según la distribución.  
- Variables categóricas: imputación por **moda** o etiqueta “Sin dato”, cuando el valor nulo representaba una condición estructural (ausencia real).  
- Columnas con más del 40 % de valores faltantes fueron descartadas tras verificar su baja contribución predictiva.

El proceso se automatizó mediante un **pipeline** con `ColumnTransformer` y `SimpleImputer`, garantizando reproducibilidad y control de errores.

### 4. Evaluación del proceso

Se compararon las distribuciones de las variables antes y después de la imputación mediante histogramas y boxplots, comprobando que las imputaciones no distorsionaban significativamente la varianza ni las relaciones originales.  
Las métricas de sesgo y desviación mostraron estabilidad respecto a los datos originales.

### 5. Documentación ética

Cada decisión fue registrada, justificando las razones técnicas y éticas detrás de cada imputación o eliminación.  
Se enfatizó la importancia de mantener trazabilidad y transparencia en las transformaciones, evitando ocultar o distorsionar información relevante.

---

## Evidencias

### Mapa de calor de valores faltantes

El mapa evidencia que las variables estructurales concentran la mayoría de los valores ausentes, reflejando dependencias contextuales entre las características de las viviendas.

### Comparación de distribuciones antes y después de la imputación

Las imputaciones mantuvieron la forma de las distribuciones y preservaron la consistencia estadística general del dataset.

---

## Insights clave

1. Aproximadamente el 15 % de las variables presentaban más del 20 % de valores faltantes.  
2. Los valores ausentes respondían mayoritariamente a un patrón MAR, no a errores de registro.  
3. La imputación contextual resultó más precisa que las estrategias globales, al respetar las relaciones estructurales del dataset.  
4. La documentación transparente de decisiones fortaleció la reproducibilidad y la trazabilidad del análisis.  
5. La calidad de los datos depende tanto de su completitud como del entendimiento del contexto en el que se generan.

---

## Reflexión

El análisis de *missing data* en Ames Housing permitió comprender que la limpieza de datos no es solo una tarea técnica, sino también una **decisión analítica y ética**.  
Imputar valores de manera contextual implica reconocer el significado de cada ausencia y evitar que las decisiones de procesamiento introduzcan sesgos o falsifiquen la realidad representada.

La reproducibilidad, la transparencia y la justificación de cada transformación son pilares de una práctica profesional responsable en ingeniería de datos.  
Este ejercicio consolida el aprendizaje en calidad de datos, promoviendo una mirada crítica sobre el impacto de cada decisión en los resultados analíticos y predictivos.

---

## Notebook en Google Colab

---

## Referencias

- Ames Housing Dataset, Kaggle Repository.  
- Kaggle. *Data Cleaning Course.*  
- Pandas Documentation. *Handling Missing Data.*  
- Scikit-learn Documentation. *Imputation and Pipeline Construction.*

---

## Navegación

⬅️[Volver a Unidad Temática 2](../main.md)  
📓[Ir a Práctica 6 – Feature Scaling y Anti-Leakage Pipeline](../practica6/main6.md)
