# Laboratorio 7 — Pipeline ETL y Data Lake

**Asignatura:** Fundamentos de Big Data (IDSD413)  
**Institución:** Escuela Politécnica Nacional  
**Modalidad:** Práctica grupal en Google Colab

## Objetivo

Implementar un pipeline ETL para procesar transacciones sintéticas con valores nulos, duplicados y valores atípicos, aplicando reglas de limpieza condicionada y organizando los datos en un Data Lake simulado.

## Actividades realizadas

- **Profiling y RAW:** generación de 5 millones de transacciones base, simulación de datos problemáticos, diagnóstico de nulos y duplicados, y conservación de los datos originales en Parquet.
- **Reto 1 — Capa de cuarentena:** detección de outliers mediante la regla IQR y almacenamiento separado en `datalake/quarantine`, sin perder esos registros.
- **Reto 2 — Descarte inteligente:** eliminación de transacciones con estado `Cancelado` y `monto` nulo; imputación con la mediana por `categoria` para los demás estados.
- **Normalización y CURATED:** escalado Min-Max de `monto`, guardado de datos preparados para el análisis y verificación de las tres capas.

## Estructura del Data Lake

Los siguientes archivos son **generados durante la ejecución**; no es necesario subir los datos masivos a GitHub.

```text
datalake/
├── raw/
│   └── ingesta_transacciones_sucio.parquet
├── quarantine/
│   └── transacciones_outliers.parquet
└── curated/
    └── transacciones_model_ready.parquet
```

- **RAW:** conserva los datos de ingesta para trazabilidad.
- **QUARANTINE:** conserva los valores atípicos para su revisión posterior.
- **CURATED:** contiene los registros depurados y normalizados para análisis.

## Cómo ejecutar

1. Abrir el notebook `.ipynb` en [Google Colab](https://colab.research.google.com/).
2. Ejecutar las celdas en orden, desde la generación de datos hasta la verificación final.
3. Revisar las salidas de limpieza, la cantidad de outliers y los archivos Parquet producidos.
4. Abrir el panel **Archivos** de Colab y comprobar las carpetas `raw`, `quarantine` y `curated`.

**Tecnologías:** Python, pandas, NumPy, PyArrow y Google Colab.

## Nota

El enunciado proporcionado describe dos retos de modificación y menciona tres en la sección de entregables. Este repositorio documenta los **dos retos detallados** y conserva el escalado Min-Max incluido en el notebook base.

Los resultados numéricos pueden variar si se modifica la semilla, la generación de datos o la lógica de transformación.
