# Semana 7 — Práctica de PySpark en Databricks

Soluciones de la práctica de **PySpark** de la semana 7, ejecutadas en **Databricks Free Edition (serverless, Spark 4.1)**. Son 10 módulos y un desafío final; cada ejercicio tiene debajo una celda de comprobación con `assert`.

Notebook: [`PySpark_Databricks_Ejercicios_resuelto.ipynb`](PySpark_Databricks_Ejercicios_resuelto.ipynb)

| Módulo | Tema | Datos |
|---|---|---|
| 1 | Crear DataFrames con esquema explícito | lista en Python |
| 2 | Explorar una tabla | `samples.nyctaxi.trips` |
| 3 | Seleccionar y filtrar | `samples.nyctaxi.trips` |
| 4 | Columnas nuevas, fechas, `when`, `try_divide` | `samples.nyctaxi.trips` |
| 5 | Agregaciones (`groupBy` / `agg`) | `viajes` |
| 6 | Joins: inner, left, left_anti, broadcast | `viajes` + `zonas` |
| 7 | Funciones de ventana: `row_number`, acumulado, `lag` | `viajes` |
| 8 | Spark SQL y celdas `%sql` | vista temporal `viajes` |
| 9 | Limpieza: nulos, duplicados, `try_cast` | `clientes_sucios` |
| 10 | Escritura en tabla Delta y CSV en un volumen | `workspace.default` |
| Desafío | Ventas por país y mejor país por región | `samples.tpch` |

## Cómo ejecutarlo

1. En Databricks, importa el notebook (**Workspace → Import**) y conéctalo a **Serverless**.
2. Ejecuta todo con **Run all**. Las celdas van en orden porque varios ejercicios usan resultados de los anteriores.
3. Cada celda de comprobación debe imprimir `Correcto`; la última imprime `Desafío B listo`.

No hace falta subir datos: todo sale de las tablas de ejemplo `samples.nyctaxi` y `samples.tpch` que ya vienen en el workspace, y de DataFrames pequeños creados en el propio notebook.

## Qué crea en el workspace

- La tabla `workspace.default.taxis_por_tipo` (módulo 10.1).
- El volumen `workspace.default.curso_pyspark` con el CSV de `top_zips` (módulo 10.2).

La última celda, **Limpieza (opcional)**, trae las instrucciones para borrarlos.

## Notas

- En serverless está activo el modo ANSI, por eso se usan `F.try_divide` y `try_cast` en lugar de la división y el `cast` normales.
- En el ejercicio 7.1 la ventana desempata por `pickup_zip`, para que el top 3 salga igual en cada ejecución.
- Los datos de `clientes_sucios` son ficticios.
