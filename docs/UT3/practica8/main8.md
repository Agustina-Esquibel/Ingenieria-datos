---
title: "Diseñando el valor oculto: cómo el feature engineering mejora la predicción de precios de vivienda"
date: 2025-10-01
---

## Contexto  
Esta práctica aborda el proceso de **feature engineering** aplicado al análisis y predicción de precios de vivienda.  
El objetivo central es comprender cómo la creación de **nuevas variables derivadas e interacciones** puede mejorar de forma significativa el desempeño predictivo de modelos y, al mismo tiempo, aumentar la interpretabilidad del problema inmobiliario.

El trabajo se desarrolla en dos etapas complementarias:  
1. La construcción y experimentación con un **dataset sintético**, que permite aislar conceptos y validar transformaciones en un entorno controlado.  
2. La aplicación de ese mismo pipeline sobre una muestra real del dataset **Ames Housing**, verificando consistencia, estabilidad y valor predictivo de las nuevas features.

El enfoque combina razonamiento estadístico, conocimiento del dominio y operaciones matemáticas orientadas a modelar relaciones estructurales del mercado inmobiliario.

---

## Objetivos  
- Implementar un flujo completo de **feature engineering** aplicando transformaciones matemáticas, proporcionales, temporales y de interacción.  
- Analizar la **distribución, correlación e importancia** de las nuevas variables.  
- Identificar qué features aportan valor predictivo a partir de métricas estadísticas y modelos de *machine learning*.  
- Validar el proceso con una muestra del dataset real **Ames Housing**.

---

## Actividades  

El desarrollo comenzó con la creación del entorno de trabajo en Google Colab y la instalación de librerías esenciales (`pandas`, `numpy`, `matplotlib`, `seaborn`, `sklearn`).  
Con el fin de experimentar sin ruido externo, se generó un **dataset sintético**, incorporando variables típicas del sector: superficie, precio, dormitorios, baños, tamaño del lote, año de construcción, distancia al centro, rating escolar y criminalidad.

### Creación de features derivadas  
Se diseñó un conjunto amplio de nuevas variables pensadas para capturar relaciones estructurales del mercado:

- **Eficiencia espacial:** `price_per_sqft`, `sqft_per_bedroom`, `density`, `bed_bath_ratio`.  
- **Transformaciones matemáticas:** `log_price`, `sqrt_sqft`, `sqft_squared`.  
- **Relaciones proporcionales:** `lot_coverage`, `bedrooms_per_1000sqft`.  
- **Variables temporales:** `property_age`, `age_category`, `is_new_property`, `decade_built`.  
- **Features de dominio:** `space_efficiency`, `crowded_property`, `advanced_location_score`.

El criterio de diseño se basó en mejorar la **explicabilidad** y representar mejor las dinámicas espaciales, temporales y estructurales del mercado.

### Análisis de distribuciones y correlaciones  
Se identificaron relaciones relevantes como:  
- correlación negativa entre eficiencia espacial y densidad interna (`-0.42`),  
- correlación negativa entre calidad percibida y antigüedad (`-0.56`),  
- patrones esperables entre precio, superficie, antigüedad y distancia al centro.

### Evaluación de importancia  
Mediante **Mutual Information** y **Random Forest Feature Importance**, se identificó que:

- `log_price` y `price_per_sqft` son los predictores más robustos,  
- variables de eficiencia y distribución interna aportan estructura adicional al modelo,  
- features de dominio refuerzan el carácter explicativo de las predicciones.

Luego, el pipeline fue aplicado a una muestra del dataset **Ames Housing**, verificando coherencia y estabilidad frente a datos reales.

---

## Desarrollo

El trabajo siguió un flujo incremental, comenzando con el dataset sintético para asegurar control sobre las transformaciones.  
Posteriormente se evaluaron las features en términos visuales y estadísticos, y se midió su impacto con métricas de importancia.  

Finalmente, se integraron features de dominio —diseñadas según criterios inmobiliarios— lo que permitió validar la utilidad práctica del pipeline en un escenario real.

---

## Evidencias

### Distribución logarítmica del precio  
![Distribución logarítmica del precio](../practica8/IMG_4228.png)  
La transformación logarítmica reduce la asimetría del precio, estabilizando la varianza y mejorando la linealidad con otras variables relevantes.

### Precio por m² según vecindario  
![Precio por m² según vecindario](../practica8/IMG_4229.png)  
Los vecindarios presentan diferencias claras de valor por metro cuadrado, destacando la importancia del contexto geográfico como feature explicativa.

### Distribuciones de nuevas features derivadas  
![Distribuciones de nuevas features derivadas](../practica8/IMG_4230.png)  
Las variables derivadas muestran patrones asimétricos, lo cual motiva transformaciones adicionales o escalado previo al modelado.

### Importancia de features  
![Importancia de features](../practica8/IMG_4231.png)  
`log_price` y `price_per_sqft` se consolidan como las variables más influyentes, seguidas por indicadores de eficiencia interna y transformaciones matemáticas.

### Correlaciones entre features derivadas  
![Correlaciones entre features derivadas](../practica8/IMG_4236.png)  
Se confirma la relación entre antigüedad y calidad estructural, mientras que otras variables mantienen independencia útil para el modelado.

### Relación suavizada: Precio vs Distancia al centro  
![Relación suavizada: Precio vs Distancia al centro](../practica8/IMG_4238.png)  
Las viviendas nuevas mantienen un valor más alto en todas las distancias al centro urbano, reforzando el rol explicativo de la variable `distance_to_city`.

---

## Insights clave  

- El feature engineering convierte datos básicos en **conocimiento estructurado**.  
- Las features de dominio aportan **valor estratégico** adicional.  
- `log_price` y `price_per_sqft` emergen como predictores altamente robustos.  
- Las correlaciones temporales y espaciales ayudan a captar dinámicas inmobiliarias reales.  
- La metodología validada con Ames Housing demuestra **generalización y consistencia** del pipeline.

---

## Reflexión  

El proceso confirmó que el valor de los datos surge de cómo se transforman y representan.  
El feature engineering se posiciona como una etapa crítica donde convergen creatividad, conocimiento del dominio y técnica estadística.  
Un pipeline bien diseñado potencia tanto la capacidad predictiva como la interpretabilidad del modelo, evitando sobreajuste y guiando decisiones basadas en evidencia.

En síntesis: **la ingeniería de atributos transforma complejidad en claridad** y convierte datos crudos en información capaz de generar decisiones más inteligentes.

---

## Notebook en Google Colab  
📓 El notebook completo con el desarrollo de esta práctica puede consultarse en el siguiente enlace:  
[Abrir en Google Colab](https://colab.research.google.com/github/Agustina-Esquibel/Ingenieria-datos/blob/main/docs/UT3/practica8/UT3_Practica_8.ipynb)

---

## Referencias  
- Feature Selection – Scikit-learn Documentation  
- Feature Engineering for Machine Learning – O’Reilly  

---

## Navegación  
⬅️ Volver a Unidad Temática 3  
➡️ Codificando la realidad – Práctica 9  
📓 Índice del Portafolio
