# PROYECTO APLICADO EN ANALITICA DE DATOS 
El grupo Stanley es un consorcio financiero creado hace 50 años, una de sus áreas
corporativas es la relacionada con la mesa de mercado de capitales MD, donde los énfasis son
las inversiones en instrumentos de renta variable (acciones derivadas cuyos subyacentes son
acciones) y cuya fundación se realizó hace seis años junto con el grupo de desarrollo de
innovación de producto financieros. Estos grupos están conformados por equipos en diferentes
países que se encargan, entre otros, de analizar oportunidades de inversión, fungir como
corredores en conjunto con otras entidades financieras, analizar tendencias del mercado y
desarrollar nuevos productos de inversión y de consumo masivo financiero.

El equipo  de especialistas y asesores externos proponen la creación y desarrollo de un nuevo producto que permita la visualización histórica y a futuro de las
variables de interés relacionadas con el índice S&P 500, adicionalmente este producto debe permitir la identificación o agrupación de acciones que poseen rendimientos similares con el
ánimo de generar una diversificación de portafolios más eficiente y de esta forma poder lograr incrementar el margen de rentabilidad proveniente de las inversiones realizadas por la mesa de dinero. 

A continuación podrán encontrar los links de acceso a:

1. Presentación final de la propuesta:
[Presentación](https://my.visme.co/v/y4z4r764-n9q834#s3)

2. Herramienta:
[Dashboard](https://uniandes.sharepoint.com/sites/ProyectoFinalAnalytics/SitePages/Estructura-de-Mercado-SP%26500.aspx)

[Manual de uso]()

3. Cumplimiento de requerimientos:
[Validación de los requerimientos](https://docs.google.com/spreadsheets/d/152vxtbDjcto2DZdYNFgvnuR__Qa9SO9iTZ8wDJn4J1k/edit#gid=0)

# Desarrollo de la propuesta
En la primera parte se hace una carga y limpieza de los datos, luego el desempeño y analisis de los modelos y por último se encuentra
la parte de las predicciones. Este proceso se encuantra descrito en las siguinetes carpetas:

# Carga de los datos:
Dentro de la carpeta se encuentra el archivo "Yahoo_finance.ipynb" en este notebook se describe el proceso de cargue y actualización
de los datos. Este proceso se hace a través de una conexión con una hoja de spreadsheets para utilizarla como base de datos y guardar información de forma incremental. Primero se obtiene un primer historico y se almacena en la hoja, cada vez que se ejecuta el codigo, 
guarda  la información en ella, la convierte en un  dataframe  y la almacena. Este proceso se realiza todos los dias sobre las 
7:00 pm. 

En este dataframe encontramos todos los simbolos del S&P 500, este registro de los simbolos se hace sobre los últimos 5 dias y se 
concatena con la base guardada anteriormente. se eliminan duplicados para no incurrir en costos computacionales elevados y se obtiene 
un dataframe denominado simbolos. Finalmente se limpia la hoja de spreadsheets para comenzar de nuevo el ciclo de carga de los datos.

# Limpieza de datos:
luego de realizada la carga del dataframe y transcurrido el tiempo necesario (sobre las 7:30 pm), se conecta con la API de spreadsheets, luego abre la información actualizada y establece la fecha como el indice del dataframe. Una vez realizada esta transformaciòn se comienza a hacer el análisis exploratorio de los datos, se verifica la cantidad de datos nulos, se analiza la cantidad de datos a eliminar y se realiza la imputabilidad de variables. El proceso de imputabilidad se lleva a cabo mediante KNNImputer tomando como vecinos k=2; es decir,tomando el día anterior y posterior al dato faltante o los datos más cercanos en caso de no existir los primeros. 

Realizado el proceso de limpieza e imputación, se exporta esta data a un archivo denominado SP_500_data_clean, luego se transforman los datos obteniendo la variación porcentual y se envian a un nuevo archivo denominado SP_500_data_pct.

# Modelos y pronósticos:
Primero se hace un análisis historico mediante una descripciòn gráfica del portafolio de activos de preferencia de la mesa de mercado del grupo Stanley, luego se hace la descomposición de la serie de tiempo y hacemos el respectivo análisis de cada una de ellas mediante  estacionalidad, tendencia y ruido. posteriormente se realiza un analisis de los correlogramas y los gráficos de autocorrelación (ACF) y autocorrelación parcial (PACF) llegando a la conclusión de que las series pueden ser modeladas mediante procesos autoregresivos. Se analizan tambien los supuestos de media y desviación estándar para la estacionariedad,  ya que en algunos casos la variabilidad de los datos puede enmascarar la naturaleza de la serie y por ende, afectar la capacidad evaluativa de la prueba ADF, se aplica una suavización exponencial a la serie para poder corregir el ruido. Una vez validada la no estacionariedad de la serie se crea una función que itere n veces hasta que la serie se vuelva estacionaria teniendo en cuenta el orden de diferenciación para cada activo.

Una vez realizado el análisis anterior se procede a implementar modelos autoregresivos integrados y de promedios moviles ARIMA y SARIMAX, este proceso utilizando la data estacionarizada por capacidad computacional. Se obtienen los resultados sobre la prueba de entrenamiento y prueba. sus metricas de desempeño y su predicción a 3o días. Este mismo proceso se repite con modelos de suavizamiento exponencial HOLTER WINTER y métodos de ensamble tipo RANDOM FOREST. Como parte del análisis se encontró, basados en las métricas de desempeño que los modelos ARIMA y RANDOM FOREST, son los que muestran mejores resultados.

# Clusterización:
En este proceso se realiza el cargue de los datos obtenido en la limpieza de los datos, luego se hace el cálculo de la matriz inversa de covarianza mediante el método de GraphicalLassoCV para encontrar que variaciones de precio están relacionadas condicionalmente con otras. Teniendo en cuenta estos resultados,  se realiza la clusterización teniendo en cuanta los retornos diarios, tomando como insumo esta matriz de covarianza o matriz de similitud de cambios en los precios de cierre. 

# Dashboard:

En esta carpeta encontramos el modelado de datos a través de Power By, para la construcción del Dashboard, Las dtas obtenidas en cada uno de los resultados después de aplicar los procesos de limpieza, implementación de los modelos y sus predicciones. 

Otro recurso importante en esta carpeta es el "Manual de usuario dashboard analítico caso stanley" esté completamente equipado para explorar y aprovechar el potencial de nuestro Tablero de Control en Power BI, y que pueda hacerlo de manera efectiva y eficiente. Esperamos que encuentre este manual útil, y le animamos a que consulte con regularidad, ya que puede ser una excelente fuente de referencia conforme se familiariza con el tablero.

En esta carpeta encontraran en el archivo " Data en tiempo real.md " los links de spreadsheets en en donde se encuentran los archivos en tiempo real de cada una de las etapas para el desarrollo de la propuesta, desde la data cruda hasta el resultado de las predicciones.

# Contraste de predicciones:

En esta carpeta se encuentra los resultados de las predicciones de los modelos ARIMA y RF aplicados, constartados con los resultados reales en una proyección de 5 días.











