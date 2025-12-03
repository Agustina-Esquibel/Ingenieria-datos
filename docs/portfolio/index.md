---
title: "Portafolio - Índice"
date: 2025-09-06
---

Prácticas del curso de Ingeniería de Datos, organizadas por unidades.  
Cada práctica contiene **objetivos, hallazgos principales y reflexiones**.

---

## Unidad Temática 1 – Análisis Exploratorio y Fuentes

### 🌸 Explorando el Iris Dataset: primeros patrones florales y variables predictivas
Link: [Ver práctica](../UT1/practica1/main1.md)

**Objetivo:** 
Explorar el dataset Iris y aplicar un análisis exploratorio inicial.  

**Hallazgos clave:**
- La especie *Setosa* se separa claramente de las demás.
- Correlaciones fuertes entre el largo y el ancho de los pétalos.
- Dataset balanceado con 50 registros por especie.

**Reflexión:** 
Esta práctica me ayudó a familiarizarme con técnicas básicas de EDA y a ganar confianza en la interpretación de correlaciones simples mediante visualizaciones claras.

---

### ⚙️ Configuración del portfolio en GitHub
Link: [Ver práctica](../UT1/practica2/main2.md)

**Objetivo:** 
Crear un repositorio en GitHub a partir del template y publicar el portafolio con GitHub Pages.  

**Hallazgos clave:**
- Repositorio configurado correctamente con estructura inicial de carpetas.
- GitHub Actions desplegó el sitio sin errores.
- Portafolio visible online desde etapas tempranas.

**Reflexión:** 
Aunque no implicó análisis de datos, esta práctica fue esencial para organizar el flujo de trabajo, mantener trazabilidad y asegurar que los resultados pudieran documentarse y compartirse fácilmente.

---

### 🎬 Explorando el catálogo de Netflix: tendencias globales y patrones de contenido audiovisual
Link: [Ver práctica](../UT1/practica3/main3.md)

**Objetivo:** 
Analizar el catálogo de Netflix considerando años, tipos de contenido, países y duración.  

**Hallazgos clave:**
- Predominio de películas sobre series.
- Crecimiento sostenido de estrenos desde 2016.
- Concentración de la producción en pocos países (principalmente EE.UU. e India).

**Reflexión:** 
Trabajar con este dataset me permitió enfrentarme a problemas reales de datos incompletos y extraer conclusiones a partir de visualizaciones que evidencian patrones de la industria audiovisual.

---

### 🚕 Analizando los viajes de Nueva York: integración de múltiples fuentes y comparación con Joins

Link: [Ver práctica](../UT1/practica4/main4.md)

**Objetivo:** 
Integrar datasets de viajes, zonas y calendario para aplicar distintos *joins* y enriquecer el análisis.  

**Hallazgos clave:**
- El `LEFT JOIN` permitió preservar todos los viajes, incluso sin coincidencia en zonas.
- Se observaron diferencias en la cantidad de viajes entre días normales y especiales.
- Boroughs con mayores volúmenes de viajes: Manhattan, Queens y Brooklyn.

**Reflexión:** 
Esta práctica fue la más desafiante de la UT1, porque implicó integración de múltiples fuentes y análisis temporal. Me permitió valorar cómo la correcta unión de datasets cambia el nivel de los insights obtenidos.

---

🛍️ **Explorando el catálogo de moda: análisis de precios y marcas**  
Link: [Ver práctica](../UT1/extraUT1/extramain.md)

**Objetivo:**  
Analizar datos de ventas de moda en formato JSON para comparar precios, marcas y temporadas, aplicando técnicas de EDA y visualización.

**Hallazgos clave:**  
- Se identificaron diferencias de precios promedio entre categorías y marcas.  
- Las marcas *Zara*, *Mango* y *Banana Republic* destacaron por tener mayor volumen en catálogo.  
- Los precios mostraron variaciones estacionales con picos en primavera y otoño.  

**Reflexión:**  
Este análisis permitió trasladar lo aprendido en la UT1 a un nuevo dominio y formato de datos (JSON), fortaleciendo la capacidad para limpiar, explorar y visualizar información estructurada en contextos comerciales.

---

## Unidad Temática 2 — Limpieza, imputación y ética de datos

### 🧱 Ames Housing bajo la lupa: reconstrucción de información faltante  
*Link:* [Ver práctica](../UT2/practica5/main5.md)  

**Objetivo:** Detectar y analizar valores faltantes en el dataset Ames Housing, aplicando estrategias de imputación contextual y reproducible.  

**Hallazgos clave:**  
- Los mecanismos de *missing data* varían según la variable (MCAR, MAR, MNAR).  
- La imputación contextual mejora la consistencia sin distorsionar distribuciones clave.  
- Documentar el proceso aumenta la trazabilidad y transparencia metodológica.  
**Reflexión:** Aprendí a aplicar imputaciones robustas y justificar decisiones técnicas desde una mirada ética y reproducible.

---

### ⚙️ Escalado y Anti-Leakage Pipeline: preprocesamiento ético y reproducible  
*Link:* [Ver práctica](../UT2/practica6/main6.md)  

**Objetivo:** Implementar un pipeline que normalice, escale y transforme datos sin fuga de información entre *train* y *test*.  

**Hallazgos clave:**  
- El *feature scaling* puede alterar relaciones estadísticas si no se controla el *data leakage*.  
- Los métodos `StandardScaler`, `MinMaxScaler` y `RobustScaler` muestran comportamientos distintos ante outliers.  
- El *log transform* mejora la simetría de variables muy sesgadas.  
**Reflexión:** Fortalecí el criterio para diseñar procesos de preprocesamiento reproducibles y éticamente responsables.

---

### ⚖️ Sesgo bajo la lupa: detección, corrección y decisiones éticas con Fairlearn  
*Link:* [Ver práctica](../UT2/practica7/main7.md)  

**Objetivo:** Detectar, medir y mitigar sesgos en modelos predictivos mediante métricas de *fairness* aplicadas a casos reales (Boston Housing y Titanic).  

**Hallazgos clave:**  
- Los sesgos históricos influyen directamente en los modelos si no se corrigen.  
- Fairlearn permite equilibrar *accuracy* y equidad de manera cuantificable.  
- Las decisiones éticas requieren evaluar impacto social, no solo rendimiento.  
**Reflexión:** Comprendí cómo la equidad y la ética son parte del ciclo técnico de un modelo, no un añadido posterior.

## Unidad Temática 3 – Feature Engineering

### 🏡 Diseñando el valor oculto: cómo el feature engineering mejora la predicción de precios de vivienda  
Link: [Ver práctica](../UT3/practica8/main8.md)

**Objetivo:**  
Aplicar técnicas de *feature engineering* numérico y de interacción para mejorar la capacidad predictiva en un problema de precios de vivienda.

**Hallazgos clave:**  
- Transformaciones como `log_price` y `price_per_sqft` aportaron estabilidad y mayor señal predictiva.
- Las features derivadas (eficiencia del espacio, densidad interna, interacción precio–antigüedad) capturaron relaciones no lineales relevantes.
- El análisis validó la importancia de combinar transformaciones matemáticas con conocimiento del dominio inmobiliario.

**Reflexión:**  
Esta práctica permitió comprender cómo el diseño de variables puede potenciar significativamente el rendimiento del modelo, incluso más que cambios en el algoritmo. El *feature engineering* se consolidó como una herramienta estratégica cuando se aplica con criterio técnico y de negocio.

---

### 🧩 Codificando la realidad: cómo el encoding categórico mejora la predicción de ingresos en datos del censo  
Link: [Ver práctica](../UT3/practica9/main9.md)

**Objetivo:**  
Evaluar y comparar distintos métodos de codificación categórica en un dataset con alta cardinalidad.

**Hallazgos clave:**  
- El *target encoding* obtuvo el mejor desempeño ante categorías numerosas.
- One-Hot Encoding generó expansión dimensional significativa.
- Label Encoding fue útil en variables con componente ordinal, pero introdujo orden artificial en categorías nominales.

**Reflexión:**  
La práctica resaltó que la correcta selección del método de codificación tiene un impacto directo en la calidad del modelo. Adaptar el encoding al tipo de variable resultó clave para mantener interpretabilidad y eficiencia.

---

### 🎛️ Reduciendo el ruido: cómo PCA y Feature Selection revelan las variables clave del valor inmobiliario  
Link: [Ver práctica](../UT3/practica10/main10.md)

**Objetivo:**  
Aplicar PCA y técnicas de selección de variables para identificar las *features* más importantes en un modelo de predicción de precios.

**Hallazgos clave:**  
- PCA conservó +90% de la varianza con pocas componentes.
- Mutual Information y SelectKBest permitieron aislar un conjunto estable de variables relevantes.
- La combinación de reducción dimensional y selección mejoró la interpretabilidad y redujo sobreajuste.

**Reflexión:**  
Esta práctica reforzó la importancia de eliminar redundancia y ruido en datasets complejos. La reducción dimensional demostró ser fundamental para simplificar el modelo sin perder capacidad predictiva.

---

### ⏳ Modelando el tiempo: cómo el feature engineering temporal anticipa la recompra en e-commerce  
Link: [Ver práctica](../UT3/practica11/main11.md)

**Objetivo:**  
Diseñar un pipeline temporal para predecir *repeat purchase* mediante lag features, rolling windows, RFM analysis y validación temporal estricta.

**Hallazgos clave:**  
- Las lag features y ventanas móviles capturaron patrones históricos esenciales.
- RFM (Recency–Frequency–Monetary) aportó información robusta sobre comportamiento del cliente.
- TimeSeriesSplit evitó *data leakage* y permitió evaluar el modelo en un contexto temporal realista.

**Reflexión:**  
La práctica evidenció que en modelos temporales, el manejo del tiempo y la prevención de *leakage* son tan importantes como las propias features. El enfoque temporal demostró mejorar la performance considerablemente frente a un modelo base sin ingeniería temporal.

---

## Unidad Temática 4 – Datos Especiales

### 🗺️ Geointeligencia urbana: cobertura del SUBTE, densidad poblacional y demanda vecinal en Buenos Aires  
Link: [Ver práctica](../UT4/practica12/main12.md)

**Objetivo:**  
Analizar datos geoespaciales reales aplicando GeoPandas y Shapely para integrar capas urbanas (subte, barrios, densidad poblacional) y detectar zonas prioritarias según accesibilidad y demanda.

**Hallazgos clave:**  
- Identificación de barrios con menor cobertura del transporte público.  
- Cruce exitoso de capas geográficas mediante *overlay* y *spatial join*.  
- Variaciones en densidad poblacional permiten detectar zonas con desbalance entre oferta y demanda.

**Reflexión:**  
Esta práctica permitió entender cómo los datos geoespaciales amplían el análisis más allá de las tablas tradicionales, incorporando contexto territorial y espacial para generar insights urbanos significativos.

---

### 📸 Visión computacional aplicada: diagnóstico, contraste y extracción de descriptores con OpenCV  
Link: [Ver práctica](../UT4/practica13/main13.md)

**Objetivo:**  
Implementar un pipeline de preprocesamiento de imágenes, incluyendo conversión de espacios de color, histogramas, mejora de contraste global/local y extracción de features (SIFT/ORB).

**Hallazgos clave:**  
- Comparación clara entre imágenes en RGB vs. escala de grises.  
- El contraste adaptativo (CLAHE) mejora zonas oscuras sin saturar el resto de la imagen.  
- Los descriptores SIFT/ORB generan puntos clave robustos para tareas posteriores de ML o matching.

**Reflexión:**  
Esta práctica mostró cómo la preparación de imágenes impacta directamente en la calidad de los features. Introdujo las bases del procesamiento visual y la importancia de preparar correctamente los datos antes de cualquier modelo.

---

### 🎧 Audio para Machine Learning: limpieza, visualización y extracción de MFCC  
Link: [Ver práctica](../UT4/practica14/main14.md)

**Objetivo:**  
Diseñar un pipeline de preprocesamiento de audio: carga, inspección visual, limpieza básica, transformación a espectrogramas y extracción de MFCC listos para su uso en modelos de ML.

**Hallazgos clave:**  
- La visualización de la forma de onda y el espectrograma permite detectar ruido, silencios y patrones temporales.  
- Los MFCC capturan características esenciales del timbre y permiten representar audio en formato numérico comparable.  
- La estandarización del pipeline garantiza que todos los audios produzcan features consistentes.

**Reflexión:**  
Trabajar con audio mostró la importancia de adaptar el pipeline a cada tipo de dato. La práctica fortaleció la comprensión de cómo transformar señales crudas en información estructurada para modelos de aprendizaje.

---

## Unidad Temática 5 – Pipelines ETL

### ☁️ Datos en movimiento: creando un pipeline ETL en Google Cloud  
Link: [Ver práctica](../UT5/practica15/main15.md)

**Objetivo:**  
Implementar un pipeline ETL/ELT utilizando Cloud Storage, Cloud Functions y BigQuery, con ejecución basada en eventos y transformación posterior.

**Hallazgos clave:**  
- Activación automática del pipeline mediante triggers.  
- Flujo ELT: carga inicial en BigQuery y transformaciones posteriores.  
- Integración fluida entre almacenamiento, funciones serverless y motor analítico.

**Reflexión:**  
Esta práctica permitió ver cómo funciona un pipeline moderno en la nube: automatizado, reproducible y sin tareas manuales.

---

### 🧽 DataPrep: limpieza visual de datos orientada a pipeline  
Link: [Ver práctica](../UT5/practica16/main16.md)

**Objetivo:**  
Crear un pipeline ETL visual con Dataprep, aplicando reglas reproducibles de limpieza y transformación integradas con BigQuery.

**Hallazgos clave:**  
- Perfilado automático de calidad de datos.  
- Transformaciones visuales versionadas como reglas.  
- Exportación directa a sistemas analíticos.

**Reflexión:**  
Dataprep mostró cómo diseñar pipelines ETL sin código, manteniendo trazabilidad, documentación y consistencia entre ejecuciones.

---
  
