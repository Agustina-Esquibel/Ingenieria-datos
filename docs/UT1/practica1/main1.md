---
title: "Explorando el Iris Dataset: patrones florales y variables predictivas"
date: 2025-08-13
---

# Explorando el Iris Dataset: patrones florales y variables predictivas

## Contexto
El dataset **Iris** es un clásico de la ciencia de datos y el aprendizaje automático.  
Incluye 150 registros con medidas de sépalos y pétalos de tres especies: *Setosa, Versicolor y Virginica*.  
Su simplicidad y limpieza lo convierten en un punto de partida ideal para aplicar técnicas de análisis exploratorio de datos (EDA), practicar visualizaciones y documentar un flujo de análisis reproducible.

## Objetivos
- Conocer la estructura y balance del dataset.  
- Generar estadísticas descriptivas y visualizaciones iniciales.  
- Identificar correlaciones y variables clave para clasificación.  
- Practicar un flujo reproducible de análisis con Google Colab.  

## Actividades
- Configuración del entorno en **Google Colab** e instalación de librerías necesarias.  
- Carga de datos desde distintas fuentes (Seaborn, scikit-learn, Kaggle API, CSV manual).  
- Revisión inicial: dimensiones, tipos de datos, primeras filas y valores faltantes.  
- Construcción de un diccionario de datos.  
- Chequeo de duplicados e imbalance de clases.  
- Análisis descriptivo y correlaciones.  
- Redacción de insights accionables.  
- Documentación del flujo y guardado de resultados en directorios.  

## Desarrollo
El análisis se llevó a cabo en **Google Colab**, lo que permitió trabajar en un entorno reproducible y con la opción de guardar visualizaciones y reportes en Google Drive.  
Se inició creando un notebook en Python 3, instalando y verificando las versiones de *Pandas, Seaborn y Matplotlib*.  

### Carga y verificación de datos
Se exploraron distintas formas de cargar el dataset:  
- Con `seaborn.load_dataset("iris")`.  
- Desde la librería **scikit-learn** (`datasets.load_iris`).  
- A través de la **Kaggle API**.  
- Mediante lectura de un CSV local o desde una URL pública.  

Todas las opciones produjeron la misma estructura de datos, confirmando que la fuente no altera el contenido, aunque sí el formato de salida.  
Para el análisis principal se utilizó la carga desde **Seaborn**, por su simplicidad y consistencia.  

Los primeros chequeos (`df.shape`, `df.dtypes`, `df.head()`) confirmaron que:  
- El dataset contenía 150 registros y 5 columnas.  
- No había valores faltantes (`df.isna().sum() == 0`).  
- No existían registros duplicados.  
- Cada clase de la variable `species` tenía exactamente 50 registros, garantizando balance.  

### Análisis descriptivo
Con `df.describe()` se calcularon estadísticos básicos. Se observó que las variables de pétalos presentaban rangos más amplios y mayor poder discriminante que las de sépalos, sugiriendo que serían más útiles para clasificación.  

### Análisis de correlaciones
La matriz de correlación (`df.corr()`) mostró una relación positiva muy fuerte (~0.96) entre `petal_length` y `petal_width`.  
Este hallazgo sirvió para profundizar luego con visualizaciones específicas.  

### Documentación y reproducibilidad
Todos los resultados (estadísticos, diccionario de datos y visualizaciones) se guardaron en directorios específicos dentro del notebook.  
Este flujo organizado asegura trazabilidad y reproducibilidad, siguiendo buenas prácticas de ciencia de datos.

## Evidencias
### Diccionario de datos
| Variable        | Tipo    | Unidad | Descripción                 |
|-----------------|--------|--------|-----------------------------|
| sepal_length    | float  | cm     | Longitud del sépalo         |
| sepal_width     | float  | cm     | Ancho del sépalo            |
| petal_length    | float  | cm     | Longitud del pétalo         |
| petal_width     | float  | cm     | Ancho del pétalo            |
| species         | string | -      | Especie de la flor (*Setosa, Versicolor, Virginica*) |

### Heatmap
El heatmap confirma una correlación muy fuerte (~0.96) entre el largo y el ancho de los pétalos, lo que indica que ambas variables aportan información muy similar en un análisis predictivo.  
![](../../assets/heatmap.png)

### Pairplot
El pairplot muestra cómo **Setosa** se separa claramente de las demás especies en variables de pétalos, mientras que **Versicolor** y **Virginica** presentan mayor solapamiento, lo que anticipa dificultades de clasificación lineal entre ambas.  
![](../../assets/Pairplot.png)

### Boxplot
El boxplot refleja que **Setosa** tiene pétalos consistentemente más pequeños, mientras que **Virginica** concentra los valores más altos, confirmando que la longitud y ancho de pétalos son las variables más discriminantes.  
![](../../assets/Box_petal_length.png)

## Insights clave
1. **Setosa** se diferencia netamente de las otras dos especies en las medidas de pétalos.  
2. Existe una correlación de ~0.96 entre `petal_length` y `petal_width`.  
3. El dataset está perfectamente balanceado (50 registros por especie).  
4. **Versicolor** y **Virginica** muestran zonas de solapamiento que podrían dificultar la clasificación.  
5. Las variables de pétalos son más discriminantes que las de sépalos para separar especies.  

## Reflexión
Esta práctica me permitió aplicar un flujo completo de análisis exploratorio: cargar datos, describirlos, visualizarlos y extraer insights.  
Los resultados mostraron la importancia de identificar variables discriminantes antes de aplicar algoritmos de clasificación.  

Un aprendizaje importante fue comprobar cómo distintas librerías ofrecen varias formas de cargar el mismo dataset. Esto refuerza la necesidad de documentar claramente la fuente utilizada, ya que la trazabilidad del origen de los datos es fundamental para la reproducibilidad de los proyectos.  

El ejercicio me mostró la ventaja de documentar cada paso en un entorno reproducible (Colab + GitHub), reforzando la idea de que la calidad del análisis depende tanto de la limpieza del código como de la claridad en la comunicación de resultados.  

Un aspecto crítico es que, al tratarse de un dataset pequeño y balanceado, el análisis fue sencillo y directo. Sin embargo, esto también es una limitación: no refleja la complejidad de datos reales con outliers, ruido o desbalance severo. Este contraste lo convierte en un excelente punto de partida, pero también en un recordatorio de que los siguientes desafíos requerirán mayor profundidad analítica.  

## Notebook en Google Colab
📓 El notebook completo con el desarrollo de esta práctica puede consultarse en el siguiente enlace:  
[🔗 Abrir en Google Colab](https://colab.research.google.com/github/agustina-esquibel/Ingenieria-datos/blob/main/docs/UT1/practica1/practica1_agustina_esquibel.ipynb)

## Referencias
- [Iris Dataset (UCI)](https://archive.ics.uci.edu/dataset/53/iris)  
- [Iris Dataset (Kaggle)](https://www.kaggle.com/datasets/uciml/iris)  

## Navegación
🔙 [Volver a Unidad Temática 1](../main.md)  
➡️ [Ir a Práctica 2 – Configuración del portafolio](../practica2/main2.md)  
🔝 [Índice del Portafolio](../../portfolio/index.md)  
