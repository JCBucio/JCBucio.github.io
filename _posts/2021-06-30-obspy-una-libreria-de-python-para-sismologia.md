---
layout: post
title: Obspy. Una librería de Python para Sismología
tags: [Obspy, Python, Sismología, Jupyter Notebook, Matplotlib]
excerpt_separator: <!--more-->
permalink: /blog/:year/:title
thumbnail: "assets/img/thumbnails/waveform.png"
feature-img: "assets/img/thumbnails/waveform.png"
---

Obspy es una librería _open source_ de Python para procesar datos sísmicos. Acepta todo tipo de formatos de archivos, nos proporciona clientes para acceder a bases de datos e incluye rutinas de procesamiento de señales sísmicas.

<!--more-->

Cuando tenemos datos sísmicos de gran importancia que queremos procesar, o señales que deseamos limpiar, la mejor opción es utilizar Obspy ya que ofrece todo tipo de herramientas para el procesamiento de dicha información. La mayor ventaja de utilizar Obspy con Python es que es _open source_, esto nos permite editar prácticamente toda la información que tengamos a nuestra disposición y personalizarla para darle una buena presentación.

<br>

## Formatos de datos
Existen muchos formatos en los que se pueden almacenar datos sísmicos pero hay algunos que suelen ser los más comunes, éstos son algunos de ellos:
- **SAC (Seismic Analysis Code)**: Este es uno de los programas y formatos más utilizados en la comunidad científica que se dedica a la Sismología, es _open source_ y puede ser descargado desde la página de [IRIS (Incorporated Research Institutions for Seismology)](http://ds.iris.edu/ds/nodes/dmc/forms/sac/){:target="_blank" rel="noopener noreferrer"}.
- **SEED (Standard for the Exchange of Earthquake Data)**: SEED es otro de los formatos más comunes para datos sísmicos, también es _open source_ y se puede descargar desde [IRIS](https://ds.iris.edu/ds/nodes/dmc/data/formats/seed/){:target="_blank" rel="noopener noreferrer"}.
- **SEG (Society of Exploration Geophysics)**: Menos común pero utilizado ampliamente en la industria petrolera y en algunos equipos de exploración geofísica.

Obspy es capaz de leer todos estos formatos y de igual forma editarlos.

Cuando leemos estos datos Obspy los divide en `stream objects` y en `trace objects`, los primeros podrían considerarse como una lista, y los segundos como los elementos de esa lista. En Sismología, los formatos de los datos sísmicos nos arrojan la información en 3 canales, los cuales nos indican el movimiento en los ejes Norte-Sur, Este-Oeste y vertical.

Si leemos los datos de una estación sísmica en una fecha y hora determinadas y le solicitamos a Obspy que nos muestre los `trace objects` de un `stream` ésto es lo que veríamos:
```
3 Trace(s) in Stream:
IU.TUC.00.HHE | 2019-07-06T03:18:53.048393Z - 2019-07-06T03:34:53.038393Z | 100.0 Hz, 96000 samples
IU.TUC.00.HHN | 2019-07-06T03:18:53.048393Z - 2019-07-06T03:34:53.038393Z | 100.0 Hz, 96000 samples
IU.TUC.00.HHZ | 2019-07-06T03:18:53.048393Z - 2019-07-06T03:34:53.038393Z | 100.0 Hz, 96000 samples
```  
Donde:
- `IU`: Red de la estación sísmica seleccionada.
- `TUC`: Estación sísmica que proporciona los datos.
- `00`: Código del instrumento utilizado (Sismógrafo, geófono, etc).
- `HNE`, `HNN`, `HNZ`: En orden, eje Este-Oeste, eje Norte-Sur, eje vertical.

Adicionalmente tenemos la fecha y hora con el inicio y el final de los datos, así como la frecuencia en _Hz_ de la señal y el número de muestras.

<br>

## Metadatos
Cada formato de datos sísmicos contienen lo que llamamos _metadatos_, los metadatos son de vital importancia ya que nos dan información específica sobre el instrumento, la estación (ubicación, código, etc), la red sísmica, entre otra información relevante para conocer mejor los tipos de datos que vamos a manejar. Obspy nos permite ver los metadatos en cualquier formato que le demos con la función `stream.stats`, este es un ejemplo de cómo se ve:

```
network: IU
station: TUC
location: 00
channel: HH1
starttime: 2019-07-06T03:18:53.048393Z
endtime: 2019-07-06T03:34:53.038393Z
sampling_rate: 100.0
  delta: 0.01
   npts: 96000
  calib: 1.0
_fdsnws_dataselect_url: http://service.iris.edu/fdsnws/dataselect/1/query
_format: MSEED
  mseed: AttribDict({'dataquality': 'M', 'number_of_records': 417, 'encoding': 'STEIM2', 'byteorder': '>', 'record_length': 512, 'filesize': 213504})
processing: ['ObsPy 1.2.2: trim(endtime=UTCDateTime(2019, 7, 6, 3, 34, 53, 38393)::fill_value=None::nearest_sample=True::pad=False::starttime=UTCDateTime(2019, 7, 6, 3, 18, 53, 38393))']
```

Con los metadatos podemos ver información importante como la calibración del instrumento, la fuente de donde provienen los datos, el tamaño de los datos y la calidad de los mismos. Incluso existen algunos formatos como SAC que nos dan las coordenadas y elevación de la estación sísmica, entre otra información, la cual podría ser de gran importancia.

<br>

## Visualizar sismogramas con Obspy y Matplotlib
Cuando se trabaja con señales sísmicas es casi imposible saber el tipo de información con la que estamos trabajando sin antes observar los sismogramas de los eventos, viendo estas señales podemos saber mucho, podemos determinar si estamos viendo un sismo o simplemente ruido detectado por la estación.

Obspy ofrece funciones sencillas para graficar estos datos, sin embargo, la mayoría de las veces es necesario hacer un procesamiento antes de poner las señales en una gráfica que queremos presentar. Esto incluye establecer escalas, unidades de medida, remover el ruido y la respuesta del instrumento en caso de ser necesario. Para complementar las funciones que nos ofrece Obspy podemos utilizar Matplotlib, una librería de Python para graficar prácticamente cualquier información.

{% include aligner.html
  images="posts-img/obspy-ss.png,posts-img/obspy-plt-ss.png"
%}

<figcaption> Izquierda/arriba: Sismogramas de Obspy sin editar. | Derecha/abajo: Mismos sismogramas personalizados con Matplotlib. </figcaption>

<br>

Como podemos ver, el primer conjunto de sismogramas no nos dicen mucho acerca de la señal que estamos viendo, sin embargo, una vez procesada la señal, con las unidades de medida correctas y unos cuantos colores para identificar los canales se puede tener una idea mucho más amplia de lo que estos sismogramas podrían significar.

<br>

### Otras gráficas de ObsPy
Obspy no solamente ofrece la opción de graficar sismogramas, en cambio, tiene una gran variedad de gráficas que muestran información de todo tipo como globos terráqueos con las ubicaciones de los sismos o mapas con las estaciones que estemos utilizando para obtener los datos.

Una función bastante útil de Obspy es `model.get_travel_times()`, la cual nos da el tiempo que tardaron en llegar todos los tipos de ondas a estaciones seleccionadas en todo el mundo. Cuando le solicitamos a Obspy dicha información obtendremos los siguientes datos:

```
26 arrivals
	P phase arrival at 601.241 seconds
	pP phase arrival at 615.345 seconds
	sP phase arrival at 621.442 seconds
	PcP phase arrival at 646.694 seconds
	PP phase arrival at 733.993 seconds
	ScP phase arrival at 883.168 seconds
	PcS phase arrival at 889.075 seconds
	PKiKP phase arrival at 1025.516 seconds
	pPKiKP phase arrival at 1040.965 seconds
	sPKiKP phase arrival at 1046.758 seconds
	S phase arrival at 1090.620 seconds
	SP phase arrival at 1101.812 seconds
	pS phase arrival at 1107.490 seconds
	PS phase arrival at 1109.853 seconds
	sS phase arrival at 1114.891 seconds
	ScS phase arrival at 1187.056 seconds
	SKiKP phase arrival at 1233.815 seconds
	SS phase arrival at 1329.168 seconds
	PKIKKIKP phase arrival at 1865.230 seconds
	SKIKKIKP phase arrival at 2073.518 seconds
	PKIKKIKS phase arrival at 2079.311 seconds
	SKIKKIKS phase arrival at 2287.432 seconds
	PKIKPPKIKP phase arrival at 2365.752 seconds
	PKPPKP phase arrival at 2376.226 seconds
	PKPPKP phase arrival at 2387.646 seconds
	SKIKSSKIKS phase arrival at 3218.627 seconds
```

A pesar de que estos datos son muy útiles sería mucho más conveniente graficarlos para entenderlos de una mejor manera, Obspy cuenta con un estilo de gráfica llamado `.plot_rays()` el cual nos da el trayecto de todas las ondas detectadas por cada estación seleccionada en su paso por el interior de la Tierra, a este tipo de ondas se les llama _de cuerpo_ o _body waves_.

![arrivals]({{ "assets/img/posts-img/body-waves.png" | relative_url }})

Las ondas de cuerpo se dividen en 2 principales: las ondas P y las ondas S. Este tipo de ondas nos permiten conocer características importantes del interior de la Tierra, como la composición de sus capas, la profundidad de las mismas y la densidad de los materiales que conforman dichas capas. Éstas son algunas características de las ondas de cuerpo mencionadas:

- **Ondas P:** Estas ondas tienen una mayor velocidad de propagación y corresponden a cambios de volumen. Son compresibles, por lo tanto pueden atravesar sólidos, líquidos y gases. Su velocidad se calcula con la siguiente fórmula:

$$
  V_{p}=\sqrt{\frac{k+\frac{4}{3}\mu }{\rho}}
$$

Donde $$V_{p}$$ es la velocidad de la onda P, $$k$$ es el Módulo de compresibilidad, $$\mu$$ es el Módulo de rigidez y $$\rho$$ es la densidad del medio.

<br>

- **Ondas S:** Su velocidad es un 58% de la de las ondas P para cualquier sólido, corresponden a una deformación cortante (que conserva el volumen). Viajan únicamente a través de sólidos ya que los líquidos no soportan esfuerzos de corte. Su velocidad se calcula con la siguiente fórmula:

$$
  V_{s}=\sqrt{\frac{\mu}{\rho}}
$$

Donde $$V_{s}$$ es la velocidad de la onda S, $$\mu$$ es el Módulo de rigidez y $$\rho$$ es la densidad del medio.

<br>

## Fuentes y recursos
Éstas son algunas fuentes, recursos y referencias que utilicé para crear este post, si te interesa saber más del tema puedes consultarlas, incluso hay algunas `jupyter notebooks` con ejercicios para practicar el uso de Obspy.

- Instalación con distribución Anaconda: [ObsPy: A Python Toolbox for seismology/seismological observatories](https://anaconda.org/conda-forge/obspy){:target="_blank" rel="noopener noreferrer"}
- Documentación oficial: [Obspy website](https://docs.obspy.org/){:target="_blank" rel="noopener noreferrer"}
- Ejercicios con jupyter notebooks: [Remote Online Sessions for Emerging Seismologists (ROSES)](https://www.iris.edu/hq/inclass/lesson/704){:target="_blank" rel="noopener noreferrer"}

<br>

#### Comentarios, sugerencias y opiniones
_Espero que este post haya sido de interés para ti, si es así compártelo en tus redes. ¡Te lo agradecería mucho!_

_Si tienes algún comentario, sugerencia u opinión házmelo saber en los comentarios de abajo, no requieres de ninguna cuenta, sólo elige un nombre de usuario (puede ser tu nombre) y un correo (opcional). Todos los comentarios son enviados a un moderador, por lo tanto tardarán un poco en publicarse._
