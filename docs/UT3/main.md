# Unidad Temática 3 – Feature Engineering

En esta unidad se trabajaron las técnicas de **feature engineering** aplicadas al aprendizaje automático, con el objetivo de optimizar la representación de los datos y mejorar la capacidad predictiva de los modelos.  
Se abordaron enfoques para transformar, codificar, reducir y seleccionar características relevantes, integrando teoría y práctica en contextos de negocio reales.

---

### Prácticas realizadas

- [**Codificando significado: de variables categóricas a información útil**](./practica8/main8.md)  
  Se exploran Label, One-Hot y Target Encoding sobre *Adult Income*, comparando su impacto en la representación y en el rendimiento del modelo.

- [**Midiendo el impacto del encoding: performance y selección de variables**](./practica9/main9.md)  
  Evaluación comparativa de encoders, con visualizaciones de métricas y análisis de importancia de *features* para elegir la estrategia adecuada según cardinalidad y objetivo.

- [**Reduciendo la complejidad: PCA y selección de características con Ames Housing**](./practica10/main10.md)  
  Aplicación de PCA y métodos de *feature selection* para simplificar el modelo sin perder capacidad predictiva. Se analizan componentes, varianza explicada y *trade-offs*.

- [**Creando tiempo: ingeniería temporal de features con Pandas**](./practica11/main11.md)  
  Implementación de *lag features*, *rolling/expanding windows* y acumulados, capturando patrones secuenciales sin incurrir en *data leakage*, sobre datos transaccionales reales.

---

### Reflexión de la unidad

- **Codificando significado: de variables categóricas a información útil** permitió afianzar el manejo de variables categóricas y comprender cómo diferentes técnicas de *encoding* (Label, One-Hot y Target) afectan la representación de los datos y el desempeño de los modelos.  
- **Midiendo el impacto del encoding: performance y selección de variables** profundizó en la evaluación comparativa de encoders y la selección de características relevantes, fortaleciendo la interpretación de métricas y la toma de decisiones basada en evidencia.  
- **Reduciendo la complejidad: PCA y selección de características con Ames Housing** introdujo la reducción dimensional y la selección de *features* como herramientas para simplificar modelos sin pérdida sustantiva de información, analizando componentes principales, varianza explicada y *trade-offs* de rendimiento.  
- **Creando tiempo: ingeniería temporal de features con Pandas** extendió el análisis hacia datos secuenciales, aplicando *lags*, *rolling windows* y *expanding windows* para capturar dinámicas temporales, evitando *data leakage* y reforzando la comprensión del tiempo como variable predictiva clave.

En conjunto, la **UT3 consolidó la ingeniería de variables** como una etapa estratégica dentro del ciclo de *machine learning*, integrando codificación categórica, selección de variables, reducción dimensional y generación de *features* temporales en un flujo de trabajo ético, escalable y reproducible.

---

### Flujo de trabajo de UT3

Este esquema refleja cómo cada práctica aportó a un ciclo completo de transformación y análisis, desde la codificación de variables hasta la creación de *features* derivados y la documentación final.


---

### Conclusión final de UT3

La UT3 permitió consolidar una comprensión integral del feature engineering como etapa crítica dentro del proceso de *machine learning*.  
A través de las distintas prácticas, se integraron técnicas de codificación categórica, evaluación comparativa, reducción dimensional y creación de variables temporales, demostrando cómo la calidad y el diseño de las *features* determinan el rendimiento, la interpretabilidad y la escalabilidad de los modelos predictivos.
