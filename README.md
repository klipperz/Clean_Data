# Limpieza de Datos de Smartwatch: Diagnóstico y Solución

**Autor:** Samuel Angel Cardona

## Introducción

Este proyecto detalla el proceso estructurado de limpieza de un conjunto de datos de salud recopilados por un smartwatch. El objetivo es transformar un dataset con datos crudos y problemáticos en un conjunto de datos robusto y fiable, listo para análisis posteriores. La metodología se centra primero en un diagnóstico completo para identificar todas las inconsistencias y errores, y luego en la aplicación de un código de limpieza definitivo para solucionarlos. La estrategia principal es eliminar cualquier registro que presente datos incompletos o erróneos para garantizar la máxima integridad de la información restante.

## Smartwatch Health (Dataset)

**Fuente:** Kaggle - [https://www.kaggle.com/datasets/mohammedarfathr/smartwatch-health-data-uncleaned?select=unclean_smartwatch_health_data.csv](https://www.kaggle.com/datasets/mohammedarfathr/smartwatch-health-data-uncleaned?select=unclean_smartwatch_health_data.csv)

El conjunto de datos original contiene 10,000 registros de métricas de salud de un smartwatch. Incluye columnas como User ID, Heart Rate (BPM), Blood Oxygen Level (%), Step Count, Sleep Duration (hours), Activity Level y Stress Level. El dataset presenta múltiples problemas típicos de datos del mundo real, como valores nulos, tipos de datos incorrectos, inconsistencias categóricas y valores atípicos.

## Descripción del Proceso de Limpieza

Se realizó una limpieza exhaustiva del conjunto de datos, comenzando con una fase de diagnóstico para obtener una "radiografía" completa del estado de los datos. Basándose en los hallazgos de esta primera etapa, se ejecutó un script de limpieza con los siguientes pasos:

1.  **Estandarización de datos categóricos:** Se corrigieron inconsistencias y errores de tipeo en la columna Activity Level (ej. actve a active, seddentary a sedentary y unificación de formatos).
2.  **Manejo de valores no numéricos:** Se identificaron y trataron valores de texto como "ERROR" y "Very High" en columnas numéricas. Estos valores fueron convertidos a un formato numérico o marcados como nulos (NaN) para su posterior eliminación.
3.  **Identificación y tratamiento de outliers:** Se marcaron como nulos los valores atípicos fisiológicamente improbables, como un ritmo cardíaco superior a 220 BPM, considerándolos errores de medición.
4.  **Eliminación de datos nulos:** Se aplicó una estrategia de eliminación estricta, descartando cualquier fila que contuviera al menos un valor nulo después de los pasos anteriores.
5.  **Corrección de tipos de datos:** Se ajustaron los tipos de datos de las columnas para que coincidieran con su naturaleza (ej. User ID y Step Count se convirtieron a enteros).
6.  **Eliminación de duplicados:** Finalmente, se eliminaron todos los registros duplicados para asegurar la unicidad de los datos.

Como resultado, el dataset se redujo de 10,000 a 8,295 registros, garantizando que solo la información completa, consistente y válida permaneciera.

## Hallazgos Principales (del Diagnóstico)

* **Datos Nulos Generalizados:** Todas las columnas del dataset presentaban una cantidad considerable de valores nulos, indicando registros incompletos.
* **Tipos de Datos Incorrectos:** Columnas como User ID, Sleep Duration (hours) y Stress Level tenían tipos de datos float u object, cuando deberían ser de tipo entero o numérico para un análisis correcto.
* **Valores No Numéricos:** Se encontraron textos como "ERROR" y "Very High" en columnas que debían ser puramente numéricas, lo que impedía realizar cálculos matemáticos.
* **Inconsistencias Categóricas:** La columna Activity Level contenía errores de tipeo y formatos inconsistentes (Seddentary vs. Sedentary, Highly Active vs. Highly_Active, Actve), dificultando la agrupación de datos.
* **Valores Atípicos (Outliers):** Se detectó un valor máximo de ritmo cardíaco (Heart Rate (BPM)) de 296.59, el cual es fisiológicamente improbable y apunta a un claro error de medición.

## Librerías utilizadas

Para llevar a cabo este proceso de limpieza y análisis, fue necesario utilizar las siguientes librerías:

* pandas
* numpy
