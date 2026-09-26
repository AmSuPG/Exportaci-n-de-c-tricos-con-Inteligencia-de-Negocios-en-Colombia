# Datos

| Carpeta | Contenido | ¿Se sube? |
|---|---|---|
| `crudos/` | Las fuentes tal como se descargan. **No se modifican nunca**: si algo se limpia, el resultado va a `procesados/` | Sí |
| `procesados/` | Lo que sale de limpiar, unir y transformar los crudos | Sí |
| `restringidos/` | Datos cuya licencia no permite publicarlos | **No** |

## Cómo leer los microdatos del DANE

Cada mes viene en tres formatos: CSV, Stata (`.dta`) y SPSS (`.sav`).

**Usar el `.dta`, no el CSV.** En 26 de los 67 meses de 2021 a julio de 2026, el CSV trae vacías las columnas de valor (`FOBDOL`) y peso (`PNK`). El `.dta` las trae completas en todos los meses.

El formato cambia entre meses, así que hay que normalizar:

| Qué | Cambio | Cómo tratarlo |
|---|---|---|
| `FOBDOL`, `PNK` | A veces numérico, a veces texto con formato colombiano (`186.240,81`) | Si es texto: quitar los puntos y cambiar la coma por punto |
| `POSAR` (subpartida) | A veces pierde el cero inicial (`805502200` en vez de `0805502200`) | Rellenar con ceros hasta 10 dígitos |
| `DPTO1`, `DPTO2` | Sin cero inicial (`5` en vez de `05`) | Rellenar a 2 dígitos |
| `NIT`, `RAZ_SIAL` | Solo existen hasta noviembre de 2022; identifican al exportador. La ficha 2025–2026 explica que el DANE dejó de publicarlas por reserva estadística | Descartarlas |

Según el diccionario de datos (`referencias/ddi-documentation-spanish-472.pdf` y `-859.pdf`):

| Variable | Qué es | Cómo usarla |
|---|---|---|
| `DPTO1` | Departamento **de origen** de la mercancía | **Es la que se usa** para saber de dónde salen los cítricos |
| `DPTO2` | Departamento **de procedencia**, desde donde se despacha. Incluye un código `1` para petróleo y derivados | No usar para origen |
| `FECH` | Año y mes **en que se procesó** la declaración de exportación (`2501` = enero de 2025), no la fecha de embarque | Declararlo como limitación al analizar temporadas |
| `PAIS` | Código numérico del país de destino, con la codificación del DANE (`249` = Estados Unidos, `573` = Países Bajos) | **Usar este**. `COD_PAI4`, el código de letras, viene vacío en muchas filas de algunos meses |
| `POSAR` | Subpartida arancelaria | Los cítricos son las que empiezan por `0805` |
| `FOBDOL` | Valor FOB en dólares | Medida principal |
| `PNK` | Kilos netos | Medida de volumen |

> **Unión Europea:** los microdatos no marcan qué países son de la UE; hay que construir esa clasificación. Recordar que el **Reino Unido no es parte de la UE** desde 2020, así que el reglamento europeo no aplica a lo que se le exporta.

**Validación:** leyendo el `.dta` con esas reglas, el total de cítricos (partida 0805) de cada año, de 2021 a 2026, coincide al 0,00 % con el Cuadro 15 del anexo oficial del DANE.

**Qué se puede publicar:** las filas individuales, aunque estén filtradas o limpias, siguen siendo microdatos y se quedan en `restringidos/`. Las tablas agregadas, por ejemplo por año, mes, departamento o país, sí pueden ir en `procesados/`, citando al DANE.

## Registro de fuentes

Cada archivo que entre a `crudos/` se anota aquí. Es la base de la tabla de fuentes del artículo, y reconstruirla después cuesta mucho más que anotarla al momento.

| Archivo | Fuente | Dirección web | Fecha de descarga | Periodo que cubre |
|---|---|---|---|---|
| `restringidos/Expo_2021.zip` a `Expo_2024.zip` | DANE, microdatos de exportaciones (EXPO), catálogo 472 | https://microdatos.dane.gov.co/index.php/catalog/472/get-microdata | 2026-09-26 | Un archivo por año, cada uno con doce archivos mensuales |
| `restringidos/Expo_2025.zip` y `Expo_2026.zip` | DANE, microdatos de exportaciones (EXPO), catálogo 859 | https://microdatos.dane.gov.co/index.php/catalog/859/get-microdata | 2026-09-26 | 2025 completo; 2026 de enero a julio |
| `crudos/anex-EXPORTACIONES-jul2026 (1).xls` | DANE, anexos del boletín de exportaciones de julio de 2026 (34 cuadros agregados) | https://www.dane.gov.co/index.php/estadisticas-por-tema/comercio-internacional/exportaciones | 2026-09-24 | Varía por cuadro: la serie anual de cítricos (Cuadro 15) va de 2021 a julio de 2026; la de limón Tahití (Cuadro 4) solo compara enero-julio 2025 con enero-julio 2026 |
