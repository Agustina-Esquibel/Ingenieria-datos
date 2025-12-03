---
title: "Geointeligencia urbana: cobertura del SUBTE, densidad poblacional y demanda vecinal en Buenos Aires"
date: 2025-11-18
---

## Contexto
El análisis geoespacial permite comprender fenómenos clave como la accesibilidad al transporte, la concentración de población y la demanda por servicios públicos.  
Esta práctica integra tres fuentes fundamentales para caracterizar la estructura urbana de CABA:

- Polígonos de **barrios** con población y superficie.  
- Líneas y **estaciones del SUBTE**.  
- Datos de **contactos SUACI**, como proxy de presión vecinal.

El objetivo general fue estudiar cómo interactúan **densidad urbana**, **accesibilidad al SUBTE** y **demanda ciudadana**, apoyándose en un flujo geoespacial reproducible con GeoPandas.

## Objetivos
- Analizar cómo se distribuye la población y la demanda vecinal en el territorio.  
- Calcular accesibilidad al SUBTE mediante estaciones por km² y distancia mínima.  
- Normalizar la demanda SUACI por habitante para evitar sesgos.  
- Integrar datasets espaciales y tabulares mediante joins y proximidad.  
- Elaborar visualizaciones narrativas orientadas a la toma de decisiones.  
- Comparar metodologías alternativas (distancia Euclidiana vs distancia por red vial).

## Actividades
- Conversión de todas las capas al CRS proyectado **EPSG:5347**.  
- Cálculo de métricas básicas: área real, densidad poblacional y contactos per cápita.  
- Join espacial entre estaciones y barrios (punto–en–polígono).  
- Distancia mínima al SUBTE mediante `sjoin_nearest`.  
- Elaboración de coropletas y visualizaciones comparativas.  
- Análisis crítico entre métricas de distancia (recta vs vial).

---

## Desarrollo

### 1. Preparación de datos y CRS
Todas las capas fueron reproyectadas a **EPSG:5347**, una proyección métrica adecuada para Buenos Aires.  
Con esto, las áreas y distancias se calcularon correctamente en m² y metros.

Se obtuvieron:
- `area_m2` a partir de la geometría.  
- `densidad_hab_km2 = poblacion / (area_m2 / 1e6)`.

Estas métricas permiten comparar barrios de distinto tamaño bajo criterios homogéneos.

### 2. Normalización de la demanda SUACI
Para evitar que los barrios más poblados aparezcan automáticamente como líderes en demanda, se utilizó una métrica ajustada por habitantes.  
La fórmula fue:
```
contactos_pc = contactos_totales / poblacion
```

Esta normalización permitió identificar barrios donde la presión vecinal es realmente alta, independientemente del tamaño de la población.

### 3. Cobertura del SUBTE y accesibilidad territorial
Mediante un join espacial punto-en-polígono se obtuvo:
- `n_estaciones` por barrio.  
- `estaciones_por_km2` como indicador de cobertura.

Luego, con centroides y `sjoin_nearest`, se calculó la **distancia mínima** de cada barrio al SUBTE.  
Este análisis evidenció brechas de accesibilidad en la periferia sur.

### 4. Visualizaciones elaboradas
*(Serán agregadas más adelante en `/assets/UT4/`)*

- Coropleta de densidad poblacional.  
- Coropleta de contactos per cápita.  
- Cobertura del SUBTE por km².  
- Distancia mínima a estaciones.  
- Scatter accesibilidad vs demanda vecinal.

---

## Comparación de métodos: razonamiento crítico

### 🔹 Enfoque 1 — Distancia Euclidiana (implementado)
- Mide la distancia directa entre centroides y estaciones.  
- Es veloz y adecuado para análisis exploratorios.  
- Subestima la accesibilidad real en zonas urbanas complejas.

| Método | Ventaja | Limitación | Complejidad |
|--------|---------|------------|-------------|
| Distancia Euclidiana | Simple y rápida | No considera la red vial | Baja |

---

### 🔹 Enfoque 2 — Distancia por red vial (OSMnx)
- Modela la caminabilidad real usando un grafo de calles.  
- Otorga estimaciones más precisas del acceso al transporte.  
- Tiene mayor costo computacional y requiere más preparación.

| Método | Ventaja | Limitación | Complejidad |
|--------|---------|------------|-------------|
| Red vial (OSMnx) | Alta fidelidad urbana | Mayor preparación/cómputo | Media/Alta |

---

### ✔ Conclusión comparativa
Para exploración inicial y reproducibilidad académica, la **distancia Euclidiana** es suficiente.  
Para análisis de movilidad o planificación urbana, la **distancia vial** sería el enfoque adecuado.

---

## Evidencias  
*(Las visualizaciones se agregarán posteriormente)*

---

### 📌 **1. Densidad de población (hab/km²)**
**Interpretación:** Los barrios del eje centro-norte (Balvanera, Recoleta, Almagro) concentran la mayor densidad.  
**Conclusión operativa:** Estas zonas requieren infraestructura más robusta y soportan mayor presión sobre servicios.

---

### 📌 **2. Contactos SUACI per cápita**
**Interpretación:** Barrios con población moderada pueden presentar la mayor demanda relativa, especialmente zonas con actividad administrativa o comercial.  
**Conclusión operativa:** La función urbana explica la demanda mejor que la población total.

---

### 📌 **3. Cobertura del SUBTE (estaciones por km²)**
**Interpretación:** La red es densa en el eje central (Palermo–Recoleta–Balvanera).  
**Conclusión operativa:** La periferia sur evidencia brechas claras de accesibilidad.

---

### 📌 **4. Distancia mínima al SUBTE**
**Interpretación:** Lugano, Soldati y Riachuelo presentan las distancias más altas.  
**Conclusión operativa:** Son candidatos para extensión del SUBTE o servicios alternativos (BRT, tren ligero).

---

### 📌 **5. Accesibilidad vs demanda (scatter)**
**Interpretación:** No existe relación lineal simple entre accesibilidad y demanda.  
**Conclusión operativa:** La centralidad funcional es un predictor más fuerte que la distancia al SUBTE.

---

## Insights clave

1. La cobertura del SUBTE se concentra en el eje central de la ciudad.  
2. La normalización cambia completamente la lectura territorial de la demanda vecinal.  
3. La densidad poblacional no predice la demanda SUACI.  
4. La periferia sur presenta las mayores brechas de accesibilidad.  
5. Accesibilidad y presión vecinal son fenómenos complementarios, no equivalentes.

---

## Reflexión
Esta práctica integró análisis geoespacial, normalización de métricas y razonamiento crítico.  
El aprendizaje clave fue comprender cómo las **decisiones metodológicas** (CRS, normalización, elección de métricas) afectan directamente la interpretación de los mapas y los fenómenos urbanos.

La diferencia entre datos absolutos y tasas per cápita, y entre distancia recta y distancia vial, mostró cómo distintas métricas producen lecturas territoriales distintas.  
Documentar estos criterios y mantener un flujo reproducible reforzó buenas prácticas de ingeniería de datos.

---

## Notebook en Google Colab
📓 El enlace será agregado una vez finalizado el notebook.

## Navegación
⬅️ Volver a Unidad Temática 4  
📓 [Índice del Portafolio](../../portfolio/index.md)
