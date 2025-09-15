# Práctica 2 – Portafolio con GitHub Pages

## Objetivo  
Configurar tu portafolio en GitHub: crear repositorio desde el template, activar GitHub Pages con GitHub Actions, y publicar una versión inicial con contenidos mínimos visibles online.

---

## Desarrollo / Pasos realizados

1. Usé el template proporcionado (`ia-portfolio-template`) para crear mi repositorio nuevo en GitHub.  
   - Owner: @AgustinaEsquibel (tu usuario)  
   - Nombre del repo: `Ingenieria-datos-Portfolio` (o como lo hayas llamado)  
   - Lo hice público para permitir que se vea con GitHub Pages.

2. Configuré GitHub Pages / GitHub Actions:  
   - En Settings → Pages elegí la opción de desplegar vía Actions.  
   - Verifiqué que el workflow automático (“deploy”) corriera sin errores.

3. Estructura de contenido inicial agregada:  
   - Página de portada / About con nombre, breve bio y vínculo a tu GitHub / contacto.  
   - En el índice, listado de prácticas relacionadas (Práctica 1, Práctica 2, etc.).  
   - Visualizaciones inciales del dataset Iris (pairplot, heatmap, etc.) incluidas como ejemplo.  
   - Una sección “Próximos pasos” donde describí lo que pienso mejorar: limpieza de datos, visualizaciones adicionales, integración de más dataset, etc.

4. Publicación:  
   - Commit + push de los cambios.  
   - Confirmé que el sitio estaba accesible en la URL de GitHub Pages correspondiente, sin errores 404.

---

## Resultados

- El repositorio quedó visible online bajo la URL: `https://agustina-esquibel.github.io/<nombre-del-repo>/` 
- Se puede ver la portada / About / Índice / enlace a práctica Iris (EDA inicial).  
- La visualización del pairplot / heatmap se muestra correctamente.  
- GitHub Actions desplegó sin fallos → vida del workflow verde.

---

## Hallazgos clave

- Aunque parezca “mínimo”, configurar el repo desde el template da estructura y uniformidad.  
- Usar GitHub Pages + MkDocs + Actions requiere cuidar las rutas y nombres de archivos (un cambio mínimo puede romper todo).  
- Tener contenido visible desde el comienzo (aunque sea poco) proyecta profesionalismo.  
- Identifiqué mejoras fáciles: imágenes comprimidas para que carguen rápido; navegación lateral bien estructurada; enlaces correctos a notebooks etc.

---

## Reflexión

El ejercicio de esta práctica fue más setup que análisis, pero su rol es fundamental: sin una base bien configurada, las prácticas posteriores se ven desordenadas o inaccesibles.  
Esta experiencia me hizo valorar mucho el trabajo “por debajo del agua” (repositorio limpio, deploy automático, estructura fija), que muchas veces se subestima.  
Estoy motivada a usar esta base para las siguientes unidades, manteniendo buenas prácticas desde el inicio.

---
