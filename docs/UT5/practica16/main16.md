---
title: "DataPrep: limpieza visual de datos orientada a pipeline"
date: 2025-12-07
---

## Contexto
Esta práctica corresponde al lab *"Cleaning Data with Dataprep"* de Google Cloud Skills.  
El objetivo principal es introducir al estudiante al uso de **Cloud Dataprep (Trifacta)**, una herramienta visual diseñada para **perfilar, limpiar, transformar y preparar datos** sin necesidad de escribir código, generando flujos reproducibles ideales para pipelines ETL/ELT.

Dataprep combina automatización inteligente, recomendaciones guiadas y ejecución escalable sobre Google Cloud, convirtiéndose en una herramienta clave dentro de procesos modernos de **DataOps**.

---

## Objetivos
- Comprender cómo funciona la **interfaz visual de Dataprep** para explorar, perfilar y transformar datos.  
- Aplicar operaciones esenciales de limpieza: detección de valores faltantes, división de columnas, extracción de patrones, normalización y combinación.  
- Crear un **workflow reproducible**, donde cada paso se registra como parte de un pipeline.  
- Ejecutar el job final para producir datos limpios, exportándolos a Cloud Storage o BigQuery.  
- Conocer buenas prácticas de preparación de datos antes de integrarlos en pipelines automatizados.

---

## Desarrollo

### 1. Inicio del entorno y carga del dataset
El estudiante inició el laboratorio en Google Cloud Skills, accediendo a Cloud Dataprep desde la consola.  
Luego:

- Se importó un archivo CSV desde Cloud Storage.  
- Dataprep generó automáticamente un **perfil de datos** que incluye tipos, valores faltantes, distribuciones y patrones.

Esta exploración inicial permitió identificar problemas comunes como formatos inconsistentes, columnas mal tipadas o datos incompletos.

---

### 2. Perfilado y evaluación de la calidad del dato
Dataprep mostró visualmente:

- Distribuciones por columna  
- Valores atípicos  
- Errores de formato  
- Frecuencias de categorías  
- Indicadores de completitud  

El estudiante identificó qué variables requerían limpieza y qué transformaciones mejorarían la coherencia del dataset.

---

### 3. Transformaciones de limpieza
Se aplicaron múltiples transformaciones guiadas:

- **Split** de columnas por delimitadores.  
- **Regex** para extraer subcadenas.  
- **Replace** para corregir valores inválidos o inconsistentes.  
- **Trim**, **lowercase/uppercase**, normalización de texto.  
- Corrección de tipos de datos: conversión a numérico, fecha o categoría.  
- Eliminación de filas con datos incompletos según criterios del ejercicio.  

Cada paso se añadió como un **step** dentro del flujo reproducible, permitiendo mantener trazabilidad.

---

### 4. Creación del pipeline visual
Dataprep estructuró todas las transformaciones dentro de un **recipe**, un pipeline visual que se puede:

- Revisar  
- Reordenar  
- Documentar  
- Ejecutar múltiples veces sobre nuevos datos  

Este enfoque permite mantener un proceso de limpieza estandarizado, esencial para pipelines ETL/ELT más grandes.

---

### 5. Ejecución del job y exportación de resultados
Finalmente se ejecutó el **job** del recipe para producir los datos limpios.  
El estudiante configuró el destino del resultado:

- Exportación a **Cloud Storage**, o  
- Carga directa en **BigQuery** para posteriores análisis o dashboards.

La ejecución mostró estadísticas del job, tiempo de procesamiento y validación final de datos.

---

## Evidencias

| Evidencia | Descripción |
|----------|-------------|
| Dataset cargado en Dataprep | Importación del CSV y perfilado automático del contenido. |
| Perfil visual del dato | Distribuciones, tipos y detección de problemas de calidad. |
| Transformaciones aplicadas | Split, replace, limpieza de texto y correcciones de formato. |
| Pipeline visual (recipe) | Secuencia de pasos reproducibles dentro del flujo. |
| Resultado exportado | Job ejecutado con datos procesados listos para análisis. |

---

## Insights clave
- Dataprep facilita la limpieza y preparación de datos mediante una interfaz intuitiva y sin código.  
- El perfilado automático acelera la detección de problemas, permitiendo concentrarse en decisiones analíticas.  
- Cada transformación queda documentada como un paso del pipeline, reforzando buenas prácticas de **DataOps**.  
- El recipe facilita **reproducibilidad**, **escalabilidad** y **mantenibilidad** del proceso de limpieza.  
- Integrar Dataprep dentro de un flujo ETL/ELT en Google Cloud reduce tiempos de preparación y mejora la calidad final del dato.

---

## Reflexión
Esta práctica reforzó la importancia de contar con herramientas que automaticen y estandaricen la preparación de datos.  
El enfoque visual de Dataprep demuestra que la ingeniería de datos no siempre requiere código para alcanzar resultados profesionales: lo fundamental es la comprensión del proceso, la calidad del dato y la capacidad de reproducir transformaciones.

Se pudo observar cómo una herramienta orientada a **pipelines escalables** permite transformar datos ruidosos en información lista para análisis o carga en BigQuery.  
En conjunto, esta práctica complementa la visión de UT5: **pipeline + limpieza reproducible = datos confiables listos para producción.**

---

## Referencias
- Google Cloud Skills – *Cleaning Data with Dataprep*  
- Dataprep by Trifacta – Documentación oficial  
- Google Cloud – DataOps & Data Engineering guidelines  

---

## Navegación
⬅️ [Volver a Unidad Temática 5](../main.md) 
📓 [Índice del Portafolio](../../portfolio/index.md)
