---
title: "Portafolio - Índice"
date: 2025-09-06
---

Prácticas del curso de Ingeniería de Datos, organizadas por unidades.  
Cada práctica contiene **objetivos, hallazgos principales y reflexiones**.

---

## Unidad Temática 1 – Análisis Exploratorio y Fuentes

### 🌸 Explorando el Iris Dataset: primeros patrones florales y variables predictivas
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

### ⚙️ Configuración del portfolio en GitHub
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

### 🎬 Explorando el catálogo de Netflix: tendencias globales y patrones de contenido audiovisual
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

### 🚕 Analizando los viajes de Nueva York: integración de múltiples fuentes y comparación con Joins

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

🛍️ **Explorando el catálogo de moda: análisis de precios y marcas**  
Link: [Ver práctica](../UT1/extraUT1/extramain.md)

**Objetivo:**  
Analizar datos de ventas de moda en formato JSON para comparar precios, marcas y temporadas, aplicando técnicas de EDA y visualización.

**Hallazgos clave:**  
- Se identificaron diferencias de precios promedio entre categorías y marcas.  
- Las marcas *Zara*, *Mango* y *Banana Republic* destacaron por tener mayor volumen en catálogo.  
- Los precios mostraron variaciones estacionales con picos en primavera y otoño.  

**Reflexión:**  
Este análisis permitió trasladar lo aprendido en la UT1 a un nuevo dominio y formato de datos (JSON), fortaleciendo la capacidad para limpiar, explorar y visualizar información estructurada en contextos comerciales.

---

## Unidad Temática 2 — Limpieza, imputación y ética de datos

### 🧱 Ames Housing bajo la lupa: reconstrucción de información faltante  
*Link:* [Ver práctica](../UT2/practica5/main5.md)  

**Objetivo:** Detectar y analizar valores faltantes en el dataset Ames Housing, aplicando estrategias de imputación contextual y reproducible.  

**Hallazgos clave:**  
- Los mecanismos de *missing data* varían según la variable (MCAR, MAR, MNAR).  
- La imputación contextual mejora la consistencia sin distorsionar distribuciones clave.  
- Documentar el proceso aumenta la trazabilidad y transparencia metodológica.  
**Reflexión:** Aprendí a aplicar imputaciones robustas y justificar decisiones técnicas desde una mirada ética y reproducible.

---

### ⚙️ Escalado y Anti-Leakage Pipeline: preprocesamiento ético y reproducible  
*Link:* [Ver práctica](../UT2/practica6/main6.md)  

**Objetivo:** Implementar un pipeline que normalice, escale y transforme datos sin fuga de información entre *train* y *test*.  

**Hallazgos clave:**  
- El *feature scaling* puede alterar relaciones estadísticas si no se controla el *data leakage*.  
- Los métodos `StandardScaler`, `MinMaxScaler` y `RobustScaler` muestran comportamientos distintos ante outliers.  
- El *log transform* mejora la simetría de variables muy sesgadas.  
**Reflexión:** Fortalecí el criterio para diseñar procesos de preprocesamiento reproducibles y éticamente responsables.

---

### ⚖️ Sesgo bajo la lupa: detección, corrección y decisiones éticas con Fairlearn  
*Link:* [Ver práctica](../UT2/practica7/main7.md)  

**Objetivo:** Detectar, medir y mitigar sesgos en modelos predictivos mediante métricas de *fairness* aplicadas a casos reales (Boston Housing y Titanic).  

**Hallazgos clave:**  
- Los sesgos históricos influyen directamente en los modelos si no se corrigen.  
- Fairlearn permite equilibrar *accuracy* y equidad de manera cuantificable.  
- Las decisiones éticas requieren evaluar impacto social, no solo rendimiento.  
**Reflexión:** Comprendí cómo la equidad y la ética son parte del ciclo técnico de un modelo, no un añadido posterior.
