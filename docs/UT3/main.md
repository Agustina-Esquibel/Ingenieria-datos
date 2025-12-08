# Unidad Temática 3 – Feature Engineering

En esta unidad se trabajaron las técnicas de **feature engineering** aplicadas al aprendizaje automático, con el objetivo de optimizar la representación de los datos y mejorar la capacidad predictiva de los modelos.  
Se abordaron enfoques para transformar, codificar, reducir y seleccionar características relevantes, integrando teoría y práctica en contextos de negocio reales.

---

## Prácticas realizadas

- [**Diseñando el valor oculto: cómo el feature engineering mejora la predicción de precios de vivienda**](./practica8/main8.md)  
  *Creación de features derivadas, transformaciones logarítmicas y variables de interacción aplicadas a un caso inmobiliario con datos sintéticos y Ames Housing.*

- [**Codificando la realidad: cómo el encoding categórico mejora la predicción de ingresos en datos del censo**](./practica9/main9.md)  
  *Comparación de técnicas de encoding categórico y su impacto en el rendimiento de modelos supervisados.*

- [**Reduciendo el ruido: cómo PCA y Feature Selection revelan las variables clave del valor inmobiliario**](./practica10/main10.md)  
  *Aplicación de PCA y métodos de selección de características para identificar factores relevantes y eliminar redundancias.*

- [**Modelando el tiempo: cómo el feature engineering temporal anticipa la recompra en e-commerce**](./practica11/main11.md)  
  *Implementación de lag features, rolling windows, expanding windows, RFM, calendar features y validación temporal con TimeSeriesSplit evitando data leakage.*

- [**Caso Retail Churn: cómo el feature engineering anticipa el abandono de clientes**](../UT3/extraUT3/extra3.md)  
Caso aplicado donde se construyen features de comportamiento (RFM, engagement, codificación categórica avanzada y PCA) para identificar señales tempranas de abandono y mejorar la capacidad interpretativa del modelo.  


## Reflexión de la unidad

- La creación de **features derivadas e interacciones** mostró cómo relaciones no evidentes pueden aportar más valor que las variables originales.  
- La **codificación categórica** confirmó su importancia en modelos sensibles a la representación de categorías.  

- La **reducción dimensional** facilitó interpretabilidad y redujo ruido en datos con alta correlación.  
- El **feature engineering temporal** reveló patrones secuenciales de comportamiento fundamentales en series de tiempo y análisis de usuarios.  
- La unidad reforzó que el rendimiento de un modelo depende en gran medida de la calidad y diseño de sus *features*, más que del algoritmo utilizado.

- **Retail Churn** profundizó la importancia del feature engineering como núcleo del análisis predictivo: la construcción de variables basadas en comportamiento real permitió detectar patrones de abandono imposibles de observar con los datos originales.


## Flujo de trabajo de UT3

![](./IMG_4605.jpeg)

Este esquema refleja las etapas clave del feature engineering: partir de los datos base, generar transformaciones, codificar variables, aplicar reducción o selección y obtener un conjunto final de features listo para modelado.


## Conclusión final de UT3

La UT3 permitió consolidar una comprensión integral del feature engineering como etapa crítica dentro del proceso de *machine learning*.  
A través de las distintas prácticas, se integraron técnicas de codificación categórica, evaluación comparativa, reducción dimensional y creación de variables temporales, demostrando cómo la calidad y el diseño de las *features* determinan el rendimiento, la interpretabilidad y la escalabilidad de los modelos predictivos.

El aprendizaje obtenido en esta unidad refuerza que el valor real de un modelo surge de **cómo se construyen las variables**, combinando conocimiento técnico, razonamiento estadístico y comprensión del dominio del problema.

---

📓 [Índice del portafolio](../portfolio/index.md)
