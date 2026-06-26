# Análisis Financiero de Ecopetrol — Dashboard en Power BI

Dashboard interactivo de análisis financiero del Grupo Ecopetrol (2021–2025),
construido con datos oficiales bajo NIIF. Incluye análisis horizontal y vertical,
ratios financieros, tendencias y alertas.

<!-- TODO: cuando publiques, reemplaza esta línea por una captura del dashboard o un GIF -->
<!-- ![Vista del dashboard](docs/images/portada.png) -->

---

## Objetivo

Construir un análisis financiero completo de una empresa pública colombiana,
mostrando capacidad para: leer e interpretar estados financieros, modelar datos
en Power BI, calcular ratios con DAX y comunicar hallazgos de forma accionable.

## Datos

- **Empresa:** Grupo Ecopetrol
- **Periodo:** 2021–2025 (anual)
- **Base contable:** Consolidado (NIIF)
- **Fuentes:**
  - Relación con Inversionistas de Ecopetrol (estados financieros consolidados) <!-- TODO: pega el link -->
  - Superintendencia Financiera — SIMEV / RNVE <!-- TODO: pega el link -->
  - SEC EDGAR — Formulario 20-F (en inglés) <!-- TODO: pega el link -->

> Nota metodológica: el análisis usa cifras **consolidadas atribuibles a la
> controladora** donde aplica (ej. ROE), por la presencia de interés no controlante
> (ej. ISA).

## Metodología

El pipeline de datos sigue el flujo `raw → interim → processed`:

1. **Descarga** de los estados financieros oficiales en PDF (`data/raw/`).
2. **Extracción** con Python (`pdfplumber`) en Colab (`notebooks/`), volcando a CSV crudo (`data/interim/`).
3. **Limpieza y normalización** a una tabla larga (`estado, cuenta, anio, valor`) lista para BI (`data/processed/`).
4. **Modelado** dimensional en Power BI (tabla de hechos + dim_cuentas + dim_tiempo).
5. **Cálculo** de ratios y comparativos temporales con DAX.
6. **Visualización** y storytelling en el dashboard (`dashboard/`).

**Control de calidad:** los subtotales extraídos se validan contra el PDF original
(total activos corrientes, total activos, pasivos, patrimonio).

## Estructura del repositorio

```
ecopetrol-dashboard/
├── data/
│   ├── raw/          PDFs oficiales (no se editan)
│   ├── interim/      extracciones intermedias
│   └── processed/    tabla larga final para Power BI
├── notebooks/        extracción y limpieza (pdfplumber)
├── dashboard/        archivo .pbix
└── docs/             capturas, video, notas
```

## Hallazgos clave

<!-- TODO: completar tras el análisis. 3–5 hallazgos en lenguaje de negocio.
Ejemplo de formato (reemplazar con los reales):
- La rentabilidad operativa siguió de cerca el ciclo del crudo, con pico en 2022.
- El endeudamiento se mantuvo en X veces EBITDA, dentro de rango.
-->

## Cómo reproducir

1. Clona el repositorio.
2. Abre el notebook en `notebooks/` (Google Colab).
3. Coloca los PDFs en `data/raw/` y ejecuta la extracción.
4. Abre `dashboard/` en Power BI Desktop y conéctalo a `data/processed/`.

## Dashboard en vivo

<!-- TODO: link al dashboard publicado en Power BI Service -->
<!-- TODO: link al video walkthrough (3–5 min) -->

## Stack

Python (pdfplumber, pandas) · Power BI (Power Query, DAX) · Git/GitHub

## Autor

Harry — Contador público | Análisis financiero + datos
<!-- TODO: link a tu LinkedIn -->
