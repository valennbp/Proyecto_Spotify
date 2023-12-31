# Canciones de Spotify más reproducidas (2023)


# Presentación 
Esta presentación tiene como objetivo mostrar la información recopilada a partir del conjunto de datos sobre las canciones más reproducidas en Spotify en 2023, así como las conclusiones derivadas del análisis y algunas visualizaciones que hemos creado utilizando Power BI.

**offline!**
[Canciones de Spotify más reproducidas - Presentación de Google](https://docs.google.com/presentation/d/1psP1eN9Bo0_F0PMBVNjjUig4YjR1byk9/edit?usp=sharing&ouid=106301975252750619883&rtpof=true&sd=true)

## Descripción del proyecto

El objetivo principal de este dataset es analizar y comprender las tendencias y características de las canciones populares de 2023 en Spotify y otras plataformas de música, identificando las canciones más populares de cada plataforma, explorando el impacto de cada plataforma y identificar artistas destacados.

## Queries y Scripts de Phyton usados

Para llevar a cabo este proyecto, utilizamos Google Colab y Python, aprovechando varias bibliotecas y scripts para manejar el conjunto de datos. Aquí está un resumen de los pasos clave que seguimos

Colab: "https://colab.research.google.com/drive/15sLcZ4RKAWh1RljtSPjY3VaF7gw5d8HX?usp=sharing"

#Instalar librería para abrir datasets
!pip install opendatasets
import opendatasets as od



#Asignar link del dataset a dataset_link
dataset_link= "https://www.kaggle.com/datasets/nelgiriyewithana/top-spotify-songs-2023"
od.download(dataset_link)



#Copiar ruta de acceso de los archivos
import os
os.chdir("top-spotify-songs-2023")
os.listdir()



#Asignamos nombre al Dataframe y separamos los datos por ","
import pandas as pd
csv_path="spotify.csv"
df = pd.read_csv(csv_path,sep=",", encoding="latin-1")



#Mostramos los datos del dataset
headers = ["track_name","artist(s)_name","artist_count","released_year","released_month","released_day","in_spotify_playlists","in_spotify_charts","streams","in_apple_playlists","in_apple_charts","in_deezer_playlists","in_deezer_charts","in_shazam_charts","bpm","key","mode","danceability_%","valence_%","energy_%,acousticness_%","instrumentalness_%","liveness_%,speechiness_%","x","y"]
headers
df.columns = headers
df.head()



#Calcula en general el conjunto de datos total
df.shape



#Revisamos los tipos de datos de cada valor
df.dtypes



#Verificar si existen datos duplicados
check_dup = df.duplicated().any()
print("¿Existen valores duplicados en los datos?",check_dup)
if check_dup:
  df = df.drop_duplicates()
  print("Los valores duplicados fueron eliminados")
else :
  print("No hay valores duplicados en los datos")



#Muestra las celdas vacías o en N/A de cada columna
print(df.isnull().sum())
## Enlace del Dataset elegido

El conjunto de datos utilizado para este análisis se encuentra en Kaggle y se titula "Most Streamed Spotify Songs (2023)". Puedes acceder a él a través del siguiente enlace

[Most Streamed Spotify Songs (2023) (kaggle.com)](https://www.kaggle.com/datasets/nelgiriyewithana/top-spotify-songs-2023)


# Documentación

Toda la información detallada, incluyendo conclusiones, términos técnicos aprendidos durante el proyecto, tecnologías utilizadas y otros detalles relevantes que no se incluyen en los enlaces anteriores, se encuentra en el siguiente informe o documento

https://docs.google.com/document/d/1UuFljtUq8fpGaHa-aCgetmNF4a0mVBbM/edit
