---
title: "Datos en movimiento: creando un pipeline ETL en Google Cloud"
date: 2025-12-07
---

## Contexto
Esta práctica forma parte de la Unidad Temática 5, enfocada en **pipelines ETL/ELT modernos** sobre Google Cloud.  
El objetivo del ejercicio es comprender cómo se construye un flujo automatizado de datos donde la extracción, transformación y carga se ejecutan mediante componentes nativos de la nube: **Cloud Storage, Cloud Functions y BigQuery**.

La práctica introduce los conceptos clave de **data pipelines**, **event-driven processing**, arquitectura desacoplada y procesamiento escalable en la nube.

---

## Objetivos
- Diseñar y ejecutar un **pipeline ETL básico** utilizando servicios serverless de Google Cloud.  
- Comprender cómo un archivo que ingresa a Cloud Storage puede **disparar automáticamente** una función de transformación.  
- Procesar datos mediante una **Cloud Function**, aplicando limpieza, parseo o enriquecimiento.  
- Cargar los datos transformados en **BigQuery**, habilitando consultas posteriores.  
- Reconocer patrones de diseño esenciales en pipelines modernos: automatización, monitorización y desacoplamiento.

---

## Desarrollo

### 1. Configuración del entorno
Se inició el laboratorio desde Google Skills Boost con un proyecto temporal de Google Cloud.  
Desde la consola, se verificaron permisos, APIs habilitadas y los recursos disponibles para el ejercicio.

---

### 2. Configuración de Cloud Storage
- Se creó un **bucket de entrada** donde se subirían los archivos fuente.  
- Se configuró el bucket para operar como disparador (trigger) del pipeline.  
- Se subió un archivo CSV de prueba para iniciar el flujo.

El estudiante comprendió que Cloud Storage actúa como punto de entrada del pipeline ETL.

---

### 3. Implementación de la Cloud Function
Se creó una **Cloud Function con trigger por evento de Storage**, encargada de:

- Leer el archivo entrante.  
- Aplicar transformaciones básicas (parseo, limpieza, normalización o mapping).  
- Generar el dataset de salida compatible con BigQuery.  
- Escribir datos limpios en un nuevo destino o enviarlos directamente al cargador de BigQuery.

La función se ejecutó bajo un modelo **serverless**, sin necesidad de administrar servidores.

---

### 4. Carga en BigQuery
Finalmente, los datos procesados fueron enviados a **BigQuery**, donde:

- Se creó una tabla destino,  
- Se definieron los tipos de datos,  
- Se verificó la carga correcta,  
- Se realizaron consultas simples para validar el funcionamiento del pipeline.

El estudiante comprobó que BigQuery permite almacenar, consultar y analizar datos transformados de forma inmediata.

---

### 5. Ejecución del pipeline end-to-end
El pipeline quedó estructurado de esta forma:

1. Un archivo es subido a Cloud Storage.  
2. Cloud Storage dispara una Cloud Function.  
3. La Cloud Function transforma los datos.  
4. Los datos resultantes se cargan automáticamente a BigQuery.

Se ejecutó nuevamente el flujo completo para confirmar que el ETL era **automático, reproducible y escalable**.

---

## Evidencias

| Evidencia | Descripción |
|----------|-------------|
| Bucket de entrada creado | Se configuró Cloud Storage como punto de ingreso del pipeline. |
| Cloud Function desplegada | Función serverless conectada por evento “archivo subido”. |
| Transformación aplicada | Lectura y limpieza del archivo fuente dentro de la función. |
| Carga en BigQuery | Tabla creada y poblada con los datos ya transformados. |
| Pipeline end-to-end | Se validó el proceso de disparo automático y carga final. |

---

## Insights clave
- Los pipelines ETL modernos se basan en **automatización**, no en tareas manuales.  
- El uso de triggers convierte a los buckets en **componentes activos del flujo**, no simples contenedores.  
- Cloud Functions permite transformar datos sin administrar servidores, reduciendo complejidad.  
- BigQuery centraliza el almacenamiento analítico, integrándose naturalmente en el pipeline.  
- La arquitectura obtenida ejemplifica un flujo ETL **desacoplado, escalable y orientado a eventos**.

---

## Reflexión
La práctica permitió comprender cómo los componentes de Google Cloud pueden integrarse para formar un pipeline funcional sin necesidad de infraestructura compleja.  
El estudiante reconoció la importancia de diseñar flujos **reproducibles y mantenibles**, donde cada servicio cumple una responsabilidad clara: almacenar, activar, transformar o cargar datos.  
Este ejercicio sienta las bases para implementar pipelines más avanzados aplicados a escenarios reales de analítica, data engineering y DataOps.

---

## Referencias
- Google Cloud Skills – *"Data in Motion: Building an ETL Pipeline"*  
- Documentación oficial de Cloud Functions  
- Documentación oficial de Cloud Storage  
- Documentación oficial de BigQuery  

---

## Navegación
⬅️ [Volver a Unidad Temática 5](../main.md)  

➡️ [DataPrep: limpieza visual de datos orientada a pipeline](../practica16/main16.md)

📓 [Índice del Portafolio](../../portfolio/index.md)
