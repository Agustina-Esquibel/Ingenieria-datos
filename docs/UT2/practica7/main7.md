---
title: Sesgo bajo la lupa — Detección, corrección y decisiones éticas con Fairlearn
date: 2025-09-24
---

## Contexto

Los modelos de aprendizaje automático aprenden patrones a partir de datos históricos, y cuando esos datos reflejan desigualdades estructurales, el modelo puede amplificarlas.  
La detección y corrección de sesgos se vuelve entonces una tarea esencial para garantizar el uso responsable de la inteligencia artificial.

En esta práctica se trabajó con dos casos de estudio complementarios:  

1. **Boston Housing (Regresión):** dataset eliminado de scikit-learn por contener una variable racial problemática que codifica la proporción de población afroamericana.  
2. **Titanic (Clasificación):** dataset donde las diferencias de supervivencia reproducen sesgos sociales basados en género y clase social.

El objetivo fue aplicar métodos de fairness mediante la librería **Fairlearn**, para detectar, medir y mitigar sesgos, evaluando tanto el impacto técnico como las implicancias éticas.

---

## Objetivos

- Detectar la presencia de sesgos en modelos predictivos basados en datos reales.  
- Analizar cómo las variables sensibles afectan la equidad del modelo.  
- Implementar estrategias de corrección de sesgo y evaluar su impacto en rendimiento.  
- Comprender el equilibrio entre precisión, equidad y responsabilidad profesional.  
- Reflexionar sobre las decisiones éticas involucradas en el desarrollo de modelos.

---

## Desarrollo

1. **Carga y exploración de datasets.**  
   Se cargaron los conjuntos de datos *Boston Housing* y *Titanic*.  
   En el caso de Boston, se reconstruyó la variable racial `Bk_racial` a partir de la fórmula original eliminada de la versión actual de scikit-learn.  
   En Titanic, se prepararon las variables numéricas y se eliminaron valores faltantes en edad y puerto de embarque.

2. **Análisis del sesgo.**  
   En Boston se calculó la correlación entre la variable racial y el precio medio de las viviendas (`MEDV`).  
   En Titanic se calcularon las tasas de supervivencia por género y clase, confirmando una diferencia significativa a favor de las mujeres y los pasajeros de primera clase.

3. **Entrenamiento de modelos base.**  
   - Para Boston, se utilizó **regresión lineal** incluyendo y excluyendo la variable racial.  
   - Para Titanic, se aplicó un **Random Forest** sin restricciones de equidad como modelo baseline.  

4. **Aplicación de Fairlearn.**  
   En el caso Titanic, se utilizó el método **ExponentiatedGradient** con la restricción de *Demographic Parity*.  
   Se entrenó un modelo ajustado que buscó equilibrar las tasas de predicción positiva entre hombres y mujeres.

5. **Evaluación y comparación.**  
   Se compararon los resultados de precisión y de equidad antes y después de aplicar la corrección, cuantificando la pérdida de rendimiento y la ganancia en justicia algorítmica.

---

## Evidencias


### Disparidad entre géneros – Antes vs Después de Fairlearn
![Disparidad entre géneros – Antes vs Después de Fairlearn](Fairlearn.png)

**Observación técnica:**  
El gráfico muestra una reducción clara en la diferencia de paridad demográfica tras aplicar Fairlearn.  
El modelo baseline presenta una disparidad cercana a 0.11, mientras que el modelo ajustado con mitigación cae a aproximadamente 0.06.

**Interpretación analítica:**  
La intervención reduce la brecha de predicción entre géneros, disminuyendo el sesgo en la tasa de supervivencia predicha para hombres y mujeres.  

**Reflexión metodológica:**  
La mitigación de sesgos con Fairlearn logra una mejora significativa en equidad sin modificar el dataset original, demostrando que la corrección algorítmica puede ser efectiva incluso en etapas posteriores del pipeline.

---

### Tasa predicha de supervivencia por género
![Tasa predicha de supervivencia por género](Tasa_predicha.png)

**Observación técnica:**  
El modelo baseline predice una mayor tasa de supervivencia para mujeres (≈0.45) que para hombres (≈0.35).  
Tras aplicar Fairlearn, las tasas convergen hacia valores similares (≈0.27 para ambos).  

**Interpretación analítica:**  
El ajuste del modelo reduce la diferencia entre géneros sin eliminar por completo la variabilidad natural de los datos.  
Esto sugiere que la mitigación logra balancear las probabilidades sin sacrificar el comportamiento estructural del dataset.  

**Reflexión metodológica:**  
Fairlearn no busca igualar forzosamente los resultados, sino disminuir las diferencias no justificadas por factores explicativos válidos.

---

### Trade-off entre rendimiento y equidad
![Trade-off entre rendimiento y equidad](Rendimiento_equidad.png)

**Observación técnica:**  
Se observa un descenso moderado del accuracy tras aplicar Fairlearn (de ~68% a ~64%), mientras que la disparidad demográfica se reduce casi a la mitad.  

**Interpretación analítica:**  
Este comportamiento confirma el clásico compromiso entre precisión y justicia: mejorar la equidad puede implicar una leve pérdida de rendimiento global.  

**Reflexión metodológica:**  
El objetivo no es maximizar una métrica aislada, sino lograr un balance ético entre desempeño predictivo y tratamiento justo hacia los distintos grupos.

---

### Distribución de precios por grupo racial
![Distribución de precios por grupo racial](Boxplot.png)

**Observación técnica:**  
Las viviendas en áreas con alta proporción de población afroamericana presentan precios promedio más bajos y mayor dispersión.  
El boxplot y los histogramas refuerzan esta diferencia estructural.  

**Interpretación analítica:**  
La disparidad no necesariamente implica discriminación directa, pero revela desigualdad subyacente en los datos, que puede trasladarse a los modelos si no se controla.  

**Reflexión metodológica:**  
El análisis previo a la modelización permite identificar posibles fuentes de sesgo estructural.  
Mitigar o compensar estas diferencias debe ser parte del diseño ético de cualquier pipeline de aprendizaje automático.

---

## Insights clave

1. Los modelos precisos pueden ser injustos si no se analizan métricas de equidad.  
2. Las variables sensibles no deben eliminarse sin antes medir su efecto en el sesgo.  
3. El contexto define la tolerancia ética al sesgo: en ámbitos sociales, la equidad es prioritaria.  
4. Fairlearn permite cuantificar y mitigar desigualdades de manera controlada y reproducible.  
5. Rendimiento y equidad no son opuestos: con un diseño ético, pueden coexistir.

---

## Reflexión

El caso **Boston Housing** muestra cómo el uso de variables sensibles puede introducir discriminaciones históricas en un modelo.  
Aunque la variable `B` mejora el ajuste, representa información que perpetúa desigualdades.  
Excluirla de los modelos de producción es una decisión ética necesaria, aun cuando implique una leve pérdida de rendimiento.

El caso **Titanic** evidencia cómo los sesgos de contexto (género, clase) pueden afectar la imparcialidad de los resultados.  
La corrección mediante *Fairlearn* demostró que es posible alcanzar un modelo más equilibrado, validando la importancia de incluir métricas de equidad en el proceso de modelado.

Ambos ejercicios llevan a una conclusión central: **no existe neutralidad algorítmica**.  
Los modelos reproducen los valores y estructuras de quienes los construyen.  
Por ello, la ética no es un complemento del proceso técnico, sino un requisito esencial para garantizar la validez y la justicia de los sistemas basados en datos.

---

## Notebook en Google Colab

📓 El notebook completo con el desarrollo de esta práctica puede consultarse en el siguiente enlace:

🔗 [Abrir en Google Colab](https://colab.research.google.com/github/Agustina-Esquibel/Ingenieria-datos/blob/main/docs/UT2/practica7/UT2_practica7.ipynb)


---

## Referencias

- Fairlearn Documentation (Microsoft Research).  
- Scikit-learn: *Model Evaluation and Ethics in Machine Learning*.  
- CMU Boston Housing Dataset (1978).  
- Titanic Dataset (Kaggle / Seaborn).  

---

## Navegación

[⬅️ Volver a Práctica 6 — Feature Scaling y Anti-Leakage Pipeline](../practica6/main6.md)  
[⬅️ Volver a UT2](../main.md)  
[📓 Índice del Portafolio](../../portfolio/index.md)
