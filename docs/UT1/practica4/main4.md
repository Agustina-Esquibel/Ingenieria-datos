---
title: "UT1 · Práctica 4 — EDA Multifuentes y Joins"
date: 2025-08-27
---

# UT1 · Práctica 4 — EDA Multi-fuentes y Joins

## Contexto
En esta práctica se trabajó con múltiples fuentes de datos (viajes, zonas y calendario de eventos) aplicando procesos de integración.  
El objetivo principal fue comprender cómo los distintos tipos de *joins* permiten enriquecer los datos y facilitar un análisis posterior más profundo.

## Objetivos
- Integrar datasets provenientes de diferentes formatos (CSV, Parquet, JSON).  
- Normalizar columnas y preparar los datos para *joins*.  
- Aplicar **LEFT JOIN** e **INNER JOIN** y analizar sus diferencias.  
- Comparar métricas entre días normales y días especiales.  
- Generar insights accionables a partir de datos integrados.  

## Actividades
1. Carga de datasets de viajes, zonas y calendario.  
2. Normalización de nombres de columnas y fechas.  
3. Aplicación de **LEFT JOIN** de viajes con zonas para asignar boroughs.  
4. Integración con calendario y creación de la variable `is_special_day`.  
5. Análisis comparativo de viajes en días normales vs días especiales.  
6. Cálculo de métricas clave: cantidad de viajes, distancias y tarifas.  
7. Reflexión crítica sobre la utilidad de los *joins* y la integración multifuente.  

## Desarrollo
El trabajo permitió poner en práctica técnicas de unión de datasets en *pandas*.  
Se verificó que el uso de **LEFT JOIN** garantiza mantener la totalidad de los registros originales, incluso si faltan coincidencias en la tabla de referencia. En contraste, el **INNER JOIN** reduce el universo de análisis, preservando solo las filas con coincidencia exacta.  

La incorporación de información contextual (zonas y días especiales) aportó una visión más rica que la obtenida con un dataset aislado. Esto permitió construir indicadores agregados por borough y comparar la demanda en días normales frente a días especiales.  

Además, se aplicaron cálculos de eficiencia y optimización de memoria para manejar la gran cantidad de registros, demostrando la importancia de preparar los datos antes de los *joins*.  

## Evidencias
- ✅ Se procesaron y unificaron datos de viajes con sus zonas geográficas (asignación de boroughs).  
- ✅ Se integró el calendario de eventos y se creó la bandera `is_special_day` para el análisis comparativo.  
- 📊 Se calcularon métricas consolidadas: total de registros, distancia promedio y tarifa promedio.  
- 🏙️ Se identificaron los boroughs con mayor volumen de viajes (Manhattan, Queens y Brooklyn).  
- 📈 Se verificó el impacto de los días especiales en la demanda frente a los días normales.  

## Insights clave
1. El **LEFT JOIN** fue clave para no perder viajes sin correspondencia en zonas, preservando el universo completo de análisis.  
2. La integración con el calendario permitió detectar variaciones de demanda en días especiales, invisibles con un dataset aislado.  
3. Los boroughs presentan distribuciones desiguales de viajes, lo que sugiere patrones de movilidad distintos según la zona.  
4. La combinación de múltiples fuentes mejora la calidad de los indicadores (ej. métricas por borough y por tipo de día).  
5. La elección del tipo de *join* no es trivial: influye directamente en el alcance y la interpretación de los resultados.  

## Reflexión
Esta práctica refuerza la importancia de la **integración de datos** como paso previo a cualquier análisis serio.  
Trabajar con múltiples fuentes permitió construir indicadores más representativos y detectar patrones que no emergen con datasets aislados.  

El contraste entre **LEFT JOIN** e **INNER JOIN** mostró cómo una decisión técnica puede modificar los resultados: el primero conserva información completa aunque con nulos, mientras que el segundo es más restrictivo pero asegura consistencia.  

En conclusión, integrar datos y reflexionar críticamente sobre la estrategia de unión no solo mejora los resultados inmediatos, sino que sienta bases sólidas para análisis más avanzados en proyectos reales.  

## Notebook en Google Colab
📓 El notebook completo con el desarrollo de esta práctica puede consultarse en el siguiente enlace:  

## Referencias
- [NYC Taxi Dataset](https://www1.nyc.gov)  
- [NYC Taxi Zones](https://www1.nyc.gov)  
- [Documentación `pandas.merge`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.merge.html)  

## Navegación
🔙 [Volver a Unidad Temática 1](../main.md)  
🔝 [Índice del Portafolio](../../portfolio/index.md)
