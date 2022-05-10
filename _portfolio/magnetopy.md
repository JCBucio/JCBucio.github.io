---
layout: post
title: MagnetoPy
img: "assets/img/portfolio/magnetic-field.png"
date: 08-04-2022
tags: [Portafolio]
excerpt_separator: <!--more-->
permalink: /portafolio/MagnetoPy
---
![image]({{ "assets/img/portfolio/magnetic_field.jpg" | relative_url }})

_MagnetoPy_ es una _CLI_ (Command Line Interface) de Python que procesa datos de campo magnético provenientes de estaciones en campo y estaciones base para obtener la variación diurna así como los valores de intensidad del campo magnético provenientes del _IGRF_.<!--more--> Escribí _MagnetoPy_ con la intención de hacer el procesamiento de datos de campo magnético mucho más fácil, rápido y eficiente.

Este proyecto lo desarrollé para mi materia de Magnetometría, donde trabajamos con instrumentos que miden la intensidad del campo magnético en un perfil de campo con el objetivo de detectar anomalías que puedan indicarnos la presencia de un objeto subterráneo o capas de distintos tipos de rocas.

<br>

## ¿Qué es el Campo Magnético Terrestre?
El Campo Magnético Terrestre (_CMT_) o Campo Geomagnético es un gran magneto con dirección norte-sur coincidente con el eje de rotación de la Tierra[^1]. Las líneas de campo que se generan por este magneto salen por el polo norte magnético y convergen en el polo sur magnético. De acuerdo a _Muniz (1997)_, el Campo Magnético Terrestre se integra por cuatro fuentes principales:

- **El campo principal**: Generado por el núcleo externo líquido de la Tierra ubicado a unos 2,900 km de profundidad aproximadamente y compuesto principalmente por Hierro (Fe) y Níquel (Ni). Se cree que las corrientes de convección de este material conductor en el núcleo actúan como un gran dínamo generando aproximadamente 90% del campo total.

- **El campo cortical**: Generado por la magnetización de las rocas en la corteza terrestre en donde las temperaturas son menores a la [_temperatura de Curie_](https://analyzing-testing.netzsch.com/es/training-know-how/glosario/temperatura-de-curie){:target="_blank" rel="noopener noreferrer"}, los minerales en esta zona son muy ricos en Hierro (Fe). Este campo es el más estable, presenta variaciones en periodos de cientos de miles de años.

- **El campo externo**: Su origen está en la interacción del viento solar con la capa magnética que envuelve la Tierra (Magnetósfera). A su vez, esta interacción se proyecta hasta la Ionósfera generando variaciones diurnas que dependen de periodos de perturbación, tormentas solares o magnetopulsaciones.

- **El campo magnético por inducción electromagnética**: Es generado por corrientes eléctricas inducidas en la corteza y manto por las variaciones externas de campo.

<br>

## ¿Qué es el IGRF?
El _IGRF_ (International Geomagnetic Reference Field) por sus siglas en inglés es un conjunto de coeficientes esféricos armónicos que pueden ser introducidos en un modelo matemático para describir la porción a gran escala y variable en el tiempo del campo magnético interno de la Tierra entre épocas desde 1900 d.C. hasta la actualidad. El _IGRF_ es calculado y producido por un grupo de trabajo internacional de científicos denominado _IAGA_ (International Association of Geomagnetism and Aeronomy). La actual decimotercera generación del _IGRF_ ha sido derivada de observaciones recopiladas por satélites, observatorios en tierra y estudios magnéticos en todo el mundo.[^2]

Las series de modelos matemáticos utilizadas para calcular el Campo Magnético Terrestre pueden representarse en la siguiente expresión:

$$
  V(r,\theta ,\phi ,t)=a\sum_{N}^{n=1}\sum_{n}^{m=0}(\frac{a}{r})^{n+1}[g_{n}^{m}cos(m\phi )+h_{n}^{m}(t)sin(m\phi )]P_{n}^{m}(cos\theta )
$$

<br>

{% include aligner.html
  images="portfolio/total-field.png,portfolio/mag-poles.png"
%}

<figcaption>Izquierda/arriba: Mapa de la intensidad total del CMT para 2020 | Derecha/abajo: Cambio de los polos magnéticos norte y sur desde 1900 d.C. <br>Fuente: International Geomagnetic Reference Field: the thirteenth generation.</figcaption>

<br>

## Utilizando _MagnetoPy_
El procedimiento que sigue _MagnetoPy_ para procesar los datos consta de recibir un archivo con los datos obtenidos de las estaciones en campo y otro archivo con los datos de las estaciones base, los archivos deben tener extensión `csv` y contar solamente con una primera línea correspondiente al nombre de cada columna seguida de los datos recopilados, las columnas mínimas necesarias de cada archivo son las siguientes:

- **Archivo estaciones**
    - _date_: Fecha de cada medición en formato `DD/MM/YYYY`.
    - _time_: Hora de cada medición en formato `HH:MM:SS`.
    - _station_: Número de estación en campo.
    - _magfield_: Intensidad de campo magnético medida en `nT` de cada estación.
    - _lat_: Latitud de la estación en coordenadas geográficas.
    - _lon_: Longitud de la estación en coordenadas geográficas.

- **Archivo estaciones base**
    - _date_: Fecha de cada medición en formato `DD/MM/YYYY`.
    - _time_: Hora de cada medición en formato `HH:MM:SS`.
    - _magfield_: Intensidad de campo magnético medida en `nT` de cada estación base.
    - _sq_: Resoluciones de cada medición (depende del instrumento).

El nombre de cada columna puede ser cualquiera ya que el programa nos permite declarar las columnas que usaremos en cada archivo, los nombres declarados arriba son una recomendación.

Aquí puedes descargar _MagnetoPy_ para comenzar a utilizarlo, también se detallan instrucciones para crear un ambiente virtual y ejecutar el programa:
- [https://github.com/JCBucio/MagnetoPy](https://github.com/JCBucio/MagnetoPy){:target="_blank" rel="noopener noreferrer"}

Con el siguiente comando corremos nuestro programa:
```
>> python magnetopy.py stationsfile.csv basefile.csv output.csv
```

Una vez que se le ha dado toda la información necesaria a _MagnetoPy_ para procesar los datos el programa realiza un _matching_ de los horarios más cercanos de mediciones en estaciones base con mediciones en estaciones móviles, asigna el valor de campo magnético a la última y calcula la variación diurna para esa medición. Veremos lo siguiente en nuestra terminal:

```
############## MAGNETIC FIELD DATA FORMATTER ##############
##                                                       ##  
##  Written by Juan Carlos Bucio (jcbucio.geo@gmail.com) ##
##               Licensed under MIT license              ##
##                                                       ##
###########################################################


--- STATIONS FILE PARAMETERS ---

Enter the columns names of the file
Date column: date
Time column: time
Stations column: station
Magnetic field column: magfield
Latitude column: gpslat
Longitude column: gpslon

Columns found!


--- BASE STATIONS FILE PARAMETERS ---

Enter the columns names of the file
Date column: date
Time column: time
Magnetic field column: nT
Resolution column: sq

Columns found!

Finding closest matches in time of base stations...

Matches and diurnal variation completed!
```

Una vez que se calcularon todas las variaciones diurnas de cada estación se solicita la intensidad del campo magnético a una _API_ (Aplication Programming Interface) del _IGRF_, a la cual se le pasarán los parámetros de nuestras mediciones para obtener medidas específicas de cada localización. El tiempo que tome este proceso puede variar bastante ya que la _API_ que se está solicitando solamente permite 50 conexiones por segundo para todos los usuarios en el mundo, debido a esto es posible que no se puedan obtener los datos solicitados si el servidor se encuentra saturado.
```
Requesting IGRF data...

10 requests completed...
20 requests completed...
30 requests completed...
40 requests completed...
50 requests completed...
60 requests completed...
70 requests completed...
80 requests completed...
90 requests completed...
100 requests completed...
110 requests completed...
120 requests completed...
130 requests completed...
140 requests completed...
150 requests completed...
160 requests completed...
170 requests completed...

170 requests completed in 1.369 minutes


--- OUTPUT FILE ---

Data succesfully saved in: output.csv

Total time spent: 2.480 minutes
```

Finalmente el programa nos da como output un archivo `csv` con el nombre que previamente asignamos, además de las columnas en nuestros dos archivos procesados también veremos los siguientes datos:

- **diff_time**: Diferencia de tiempo entre la medición de la estación móvil y la medición de la estación base.
- **base_magfield_mean**: Promedio en un día del campo magnético de las estaciones base.
- **diurnal_var**: Variación diurna de la intensidad de campo magnético para cada medición.
- **diurnal_var_corr**: Corrección por variación diurna.
- **igrf_intensity**: Intensidad total del campo magnético para cada medición proveniente del _IGRF_.
- **igrf_res_field**: Campo magnético residual calculado a partir de la intensidad total del campo magnético obtenida del _IGRF_.

<br>

## Convertir archivos GPX a CSV
Es bastante común que si no contamos con un _GPS_ al hacer nuestros levantamientos en campo tengamos que recurrir a ubicar nuestras estaciones móviles por medio de softwares como Google Earth o _SIGs_ (Sistemas de Información Geográfica) que suelen devolvernos los archivos de nuestra planeación de campo en formato _GPX_, el cual contiene las coordenadas y los números de cada una de nuestras estaciones y perfiles. Sin embargo, cuando realizamos perfiles muy extensos es tedioso buscar nuestra estación y cotejarla con la lectura de nuestro instrumento por medio de los softwares anteriormente mencionados, para resolver este problema añadí un pequeño programa llamado `gpx_converter.py` que puedes encontrar en el repositorio de _MagnetoPy_. Para utilizar este convertidor de archivos gpx a csv solo necesitamos instalar el paquete [gpxpy](https://github.com/tkrajina/gpxpy){:target="_blank" rel="noopener noreferrer"} dentro de nuestro ambiente virtual de la siguiente manera:

```
>> conda install -c conda-forge gpxpy
```

Una vez que tenemos el paquete instalado podemos convertir cualquier archivo gpx a csv con el siguiente comando:

```
>> python gpx_converter.py file.gpx output_file.csv
```

Veremos un output como el siguiente:

```
Data saved in: output_file.csv
```

Las columnas que podremos ver en nuestro archivo csv son las siguientes:

- **route**: Número de nuestra ruta, esto es en el caso de que nuestra planeación de estaciones tenga múltiples líneas de perfiles.
- **station**: Número de nuestra estación en el perfil (ruta) correspondiente.
- **latitude**: Latitud en coordenadas geográficas.
- **longitude**: Longitud en coordenadas geográficas.

<br>

### Mejoras futuras
_MagnetoPy_ sigue en desarrollo y es posible que tenga algunos pequeños errores si no se introducen los datos de manera correcta, sigo trabajando para hacer esta _CLI_ mucho más sencilla y rápida de utilizar.

<br>

#### Comentarios, sugerencias y opiniones
_Si tienes algún comentario, sugerencia u opinión házmelo saber en los comentarios de abajo, no requieres de ninguna cuenta, sólo elige un nombre de usuario (puede ser tu nombre) y un correo (opcional). Todos los comentarios son enviados a un moderador, por lo tanto tardarán un poco en publicarse._

<br>

[^1]: {% include citation.html key="magfield" %}
[^2]: {% include citation.html key="igrf-13" %}
