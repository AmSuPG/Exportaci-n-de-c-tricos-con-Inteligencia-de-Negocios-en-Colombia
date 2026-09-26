# Bitácora del proyecto

Una entrada por decisión. Lo más reciente arriba.

---

## 2026-09-26 · Revisión de los microdatos de exportaciones

- Se descargaron los microdatos del DANE de 2021 a julio de 2026: 67 meses.
- **Las columnas casi no cambian:** desde diciembre de 2022 desaparecen `NIT` y `RAZ_SIAL`, que identifican al exportador. Las demás se llaman igual en todos los meses.
- **Lo que sí cambia es el formato:** el separador, la codificación de caracteres, el separador decimal y los ceros iniciales de la subpartida y el departamento.
- **Hallazgo principal:** en 26 de los 67 meses el CSV trae vacíos el valor y el peso. Casi todo 2025 y 2026 está así. El `.dta` los trae completos.
- **Decisión técnica:** leer el `.dta` y normalizar formatos. Reglas en `datos/README.md`.
- **Validación:** el total de cítricos (0805) por año coincide al 0,00 % con el anexo oficial del DANE en los seis años.
- Registros de cítricos por año: alrededor de 2.000, con 58.780 t en 2021, 105.704 t en 2024 y 99.056 t en 2025.
- **Según el diccionario del DANE:** el origen se toma de `DPTO1`, no de `DPTO2`, que es el departamento desde donde se despacha. El destino se toma de `PAIS`, porque el código de letras viene incompleto. `FECH` es el mes en que se procesó la declaración, no el de embarque, y eso es una **limitación para el análisis por temporadas**.

---

## 2026-09-25 · Viabilidad, enfoque y título

**Viabilidad verificada.**
- La UE interceptó *G. aurantianum* en *Citrus sinensis* de Colombia en marzo de 2021. Fuente: informe mensual de interceptaciones de la UE, marzo de 2021, página 2.
- EPPO la registra como presente en Colombia, sin detalles.
- No hay datos públicos para medir cuánta plaga hay ni dónde: GBIF tiene 5 registros en Colombia (Boyacá 3, Bogotá 1, Meta 1; 2022–2023).

**Enfoque decidido.** La pregunta es el riesgo comercial de las exportaciones frente a la norma europea. La plaga pasa a ser contexto: causa de la norma y evidencia de que el riesgo es real.

**Título decidido:** *Riesgo comercial de las exportaciones colombianas de cítricos ante el requisito fitosanitario europeo contra Gymnandrosoma aurantianum: un análisis por temporadas mediante Inteligencia de Negocio.*

**Pendiente:**
- Si el clima entra al análisis. Es el único vínculo analítico con la plaga.
- Qué es una temporada.
- Periodo (se propuso 2021–2025) y nivel geográfico (se propuso departamento). Sin confirmar.

---

## 2026-09-25 · Reinicio

- Se reinicia el proyecto. Se conserva la idea: analizar con Inteligencia de Negocios el riesgo de *Gymnandrosoma aurantianum* para la exportación de cítricos colombianos.
- El análisis se organizará **por temporadas de tiempo**. Qué tipo de temporada: **pendiente**, se definirá después de revisar la información que aportó Ammi.
- Las fuentes las descargan los autores.
- Se construye por partes.
- Se crea la estructura de carpetas del repositorio.
