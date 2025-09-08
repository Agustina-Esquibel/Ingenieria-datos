---
title: "UT1 · Práctica 3 — EDA Multifuentes y Joins"
date: 2025-09-07
---

# UT1 · Práctica 3 — EDA Multifuentes y Joins

## Contexto
En esta práctica se trabajó con múltiples fuentes de datos (viajes, zonas y calendario de eventos) aplicando procesos de integración.  
El objetivo principal fue comprender cómo los distintos tipos de *joins* permiten enriquecer los datos y facilitar el análisis posterior.

---

## Objetivos
- Integrar datasets provenientes de diferentes formatos (CSV, Parquet, JSON).  
- Normalizar columnas y preparar los datos para *joins*.  
- Aplicar `LEFT JOIN` e `INNER JOIN` y analizar sus diferencias.  
- Comparar métricas entre días normales y días especiales.  
- Generar insights a partir de datos integrados.

---

## Actividades
1. Carga de datasets de viajes, zonas y calendario.  
2. Normalización de nombres de columnas y fechas.  
3. `LEFT JOIN` de viajes con zonas para añadir boroughs.  
4. Integración con calendario y creación de la variable `is_special_day`.  
5. Análisis comparativo de viajes en días normales vs especiales.  
6. Cálculo de métricas clave (cantidad de viajes, distancias, tarifas).  
7. Respuestas de reflexión sobre la utilidad de los *joins* y la integración multifuente.  

---

## Desarrollo
El trabajo permitió poner en práctica técnicas de unión de datasets en pandas.  
Se verificó que el uso de `LEFT JOIN` garantiza mantener la totalidad de los registros originales, aún si faltan coincidencias en la tabla de referencia.  
La incorporación de información contextual (zonas y días especiales) aporta una visión más rica que la que se obtiene con un dataset aislado.

---

## Evidencias
(Evidencias **escritas**; en esta práctica no se incluyen imágenes.)

- ✅ Se procesaron y unificaron datos de viajes con sus zonas geográficas (asignación de boroughs).  
- 📅 Se integró el calendario de eventos y se creó la bandera `is_special_day` para el análisis comparativo.  
- 📊 Se calcularon métricas consolidadas: total de registros, distancia promedio y tarifa promedio.  
- 🏙️ Se identificaron los boroughs con mayor volumen de viajes (ej.: Manhattan, Queens, Brooklyn).  
- 🔄 Se verificó el impacto de días especiales en la demanda frente a días normales.

---

## Insights clave
1. El `LEFT JOIN` fue clave para **no perder viajes** sin correspondencia en zonas, preservando el universo de análisis.  
2. La integración con calendario permitió **detectar cambios de demanda** en días especiales.  
3. Los boroughs presentan **distribuciones desiguales** de viajes, lo cual sugiere comportamientos y necesidades distintas por zona.  
4. La combinación de fuentes mejora la **calidad de los indicadores** (ej.: métricas por borough y por tipo de día) frente a trabajar con un solo dataset.

---

## Reflexión
Esta práctica refuerza la importancia de la **integración de datos** como paso previo a cualquier análisis serio.  
Trabajar con múltiples fuentes permite construir indicadores más representativos y detectar patrones que no emergen cuando se mira la información de forma aislada.  
Además, la elección del tipo de *join* influye directamente en el **alcance** y la **interpretación** de los resultados.

---

## Referencias
- Consigna oficial: <https://juanfkurucz.com/ucu-id/ut1/04-eda-multifuentes-joins/>

---

## Navegación
- [Volver al índice general](../index.md)  
- [Ir al portafolio completo](index.md)  
- [Ir a la Práctica 2](ut1-practica2.md)  

---

## Nota
El código completo y reproducible de esta práctica está disponible en el README de la carpeta correspondiente en GitHub.
