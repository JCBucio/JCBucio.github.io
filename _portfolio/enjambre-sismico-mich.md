---
layout: post
title: Gráfica 3D del enjambre sísmico en Michoacán
img: "assets/img/portfolio/3d-modeling.png"
date: 13-11-2022
tags: [Portafolio]
excerpt_separator: <!--more-->
permalink: /portafolio/enjambre-sismico-michoacan
---
![image]({{ "assets/img/portfolio/secuencia-mich-2021.png" | relative_url }})

*Web app* elaborada con las librerías [Plotly](https://plotly.com/){:target="_blank" rel="noopener noreferrer"} y [Dash](https://plotly.com/dash/){:target="_blank" rel="noopener noreferrer"} de **Python** para visualizar los enjambres sísmicos ocurridos en Michoacán de 2019 a 2022 mediante una gráfica 3D.<!--more--> Esta web app es una herramienta para la caracterización de la actividad sísmica que podría estar asociada al movimiento de magma debajo de la superficie en las cercanías del Pico de Tancítaro y el volcán Paricutín en Michoacán, México.

<br>

## Plotly, Dash y Plotly Express
[Plotly](https://plotly.com/){:target="_blank" rel="noopener noreferrer"} es una organización *open source* que desarrolla las librerías [Dash](https://plotly.com/dash/){:target="_blank" rel="noopener noreferrer"} y [Plotly Express](https://plotly.com/python/plotly-express/){:target="_blank" rel="noopener noreferrer"}, utilizadas ampliamente en el mundo de la ciencia de datos. Además de las librerías *open source*, Plotly ofrece un paquete empresarial llamado [Dash Enterprise](https://plotly.com/dash/){:target="_blank" rel="noopener noreferrer"} que proporciona un conjunto de herramientas para la creación de aplicaciones web interactivas y *dashboards* más complejas.

**Dash** es una librería ó _framework_ bastante popular por ser _low-code_, es decir, que permite la creación de _data apps_ de una manera rápida y sencilla en una variedad de lenguajes como Python, R, Julia y F# (experimental). Dash está escrito sobre [Plotly.js](https://plotly.com/){:target="_blank" rel="noopener noreferrer"} y [React.js](https://reactjs.org/){:target="_blank" rel="noopener noreferrer"}, lo cual lo hace ideal para construir y desplegar *data apps* con interfaces de usuario personalizables en un ambiente de desarrollo adecuado para cualquier persona que trabaje con datos.

**Plotly Express** es una librería de visualización de datos interactiva que permite crear gráficas, mapas y aplicaciones web de manera rápida y sencilla. Plotly está escrita sobre [D3.js](https://d3js.org/){:target="_blank" rel="noopener noreferrer"} y [stack.gl](http://stack.gl/){:target="_blank" rel="noopener noreferrer"}, cuenta con más de 40 tipos de gráficas, incluyendo figuras 3D, gráficas estadísticas, financieras, mapas SVG, entre otros.

{% include aligner.html images="portfolio/plotly-logo.png" %}
<figcaption>Plotly logo.</figcaption>

## Datos sísmicos
Los datos sísmicos utilizados en esta *web app* fueron obtenidos del [Servicio Sismológico Nacional](https://www.ssn.unam.mx/){:target="_blank" rel="noopener noreferrer"} (SSN) de la [Universidad Nacional Autónoma de México](https://www.unam.mx/){:target="_blank" rel="noopener noreferrer"} (UNAM). Las descripciones de las secuencias sísmicas que se incluyen a continuación son parte de los reportes especiales del SSN titulados **"Secuencia sísmica del 5 de enero al 10 de marzo de 2020 Michoacán (M 4.1)"** y **"Secuencia sísmica del 30 de mayo al 3 de septiembre de 2021 Michoacán (M 4.1)"**, los cuales pueden ser descargados en el portal del SSN, dentro de la sección de reportes especiales.

Del 5 de enero al 10 de marzo de 2020 el *SSN* reportó una secuencia sísmica con 3,294 sismos localizados en las cercanías de Uruapan, en el estado de Michoacán. La extensión de dicho enjambre abarcó una circunferencia de alrededor de 25 km de radio centrada en las coordenadas 19.50°N y 102.12°W. Posteriormente, la sismicidad comenzó a migrar al oeste, por lo que se modificó la circunferencia de búsqueda a un radio de 30 km con centro en las coordenadas 19.43°N y 102.17°W. Los sismos de mayor magnitud de la secuencia fueron de magnitud 4.1.

En 2021, entre el 30 de mayo y el 3 de septiembre, el *SSN* reportó 1,083 eventos que conforman otro enjambre sísmico. Los sismos registrados se encuentran en una circunferencia de 30 km de radio centrada en las coordenadas 19.43° latitud N y 102.17° longitud W. El sismo de mayor magnitud de la secuencia fue de magnitud 4.1.

<br>

{% include aligner.html
  images="portfolio/secuencia-mich.png,portfolio/secuencia2-mich-2021.png"
  column=2
%}
<figcaption>Izquierda: Epicentros de los sismos que conforman la secuencia sísmica del 5 de enero al 10 de
marzo de 2020 en Michoacán. Estos sismos fueron obtenidos al consultar el catálogo del SSN
(http://www2.ssn.unam.mx:8080/catalogo/) utilizando una circunferencia de 30 km de radio
centrada en las coordenadas 19.43° latitud N y 102.17° longitud W. | Derecha: Epicentros de los sismos que conforman la secuencia sísmica del 30 de mayo al 3 de
septiembre de 2021. Estos sismos fueron obtenidos al consultar el catálogo del SSN
(http://www2.ssn.unam.mx:8080/catalogo/) utilizando una circunferencia de 30 km de radio
centrada en las coordenadas 19.43° latitud N y 102.17° longitud W.</figcaption>

<br>

### Actividad sísmica en la región de Michoacán
La actividad sísmica en el estado de Michoacán es intensa. Históricamente, grandes terremotos han ocurrido a lo largo de la costa de este estado como consecuencia de la subducción de la placa de Cocos por debajo de la placa de Norteamérica.

En los años de 1999 y 2000 ocurrió otro enjambre sísmico en las cercanías del volcán Tancítaro y durante mayo a junio de 2006 se registró otra secuencia sísmica con cerca de 1,000 sismos de bajas magnitudes. Los resultados de los análisis de dicho enjambre concluyeron que los sismos fueron originados por un cuerpo magmático que se estaba elevando a cierta profundidad en las cercanías del volcán Tancítaro (Pinzón, et. al., 2017).

Más recientemente, entre enero y marzo de 2020 se presentó una intensa actividad sísmica en la región cercana a Uruapan, Michoacán. Se registraron miles de sismos, muchos de los cuales fueron muy pequeños para ser localizados. Sin embargo, se localizaron 3,666 en esa región durante esas fechas.

{% include aligner.html images="portfolio/placas.png" column=1 %}
<figcaption>Placas tectónicas que interactúan en el territorio mexicano. Recuperado del reporte especial del SSN titulado "Secuencia sísmica del 30 de mayo al 3 de septiembre de 2021 Michoacán (M 4.1)".</figcaption>

<br>

## Topografía
La topografía utilizada en esta *web app* fue obtenida de la plataforma [OpenTopography](https://www.opentopography.org/){:target="_blank" rel="noopener noreferrer"} con una resolución de 150m. Debido a que el archivo `.xyz` tenía un tamaño de varios Mb que podían relentizar la carga de la información en la plataforma, se decidió aplicarle un interpolado que mantuviera la misma resolución de la topografía pero convertido a un archivo binario `.nc`, de esta forma se logró reducir el tamaño del archivo a menos de 1 Mb. La interpolación de la topografía, así como su conversión a binario se realizó por medio de la herramienta para línea de comandos [grdsample](https://gmt.soest.hawaii.edu/doc/latest/grdsample.html){:target="_blank" rel="noopener noreferrer"} de [Generic Mapping Tools](https://www.generic-mapping-tools.org/){:target="_blank" rel="noopener noreferrer"}. A continuación se muestra el comando utilizado para realizar la conversión:

```
$ gmt grdsample tancitaro_sampled_150m.xyz -T -Gtancitaro_sampled_150m.nc
```

Donde `tancitaro_sampled_150m.xyz` es el archivo de topografía obtenido de *OpenTopography* y `tancitaro_sampled_150m.nc` es el archivo binario de topografía que la herramienta `grdsample` genera después de realizar la interpolación.

Para leer los datos y poder añadir la capa de topografía a la gráfica 3D se utilizó la librería de *Python* [netCDF4](https://pypi.org/project/netCDF4/){:target="_blank" rel="noopener noreferrer"} que permite leer archivos `.nc` y utilizar los datos para añadir una superficie tridimensional a la gráfica.

<br>

## Modelo 3D
Para realizar la graficación de los datos sísmicos y de topografía se utilizaron los módulos `go.Scatter3d` y `go.Surface` de *Plotly* respectivamente en la misma figura, de manera que pudieran ser apreciables las ubicaciones de los sismos en los 3 ejes (x, y, z). Adicionalmente, *Plotly* nos permite desplegar los datos de un punto específico en la topografía, o bien de un sismo en específico al pasar el cursor sobre el punto en la gráfica. Para poder interactuar mejor con la gráfica se puede visualizar directamente en el link del sitio: [https://enjambre-sismico-mich.onrender.com/](https://enjambre-sismico-mich.onrender.com/){:target="_blank" rel="noopener noreferrer"}

<iframe title="Enjambre sísmico Michoacán 2019-2022"
    width='100%' height='1000px' scrolling='no' frameborder='0' style="background: #FFFFFF;"
    src="https://enjambre-sismico-mich.onrender.com/">
</iframe>

<br>

### Lectura de datos
Los datos de sismicidad se almacenan en formato `.csv` y son leídos por medio de la librería de *Python* [pandas](https://pandas.pydata.org/){:target="_blank" rel="noopener noreferrer"}, para graficar esta información se utilizaron las columnas de latitud, longitud y profundidad proporcionadas por el *SSN*. Los datos de topografía se leen por medio de la librería [netCDF4](https://pypi.org/project/netCDF4/){:target="_blank" rel="noopener noreferrer"}, en el caso de la topografía, por tratarse de una superficie, la manera de leer los datos difiere un poco a los sismos, en este caso se pasa a la gráfica un *grid* con los valores de elevación interpolados para que se pueda generar la capa de topografía en 3D.

<br>

### Interacción con la gráfica
Una de las ventajas de *Plotly* y *Dash* es que nos proporcionan componentes prediseñados para poderlos integrar en nuestra gráfica de manera que el usuario pueda interactuar con la misma. En este modelo 3D se añadieron las siguientes componentes:

- `dcc.DatePickerRange`: Permite seleccionar un rango de fechas para poder visualizar los sismos que se han registrado en ese periodo de tiempo.

- `dcc.Slider`: Permite seleccionar un valor para exagerar las elevaciones de la topografía.

- `dcc.RangeSlider`: Permite seleccionar un rango de magnitudes para poder filtrar los sismos dentro de los parámetros establecidos.

Además de estos componentes, es posible desactivar las capas para ocultar la topografía o los sismos, también se incluye un pequeño contador en la parte superior derecha que nos proporciona la cantidad de sismos que se están visualizando en ese momento.

<br>

### Despliegue de la app
Para desplegar la aplicación se utilizó la plataforma [Render](https://render.com/){:target="_blank" rel="noopener noreferrer"}, esta plataforma nos permite desplegar aplicaciones web de manera gratuita y con un tiempo de respuesta bastante rápido. Para poder desplegar la aplicación, *Render* nos da la opción de conectar nuestro [repositorio de *Github*](https://github.com/JCBucio/enjambre-sismico-mich){:target="_blank" rel="noopener noreferrer"} y así, poder desplegar la aplicación cada vez que se hagan cambios al código fuente.

<br>

#### Comentarios, sugerencias y opiniones
_Si tienes algún comentario, sugerencia u opinión házmelo saber en los comentarios de abajo, no requieres de ninguna cuenta, sólo elige un nombre de usuario (puede ser tu nombre) y un correo (opcional). Todos los comentarios son enviados a un moderador, por lo tanto tardarán un poco en publicarse._