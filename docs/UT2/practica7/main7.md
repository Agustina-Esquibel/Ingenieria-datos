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

### Brecha racial en Boston Housing

La visualización muestra la diferencia promedio de precios entre zonas con alta y baja proporción afroamericana.  
Los resultados indican una **brecha de aproximadamente 8.500 dólares**, equivalente al **18 % del valor medio de las viviendas**.  
Esto evidencia un sesgo estructural histórico en el dataset, que se traslada directamente al modelo de regresión si la variable racial es incluida.

---

### Distribución de precios por grupo racial

El histograma y boxplot comparan las distribuciones de precios de los dos grupos.  
Se observa que las zonas con mayor proporción afroamericana presentan precios más bajos y menor variabilidad, mientras que las demás zonas exhiben precios medios y dispersiones superiores.  
Esta desigualdad se traduce en predicciones sistemáticamente más bajas para ciertos grupos poblacionales.

---

### Sesgo de género en el modelo Titanic (baseline)

El gráfico muestra la tasa de supervivencia predicha por género en el modelo baseline.  
Las mujeres presentan una probabilidad de supervivencia un **33 % mayor** que los hombres.  
Aunque este resultado refleja la realidad del hecho histórico, en términos algorítmicos representa un **sesgo de clasificación injusto** que favorece a un grupo.

---

### Modelo corregido con Fairlearn

Tras aplicar el método **ExponentiatedGradient**, la disparidad entre géneros se reduce considerablemente.  
El *Demographic Parity Difference* pasa de **0.27 a 0.10**, mientras que la pérdida de rendimiento (accuracy) fue mínima, pasando de **0.79 a 0.76**.  
La visualización comparativa confirma una distribución más balanceada de predicciones entre hombres y mujeres.

---

### Trade-off entre rendimiento y equidad

El gráfico de trade-off muestra el equilibrio logrado entre precisión y justicia.  
El modelo justo perdió un **3,8 % de rendimiento**, pero mejoró la equidad en **0.17 puntos**, logrando un compromiso óptimo.  
El resultado respalda la idea de que es posible **reducir sesgos sin comprometer en exceso la capacidad predictiva**.

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


---

## Referencias

- Fairlearn Documentation (Microsoft Research).  
- Scikit-learn: *Model Evaluation and Ethics in Machine Learning*.  
- CMU Boston Housing Dataset (1978).  
- Titanic Dataset (Kaggle / Seaborn).  

---

## Navegación
