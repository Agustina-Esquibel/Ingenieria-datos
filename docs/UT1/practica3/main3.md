---
title: "Explorando el catálogo de Netflix: tendencias globales y patrones de contenido audiovisual"
date: 2025-08-20
---

## Contexto
El dataset de Netflix contiene información sobre más de 6.000 títulos entre películas y series, con variables como tipo de contenido, país, director, elenco, año de lanzamiento, fecha de incorporación, duración, clasificación y géneros.  
Este conjunto de datos es ampliamente utilizado para prácticas de análisis exploratorio de datos (EDA) porque refleja un escenario **realista**: datos incompletos, categorías heterogéneas y variables que requieren limpieza antes del análisis.
El objetivo del análisis es comprender la evolución del catálogo y los patrones de producción y consumo dentro de la plataforma.

## Objetivos
- Explorar la estructura y calidad del dataset.  
- Identificar valores faltantes y patrones de datos incompletos.  
- Analizar tendencias en lanzamientos y distribución de contenido.  
- Visualizar características clave mediante gráficos y un dashboard integrador.  

## Actividades
- Carga y exploración inicial del dataset (`shape`, `head`, `info`, `describe`).  
- Análisis de valores faltantes y creación de visualizaciones específicas.  
- Generación de gráficos descriptivos:  
  - Distribución de *Movies* vs *TV Shows*.  
  - Evolución temporal de títulos lanzados.  
  - Ratings por tipo de contenido.  
  - Principales países productores.  
- Creación de un dashboard final integrador con hallazgos.  

## Desarrollo
Los datos se cargaron desde un archivo CSV (`netflix_titles.csv`) en Google Colab.  
Se realizó una limpieza básica: ajuste de fechas, homogenización de países y detección de valores faltantes en **director**, **cast** y **country**, que representaron las columnas con mayor nivel de incompletitud.  

Luego se analizaron estadísticas generales y se generaron visualizaciones que mostraron:  
- La proporción de *Movies* vs *TV Shows*.  
- El crecimiento de estrenos a lo largo de los años, con un incremento sostenido después de 2010 y un pico en 2018.  
- La concentración de producción en unos pocos países, con Estados Unidos e India liderando.  
- Los ratings más frecuentes (TV-MA y TV-14), representativos de la orientación de la plataforma hacia público adolescente y adulto.  

Finalmente, los gráficos se integraron en un **dashboard único** para facilitar la interpretación global del análisis.

## Evidencias
![](../../assets/p2_dashboard.png)

### Distribución de Movies vs TV Shows
El gráfico circular evidencia el claro predominio de películas (alrededor del 68%) frente a series (32%) dentro del catálogo.  
Esta diferencia refleja el enfoque original de Netflix como distribuidor de películas antes de su expansión hacia producciones seriadas, destacando una estrategia centrada en el contenido cinematográfico.

### Evolución temporal de títulos lanzados
La serie temporal muestra un crecimiento sostenido en la cantidad de estrenos a partir de 2010, con un pico cercano a 2018.  
Este incremento coincide con la consolidación del streaming como formato dominante y la inversión de Netflix en producciones originales, lo que sugiere una etapa de fuerte expansión global.

### Top 10 de países productores
El gráfico de barras confirma que Estados Unidos e India son los mayores productores dentro del catálogo, seguidos por Reino Unido y Canadá.  
Esta concentración geográfica indica una fuerte presencia angloparlante y una diversificación incipiente hacia mercados asiáticos, en línea con la internacionalización de la plataforma.

### Ratings por tipo de contenido
El gráfico de barras agrupadas evidencia que los ratings más frecuentes son **TV-MA** y **TV-14**, correspondientes a contenido para público adolescente y adulto.  
Esto muestra la orientación predominante de Netflix hacia audiencias maduras, con menor proporción de títulos familiares o infantiles.

### Evolución por década y tipo de contenido (heatmap)
El mapa de calor sintetiza la evolución histórica del catálogo: a partir de 2010 se observa un salto en la producción, sobre todo en películas.  
Las décadas anteriores presentan menor densidad, lo que refuerza la idea de un crecimiento reciente impulsado por el modelo digital.  
El patrón destaca cómo la disponibilidad de títulos aumenta drásticamente en los últimos años, con una expansión sostenida en diversidad temática.

### Síntesis del dashboard
El dashboard integrador permite observar de forma global las dinámicas principales del catálogo de Netflix:  
un claro predominio de películas, una expansión sostenida de estrenos en la última década, la concentración geográfica en pocos países y una orientación hacia contenidos maduros.  
Estos hallazgos reflejan cómo la evolución del streaming transformó el perfil de la oferta audiovisual, combinando volumen, diversidad y segmentación de audiencias.

## Insights clave
1. El 68% del contenido corresponde a películas, frente al 32% de series.  
2. La mayor cantidad de títulos proviene de Estados Unidos e India.  
3. El crecimiento en lanzamientos se intensificó después de 2010, alcanzando un pico en 2018.  
4. Los ratings más frecuentes son **TV-MA** y **TV-14**, lo que refleja un foco en público adolescente/adulto.  
5. Existen variables con gran proporción de datos faltantes, especialmente en *director* y *cast*, lo que limita ciertos análisis.  

## Reflexión
Esta práctica permitió aplicar un flujo completo de análisis exploratorio, incluyendo carga, limpieza, visualización y síntesis mediante un dashboard
Lo desafiante fue trabajar con un **dataset real**, con valores faltantes y categorías inconsistentes, lo que  obligó a tomar decisiones de limpieza y a reflexionar sobre cómo estas afectan los resultados.  

El caso de Netflix muestra la importancia de:  
- Detectar y documentar patrones de calidad de datos.  
- Seleccionar visualizaciones adecuadas para responder preguntas de negocio.  
- Integrar hallazgos en un formato comprensible y reproducible.  

Este aprendizaje es fundamental para futuros proyectos, donde la reproducibilidad y la claridad en la comunicación de insights son tan relevantes como el análisis técnico.  

## Notebook en Google Colab
📓 El notebook completo con el desarrollo de esta práctica puede consultarse en el siguiente enlace:  
[🔗 Abrir en Google Colab](https://colab.research.google.com/github/agustina-esquibel/Ingenieria-datos/blob/main/docs/UT1/practica3/Agustina_Esquibel_practico3.ipynb)


## Referencias
- [Dataset en Kaggle](https://www.kaggle.com/shivamb/netflix-shows)  
- [Documentación Pandas](https://pandas.pydata.org/)  
- [Documentación Seaborn](https://seaborn.pydata.org/)  

## Navegación
⬅️ [Volver a Unidad Temática 1](../main.md)  
➡️ [Ir a Práctica 4 – Dataset Taxis NYC](../practica4/main4.md)  
📓[Índice del Portafolio](../../portfolio/index.md)
