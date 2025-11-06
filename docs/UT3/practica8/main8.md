---
title: "Diseñando el valor oculto: cómo el feature engineering mejora la predicción de precios de vivienda"
date: 2025-10-01
---

## Contexto
Esta práctica se enfoca en el proceso de **feature engineering** aplicado a un caso de negocio inmobiliario.  
El objetivo es comprender cómo la creación de **nuevas variables derivadas e interacciones** mejora la capacidad predictiva de los modelos de precios de vivienda, utilizando primero un **dataset sintético** y luego validando los resultados con una muestra reducida del dataset real **Ames Housing**.  

El enfoque combina la **experimentación técnica** con el **conocimiento del dominio**, demostrando que el diseño de variables relevantes puede transformar datos estructurales simples en información estratégica **capaz de optimizar decisiones de valuación y predicción en el mercado inmobiliario.**

---

## Objetivos  
- Aplicar un flujo completo de **feature engineering** con datos simulados y reales.  
- Generar nuevas **features derivadas** y de **interacción** que representen comportamientos reales del mercado inmobiliario.  
- Analizar la **distribución, correlación e importancia** de las nuevas variables.  
- Evaluar el impacto predictivo de las features mediante métricas estadísticas y modelos de *machine learning*, validando los resultados con una muestra del dataset **Ames Housing**.

---
  
## Actividades 

1. **Set up y carga de datos**  
   - Configuración del entorno en Google Colab y carga de librerías (`pandas`, `numpy`, `matplotlib`, `seaborn`, `sklearn`).  
   - Creación de un **dataset sintético de viviendas** con atributos de superficie, precio, habitaciones, año y ubicación, simulando un escenario realista.  

2. **Creación de features derivadas**  
   - A partir de las variables base, se generaron transformaciones numéricas y logarítmicas:  
     - `price_per_sqft`, `log_price`, `sqft_per_bedroom`, `density`, `property_age`, `bed_bath_ratio`.  
   - Estas variables permitieron capturar proporciones, relaciones de escala y efectos de antigüedad en el valor del inmueble.  

3. **Análisis de distribución y correlaciones**  
   - Evaluación de las nuevas features mediante histogramas, boxplots y heatmaps.  
   - Identificación de correlaciones significativas entre eficiencia, densidad y edad (`efficiency_score` vs `density` = -0.42, `quality_indicator` vs `property_age` = -0.56).  
   - Visualización de relaciones *Precio–Superficie–Antigüedad* y *Precio–Distancia al centro*.  

4. **Evaluación de importancia de features**  
   - Aplicación de **Mutual Information** y **Random Forest Regressor** para medir la relevancia de cada variable.  
   - `log_price` y `price_per_sqft` se consolidaron como las más influyentes, seguidas por `density` y `sqft_per_bedroom`.  

5. **Investigación libre – Creación de features de dominio (Desafíos)**  
   **Desafío 1: Features de Dominio Inmobiliario**  
   - `space_efficiency`: relación superficie/lote → mide eficiencia del terreno.  
   - `crowded_property`: habitaciones cada 100 sqft → mide densidad interna.  
   - `advanced_location_score`: combina distancia, rating escolar y crimen → score de ubicación.  

   **Desafío 2: Features de Interacción**  
   - `price_age_interaction`: mide depreciación del precio por antigüedad.  
   - `new_large_property`: 1 si la propiedad es grande y nueva.  
   - `distance_school_interaction`: penaliza distancia y bajo rating escolar.  

   **Desafío 3: Evaluación de impacto**  
   - Correlaciones con el precio:  
     ```
     price_age_interaction           0.1633
     distance_school_interaction    -0.0489
     advanced_location_score        -0.0382
     space_efficiency               -0.0312
     crowded_property                0.0259
     new_large_property             -0.0008
     ```
   - Se comprobó que las features creadas aportan información adicional, especialmente las relacionadas con antigüedad y eficiencia.  

6. **Dataset de prueba – Ames Housing (validación final)**  
   Finalmente, se aplicó el pipeline de feature engineering a una muestra reducida del dataset real **Ames Housing**, verificando que las transformaciones mantuvieran coherencia y relevancia predictiva en un entorno real.

---

## Desarrollo  

El desarrollo se llevó a cabo de forma incremental, comenzando con la creación de un entorno controlado para experimentar con distintas estrategias de *feature engineering*.  
El código se estructuró en celdas secuenciales dentro de Google Colab, facilitando la trazabilidad de cada etapa del flujo de trabajo.  

Primero, se construyó un **dataset sintético** para aislar variables y probar transformaciones sin interferencias externas.  
Este enfoque permitió **validar el comportamiento de cada feature en condiciones controladas** antes de incorporar la complejidad de un dataset real.  

Sobre esta base se aplicaron operaciones matemáticas, logarítmicas y proporcionales para crear nuevas variables, priorizando aquellas que representaran relaciones interpretables entre los datos (eficiencia del espacio, densidad habitacional o relación entre antigüedad y precio).  

El análisis estadístico se complementó con visualizaciones generadas en `seaborn` y `matplotlib`, empleadas para inspeccionar distribuciones, correlaciones y presencia de valores atípicos.  
Los cálculos de *Mutual Information* y *Random Forest Feature Importance* se implementaron en `scikit-learn` para cuantificar la relevancia de cada variable y validar la contribución de las features derivadas.  

Finalmente, se abordaron los **Desafíos de creación de nuevas variables**, integrando conocimiento del dominio inmobiliario.  
Cada feature fue diseñada, testeada y evaluada de forma individual antes de incorporarse al conjunto final, consolidando un pipeline iterativo, escalable y consistente con los objetivos del caso.

---

## Evidencias

### Distribución logarítmica del precio  
![Distribución logarítmica del precio](../practica8/IMG_4228.png)  
La transformación logarítmica del precio reduce la asimetría de la distribución, generando una forma más cercana a la normal. Esto mejora la estabilidad de los modelos lineales y evita el sesgo hacia propiedades con precios extremos.


### Precio por m² según vecindario  
![Precio por m² según vecindario](../practica8/IMG_4229.png)  
Los vecindarios muestran diferencias marcadas en el precio por metro cuadrado. “NoRidge” y “Mitchel” presentan los valores más altos, lo que refleja la influencia del contexto geográfico sobre el valor de las viviendas.


### Distribuciones de nuevas features derivadas  
![Distribuciones de nuevas features derivadas](../practica8/IMG_4230.png)  
Las features derivadas como `space_efficiency`, `crowded_property` y `distance_school_interaction` presentan distribuciones asimétricas. Esto sugiere la presencia de propiedades extremas y la necesidad de escalado o transformación antes del modelado.

---

### Importancia de features  
![Importancia de features](../practica8/IMG_4231.png)  
Tanto la información mutua como el modelo Random Forest destacan `log_price` y `price_per_sqft` como las variables más influyentes. Esto valida su peso en la predicción y sugiere una relación no lineal con la variable objetivo.


### Correlaciones entre features derivadas  
![Correlaciones entre features derivadas](../practica8/IMG_4236.png)  
Se observa correlación moderada negativa entre `quality_indicator` y `property_age`, lo cual indica que las propiedades más antiguas tienden a tener menor calidad percibida. Las demás variables mantienen independencia relativa, útil para evitar multicolinealidad.


### Relación suavizada: Precio vs Distancia al centro  
![Relación suavizada: Precio vs Distancia al centro](../practica8/IMG_4238.png)  
Las viviendas nuevas muestran precios más altos en todas las distancias, mientras que las antiguas pierden valor conforme se alejan del centro urbano. Esta tendencia respalda la relevancia de la variable `distance_to_city` como factor de ubicación.

---

## Insights clave  

- El **feature engineering transforma datos básicos en conocimiento aplicable**, mejorando la capacidad predictiva y explicativa.  
- Las variables **de dominio** aportan valor añadido al incorporar aspectos contextuales (ubicación, antigüedad, eficiencia).  
- `log_price` y `price_per_sqft` se consolidaron como **indicadores robustos del valor real del inmueble**.  
- Las correlaciones entre edad, calidad y eficiencia refuerzan la relación entre modernización y valorización.  
- El proceso demostró que integrar razonamiento técnico y conocimiento de negocio **potencia la capacidad interpretativa de los modelos**.

---

## Reflexión
Esta práctica confirmó que el valor de los datos **no reside en su forma original, sino en cómo se transforman para revelar conocimiento útil**.  
El **feature engineering** se consolida como una de las etapas más críticas del flujo de ciencia de datos, donde confluyen **creatividad, rigurosidad estadística e interpretabilidad**.  

Diseñar nuevas variables con base en sentido del negocio y evidencia empírica permite **incrementar la capacidad predictiva de los modelos** sin sacrificar su transparencia.  
Asimismo, se evidenció que **un exceso de transformaciones puede inducir sobreajuste**, por lo que la selección de features debe fundamentarse en métricas objetivas como *mutual information* y *feature importance*.  

En síntesis, esta práctica permitió comprender que la ingeniería de atributos es tanto un arte como una ciencia: **convierte datos crudos en conocimiento accionable**, y refuerza que el verdadero valor de la ingeniería de datos radica en su capacidad para **convertir complejidad en claridad, y datos en decisiones.**

---

## Notebook en Google Colab
📓 El notebook completo con el desarrollo de esta práctica puede consultarse en el siguiente enlace:  
[Abrir notebook en Google Colab](https://colab.research.google.com/github/Agustina-Esquibel/Ingenieria-datos/blob/main/docs/UT3/practica8/UT3_Práctica_8.ipynb)

---

## 🔗 Referencias  
- [Feature Selection – Scikit-learn Documentation](https://scikit-learn.org/stable/modules/feature_selection.html)  
- [Feature Engineering for Machine Learning – O’Reilly](https://www.oreilly.com/library/view/hands-on-machine-learning/9781098125967/)  

---

## Navegación
⬅️ [Volver a Unidad Temática 2](../main.md)  
➡️ [Ir a Práctica 9](../practica9/main9.md)  
📓 [Índice del Portafolio](../../portfolio/index.md)
