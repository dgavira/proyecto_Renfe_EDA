# proyecto_Renfe_EDA
Proyecto de Análisis y Limpieza de Datos (Data Wrangling) sobre billetes de Renfe. Preparación, exploración (EDA) y preprocesamiento de un dataset masivo para un futuro modelo de Machine Learning predictivo de precios.

# Análisis y Preprocesamiento de Datos: Precios de Renfe 🚄

Este repositorio contiene un proyecto enfocado puramente en la **limpieza, análisis exploratorio (EDA) y preprocesamiento de datos**. Es el paso previo y fundamental antes de entrenar cualquier algoritmo de Machine Learning.

## 🎯 Objetivo del Proyecto
El objetivo es transformar un conjunto de datos "en bruto" (información de búsquedas reales de billetes en la web de Renfe) en un formato numérico y limpio, listo para ser ingerido por un modelo predictivo que intente adivinar el precio de los billetes.

## 🛠️ Herramientas Utilizadas
- **Lenguaje:** Python
- **Manipulación de Datos:** Pandas, Numpy
- **Visualización:** Matplotlib, Seaborn, Plotly (para mapas interactivos)

## 🧹 El Proceso de Data Wrangling (Limpieza y Transformación)
Los datos del mundo real nunca vienen perfectos. En este proyecto se han realizado las siguientes fases clave:

1. **Tratamiento de Nulos y Duplicados:** - Se eliminaron filas duplicadas y registros con datos faltantes en columnas clave (como la clase del billete o el tipo de tarifa).
   - Los valores nulos en la columna `precio` se imputaron (rellenaron) utilizando la media estadística.
   - Se detectaron y eliminaron valores atípicos (billetes con precio de 0€).

2. **Ingeniería de Características (Feature Engineering):**
   - Las máquinas no entienden fechas en formato texto. Se extrajeron el día, mes, día de la semana y la hora exacta de salida.
   - Se calculó una nueva variable muy valiosa: el **tiempo de viaje** (restando la fecha de llegada y la de salida).
   - Se cruzó el dataset original con un archivo externo de coordenadas (`coordenadas_ciudades.csv`) para dotar al proyecto de información geoespacial.

3. **Codificación de Variables Categóricas (One-Hot Encoding):**
   - Los algoritmos matemáticos no saben leer palabras como "Turista" o "Promo". Se aplicó una técnica llamada *One-Hot Encoding*, que transforma estas categorías en nuevas columnas de ceros y unos. El dataset pasó de tener 13 columnas a 58 columnas estructuradas y listas para modelizar.

## 💡 Conclusiones del Análisis Exploratorio
Durante la exploración visual y el análisis de correlación, surgió un hallazgo muy importante para el futuro modelo:

* **El precio no depende de los números, sino de las categorías.** No se encontró ninguna correlación fuerte (superior a 0.5) entre el precio y las variables puramente numéricas (como la duración del viaje en minutos o las coordenadas de la ciudad). 
* Esto nos indica que el algoritmo que intente predecir el precio tendrá que darle mucho más peso a las variables categóricas, como el `tipo_tarifa`, la `clase` o el `tipo_tren`.
