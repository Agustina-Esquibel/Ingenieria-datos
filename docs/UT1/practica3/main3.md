---
title: "UT1 · Práctica 3 — Exploración del dataset Netflix"
date: 2025-08-20
---

# UT1 · Práctica 3 — EDA Netflix con Visualizaciones

## Contexto
El dataset de Netflix contiene información sobre más de 6.000 títulos entre películas y series, con variables como tipo de contenido, país, director, elenco, año de lanzamiento, fecha de incorporación, duración, clasificación y géneros.  
Este conjunto de datos es ampliamente utilizado para prácticas de análisis exploratorio de datos (EDA) porque refleja un escenario **realista**: datos incompletos, categorías heterogéneas y variables que requieren limpieza antes del análisis.

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

Este dashboard resume los principales hallazgos:  
- Predominio de películas sobre series.  
- Aceleración de estrenos a partir de 2010.  
- Concentración en Estados Unidos e India.  
- Géneros y ratings distribuidos de forma heterogénea.  

## Insights clave
1. El 68% del contenido corresponde a películas, frente al 32% de series.  
2. La mayor cantidad de títulos proviene de Estados Unidos e India.  
3. El crecimiento en lanzamientos se intensificó después de 2010, alcanzando un pico en 2018.  
4. Los ratings más frecuentes son **TV-MA** y **TV-14**, lo que refleja un foco en público adolescente/adulto.  
5. Existen variables con gran proporción de datos faltantes, especialmente en *director* y *cast*, lo que limita ciertos análisis.  

## Reflexión
Esta práctica permitió aplicar un flujo completo de análisis exploratorio: carga, limpieza, visualización y síntesis en un dashboard.  
Lo desafiante fue trabajar con un **dataset real**, con valores faltantes y categorías inconsistentes, lo que me obligó a tomar decisiones de limpieza y a reflexionar sobre cómo estas afectan los resultados.  

El caso de Netflix muestra la importancia de:  
- Detectar y documentar patrones de calidad de datos.  
- Seleccionar visualizaciones adecuadas para responder preguntas de negocio.  
- Integrar hallazgos en un formato comprensible y reproducible.  

Este aprendizaje es fundamental para futuros proyectos, donde la reproducibilidad y la claridad en la comunicación de insights son tan relevantes como el análisis técnico.  

## Notebook en Google Colab
📓 El notebook completo con el desarrollo de esta práctica puede consultarse en el siguiente enlace:  

## Referencias
- [Dataset en Kaggle](https://www.kaggle.com/shivamb/netflix-shows)  
- [Documentación Pandas](https://pandas.pydata.org/)  
- [Documentación Seaborn](https://seaborn.pydata.org/)  

## Navegación
🔙 [Volver a Unidad Temática 1](../main.md)  
➡️ [Ir a Práctica 4 – Dataset Taxis NYC](../practica4/main4.md)  
🔝 [Índice del Portafolio](../../portfolio/index.md)
