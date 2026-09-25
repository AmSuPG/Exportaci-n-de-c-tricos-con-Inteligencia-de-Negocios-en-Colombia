# Contexto del proyecto

Artículo para la materia **Inteligencia de Negocios y Big Data**, Universidad Distrital Francisco José de Caldas, Ingeniería de Sistemas.

**Autores:** Ammi Susana Pineda Guzmán y Diego Felipe Barreto Rubiano.

**Título:** Análisis del riesgo de la polilla perforadora *Gymnandrosoma aurantianum* en la exportación de cítricos colombianos mediante Inteligencia de Negocio.

---

## La idea

Analizar, con Inteligencia de Negocios, el riesgo que representa la polilla perforadora *Gymnandrosoma aurantianum* para la exportación de cítricos colombianos.

**Delimitación:** el trabajo se limita a Inteligencia de Negocios. Así lo decidieron los autores desde el inicio.

---

## Cómo se trabaja

El proyecto **se reinició el 2026-09-25**. Estas son las reglas desde ese día:

- **El análisis se organiza por temporadas de tiempo.** Qué significa "temporada" lo definen los autores después de revisar la información que aportó Ammi. Hasta que lo definan, no se asume.
- **Los autores descargan las fuentes ellos mismos.** No descargar datos por cuenta propia.
- **Se construye por partes, una a la vez.** No adelantar diseño, modelo, indicadores ni estructura del artículo que los autores no hayan pedido.
- **Cada decisión se registra** en `notas/bitacora.md`.
- **Cada fuente descargada se registra** en la tabla de `datos/README.md`.

---

## ⚠️ El repositorio es público

- **No subir los códigos estudiantiles** de los autores.
- Los **PDFs de artículos** van en `referencias/pdf/`, que no se sube.
- Los **datos con licencia restringida** van en `datos/restringidos/`, que no se sube.
- `datos/crudos/` no se modifica nunca: lo transformado va a `datos/procesados/`.

---

## Estructura

| Carpeta | Contenido |
|---|---|
| `articulo/` | LaTeX, clase `IEEEtran` modo `conference`, en español |
| `datos/crudos/` | Fuentes tal como se descargan |
| `datos/procesados/` | Resultado de limpiar y transformar |
| `datos/restringidos/` | Datos no publicables (ignorado por git) |
| `powerbi/` | Archivo `.pbix` del tablero |
| `referencias/` | Bibliografía y notas de lectura |
| `notas/` | Bitácora de decisiones |

---

## Versión anterior

Hubo un diseño previo que los autores **descartaron**. Está archivado solo en el equipo de Diego, fuera del repositorio. **No usarlo como guía** salvo que los autores pidan recuperar algo puntual.
