# CENTINELA

**CENTINELA** es la capa de seguridad y confianza del proyecto **AtalaIA Licit@**: la "IA del licitador".

AtalaIA Licit@ es una plataforma de inteligencia artificial que analiza licitaciones públicas por cuenta de PYMEs de ingeniería — una capacidad hoy reservada a grandes empresas con departamentos de análisis propios. Para funcionar, esa plataforma necesita que las empresas le confíen información sensible: pliegos, ofertas, condiciones comerciales. Si esa información no está bien protegida, la plataforma no solo sería insegura, sería inviable como negocio.

CENTINELA es el diseño y la construcción de esa capa de protección, antes de escribir la primera línea de la plataforma: seguridad desde el diseño, no añadida después. Es el prototipo presentado a los **Premios de la Cátedra de Ciberseguridad a la Innovación en Ciberseguridad e Inteligencia Artificial** de la Universidad de Málaga, desarrollado durante julio y agosto de 2026 en GSEC Málaga con la mentoría de profesionales de Google.

Equipo: Francisco Andrés Correa Barrera (fundador de AtalaIA Licit@, responsable del proyecto) y Mario Quintana Simonet (partner estratégico técnico).

Demo del proyecto AtalaIA Licit@: https://pacocorreab-ui.github.io/AtalaIA/

## Ver la memoria online (GitHub Pages)

Este repositorio publica la memoria del proyecto como una página web de una sola vista, navegable con scroll (no un PDF), adaptada tanto a ordenador como a móvil.

1. Sube el contenido de este repositorio a GitHub (ver estructura de ficheros abajo).
2. En el repositorio: **Settings → Pages**.
3. En "Build and deployment", elige **Deploy from a branch**, rama `main` (o `master`) y carpeta `/root`.
4. Guarda. GitHub publicará el sitio en `https://<tu-usuario>.github.io/<nombre-del-repo>/` en uno o dos minutos.

`index.html` es la página de entrada que GitHub Pages sirve automáticamente en esa URL.

## Estructura de ficheros necesaria

```
index.html                     ← documento principal (no mover ni renombrar)
support.js                     ← runtime de render, no editar
doc-page.js                    ← componente de paginado del documento
uploads/AtalaIA-Emblema.png    ← logotipo usado en portada, cierre y pie de página
```

Los cuatro deben mantenerse en las mismas rutas relativas entre sí; si cambias la estructura de carpetas, las rutas dentro de `index.html` dejarán de resolver.

## Actualizar el contenido

El documento fuente editable es `Memoria CENTINELA.dc.html` (fuera de este export). Cualquier cambio debe hacerse ahí y luego volver a copiarse sobre `index.html` para republicar.

## Notas técnicas

- La página carga React, ReactDOM y Babel bajo demanda desde una CDN pública (unpkg) — se necesita conexión a internet para verla.
- No requiere backend ni build: son ficheros estáticos servidos tal cual.
- En pantallas estrechas (móvil), la página se reduce de escala automáticamente para mostrar el documento completo sin recortes, conservando texto e imágenes nítidos.
