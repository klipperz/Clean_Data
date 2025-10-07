# Limpieza de Datos de Smartwatch: Diagnóstico y Solución

**Autor:** Samuel Angel Cardona

## Introducción

Este proyecto detalla el proceso estructurado de limpieza de un conjunto de datos de salud recopilados por un smartwatch. El objetivo es transformar un dataset con datos crudos y problemáticos en un conjunto de datos robusto y fiable, listo para análisis posteriores. La metodología se centra primero en un diagnóstico completo para identificar todas las inconsistencias y errores, y luego en la aplicación de un código de limpieza definitivo para solucionarlos. La estrategia principal es eliminar cualquier registro que presente datos incompletos o erróneos para garantizar la máxima integridad de la información restante.

## Smartwatch Health (Dataset)

**Fuente:** Kaggle - [https://www.kaggle.com/datasets/mohammedarfathr/smartwatch-health-data-uncleaned?select=unclean_smartwatch_health_data.csv](https://www.kaggle.com/datasets/mohammedarfathr/smartwatch-health-data-uncleaned?select=unclean_smartwatch_health_data.csv)

El conjunto de datos original contiene 10,000 registros de métricas de salud de un smartwatch. Incluye columnas como User ID, Heart Rate (BPM), Blood Oxygen Level (%), Step Count, Sleep Duration (hours), Activity Level y Stress Level. El dataset presenta múltiples problemas típicos de datos del mundo real, como valores nulos, tipos de datos incorrectos, inconsistencias categóricas y valores atípicos.

## Descripción del Proceso de Limpieza

El proceso inició con un diagnóstico para identificar todos los errores del dataset. Posteriormente, se ejecutó un script para estandarizar datos categóricos, corregir valores no numéricos y marcar outliers fisiológicamente improbables. Finalmente, se ajustaron los tipos de datos a su formato correcto y se eliminaron todas las filas con valores nulos, así como los registros duplicados.

## Hallazgos Principales del Diagnóstico

* **Datos Nulos Generalizados:** Todas las columnas del dataset presentaban una cantidad considerable de valores nulos, indicando registros incompletos.
* **Tipos de Datos Incorrectos:** Columnas como User ID, Sleep Duration (hours) y Stress Level tenían tipos de datos float u object, cuando deberían ser de tipo entero o numérico para un análisis correcto.
* **Valores No Numéricos:** Se encontraron textos como "ERROR" y "Very High" en columnas que debían ser puramente numéricas, lo que impedía realizar cálculos matemáticos.
* **Inconsistencias Categóricas:** La columna Activity Level contenía errores de tipeo y formatos inconsistentes (Seddentary vs. Sedentary, Highly Active vs. Highly_Active, Actve), dificultando la agrupación de datos.
* **Valores Atípicos (Outliers):** Se detectó un valor máximo de ritmo cardíaco (Heart Rate (BPM)) de 296.59, el cual es fisiológicamente improbable y apunta a un claro error de medición.
Como resultado, el dataset se redujo de 10,000 a 8,295 registros, garantizando que solo la información completa, consistente y válida permaneciera.
## Librerías utilizadas

Para llevar a cabo este proceso de limpieza y análisis, fue necesario utilizar las siguientes librerías:

* pandas
* numpy
