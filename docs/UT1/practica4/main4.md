---
title: "Analizando los viajes de Nueva York: integración de múltiples fuentes y comparación con Joins"
date: 2025-08-27
---

## Contexto
En esta práctica se integraron múltiples fuentes de datos del ecosistema de transporte de Nueva York —viajes, zonas y calendario de eventos— aplicando distintas estrategias de unión (*joins*)
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
El trabajo permitió poner en práctica las técnicas de unión de datasets en *pandas*.  
Se observó que el uso de *LEFT JOIN* garantiza mantener la totalidad de los registros originales, incluso si faltan coincidencias en la tabla de referencia. En cambio, *INNER JOIN* restringe el universo de análisis, priorizando solo las coincidencias exactas.  
La integración del contexto espacial (zonas) y temporal (días especiales) aportó una visión más completa que la obtenida con un dataset aislado. Esto permitió calcular métricas agregadas por *borough* y comparar la demanda de viajes según el tipo de día, destacando el impacto de eventos y feriados en el volumen de transporte.  
Además, se aplicaron cálculos de eficiencia y optimización de memoria para manejar grandes volúmenes de datos, reforzando la importancia de preparar correctamente las fuentes antes de ejecutar los *joins*

## Evidencias
- ✅ Se procesaron y unificaron datos de viajes con sus zonas geográficas (asignación de boroughs).  
- ✅ Se integró el calendario de eventos y se creó la bandera `is_special_day` para el análisis comparativo.  
- 📊 Se calcularon métricas consolidadas: total de registros, distancia promedio y tarifa promedio.  
- 🏙️ Se identificaron los boroughs con mayor volumen de viajes (Manhattan, Queens y Brooklyn).  
- 📈 Se verificó el impacto de los días especiales en la demanda frente a los días normales.  

### Comparación visual de estrategias de JOIN

**Resumen de registros tras la integración**
| Paso | Registros | Descripción |
|---|---:|---|
| Viajes (base) | 100% | Universo de viajes crudos |
| LEFT JOIN con zonas | ~100% | Conserva viajes sin zona conocida (nulos); no pierde universo |
| INNER JOIN con zonas | ↓ | Elimina viajes sin zona (solo coincidencias exactas) |

**¿Qué cambia con cada JOIN? (ejemplo ilustrativo)**
| id_viaje | id_zona | LEFT JOIN zona | INNER JOIN zona |
|---:|---:|:---:|:---:|
| 101 | 12 | ✅ | ✅ |
| 102 | —  | ✅ *(zona = nulo)* | ❌ *(se descarta)* |
| 103 | 07 | ✅ | ✅ |

**Conclusión operativa**  
- **LEFT JOIN** preserva el **universo completo** y permite análisis con nulos controlados.  
- **INNER JOIN** **depura** pero **reduce alcance**; útil si se requiere consistencia estricta.

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
[🔗 Abrir en Google Colab](https://colab.research.google.com/github/agustina-esquibel/Ingenieria-datos/blob/main/docs/UT1/practica4/Agustina_Esquibelpractico4.ipynb)

## Referencias
- [NYC Taxi Dataset](https://www1.nyc.gov)  
- [NYC Taxi Zones](https://www1.nyc.gov)  
- [Documentación `pandas.merge`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.merge.html)  

## Navegación
⬅️ [Volver a Unidad Temática 1](../main.md)  
📓 [Índice del Portafolio](../../portfolio/index.md)
