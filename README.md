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



