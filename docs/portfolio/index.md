---
title: "Portafolio - Índice"
date: 2025-09-06
---
# Portfolio

Prácticas del curso de Ingeniería de Datos, organizadas por unidades.  
Cada práctica contiene **objetivos, hallazgos principales y reflexiones**.

---

## Unidad Temática 1

### Práctica 1 – Dataset Iris
Link: [Ver práctica](../UT1/practica1/main1.md)

**Objetivo:** 
Explorar el dataset Iris y aplicar un análisis exploratorio inicial.  

**Hallazgos clave:**
- La especie *Setosa* se separa claramente de las demás.
- Correlaciones fuertes entre el largo y el ancho de los pétalos.
- Dataset balanceado con 50 registros por especie.

**Reflexión:** 
Esta práctica me ayudó a familiarizarme con técnicas básicas de EDA y a ganar confianza en la interpretación de correlaciones simples mediante visualizaciones claras.

---

### Práctica 2 – Configuración del portafolio en GitHub
Link: [Ver práctica](../UT1/practica2/main2.md)

**Objetivo:** 
Crear un repositorio en GitHub a partir del template y publicar el portafolio con GitHub Pages.  

**Hallazgos clave:**
- Repositorio configurado correctamente con estructura inicial de carpetas.
- GitHub Actions desplegó el sitio sin errores.
- Portafolio visible online desde etapas tempranas.

**Reflexión:** 
Aunque no implicó análisis de datos, esta práctica fue esencial para organizar el flujo de trabajo, mantener trazabilidad y asegurar que los resultados pudieran documentarse y compartirse fácilmente.

---

### Práctica 3 – Dataset Netflix
Link: [Ver práctica](../UT1/practica3/main3.md)

**Objetivo:** 
Analizar el catálogo de Netflix considerando años, tipos de contenido, países y duración.  

**Hallazgos clave:**
- Predominio de películas sobre series.
- Crecimiento sostenido de estrenos desde 2016.
- Concentración de la producción en pocos países (principalmente EE.UU. e India).

**Reflexión:** 
Trabajar con este dataset me permitió enfrentarme a problemas reales de datos incompletos y extraer conclusiones a partir de visualizaciones que evidencian patrones de la industria audiovisual.

---

### Práctica 4 – Dataset Taxis NYC
Link: [Ver práctica](../UT1/practica4/main4.md)

**Objetivo:** 
Integrar datasets de viajes, zonas y calendario para aplicar distintos *joins* y enriquecer el análisis.  

**Hallazgos clave:**
- El `LEFT JOIN` permitió preservar todos los viajes, incluso sin coincidencia en zonas.
- Se observaron diferencias en la cantidad de viajes entre días normales y especiales.
- Boroughs con mayores volúmenes de viajes: Manhattan, Queens y Brooklyn.

**Reflexión:** 
Esta práctica fue la más desafiante de la UT1, porque implicó integración de múltiples fuentes y análisis temporal. Me permitió valorar cómo la correcta unión de datasets cambia el nivel de los insights obtenidos.

---

## Extra – Flujo de trabajo de UT1

Para esta primera unidad, el proceso seguido puede resumirse en el siguiente flujo:

```mermaid
flowchart LR
    A[📂 Datos crudos] --> B[🧹 Limpieza con Pandas]
    B --> C[🔎 EDA: análisis exploratorio]
    C --> D[📊 Visualizaciones con Matplotlib/Seaborn]
    D --> E[📝 Hallazgos documentados en MkDocs]
    E --> F[🌐 Publicación en GitHub Pages]

Este esquema refleja como cada practica 
