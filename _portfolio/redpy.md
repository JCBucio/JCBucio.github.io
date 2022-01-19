---
layout: post
title: REDPy (Repeating Earthquake Detector)
img: "assets/img/portfolio/earthquake.png"
date: 05-07-2021
tags: [Portafolio]
excerpt_separator: <!--more-->
permalink: /portafolio/REDPy
---
![image]({{ "assets/img/portfolio/redpy-logo.png" | relative_url }})

Este es un trabajo de apoyo a la investigación que consiste en utilizar un software llamado _REDPy_ para procesar datos sísmicos y detectar sismos repetitivos.<!--more--> _REDPy_ fue creado por la [Dra. Alicia J Hotovec-Ellis](https://www.usgs.gov/staff-profiles/alicia-j-hotovec-ellis?qt-staff_profile_science_products=3#qt-staff_profile_science_products){:target="_blank" rel="noopener noreferrer"}, dedicada a la investigación de la Sismología volcánica.

Este trabajo lo estuve realizando con el [Dr. Luis Antonio Domínguez](https://scholar.google.com.mx/citations?user=9mUpMwwAAAAJ&hl=en){:target="_blank" rel="noopener noreferrer"}, que se dedica a estudiar la propagación de ondas sísmicas en medios hetererogéneos, análisis de tasas de desplazamiento en zonas de subducción, y sistemas de alerta temprana.

<br>

## ¿Qué son los sismos repetitivos?
Los sismos repetitivos son un grupo particular de eventos sísmicos de una magnitud relativamente baja (usualmente no mayores a 4.0). Como su nombre los define, estos eventos suelen ocurrir con frecuencia, especialmente en zonas sísmicamente activas como son los límites de placas tectónicas, o en casos más especiales, cerca de volcanes.

La importancia de estos eventos surge a partir de la frecuencia con que suceden, gracias a ello se pueden detectar patrones dentro de una ventana de tiempo y un área delimitada. Dichos patrones son de utilidad ya que los sismos repetitivos suelen ocurrir antes de eventos sísmicos de mayores magnitudes, esto **NO** quiere decir que los sismos se puedan predecir, sin embargo, es un punto de partida para estudiar el comportamiento de estos eventos y eventualmente hacer predicciones más acertadas de la actividad sísmica que podría existir en una zona de estudio.

![Secuencia-Mich-2020]({{ "/assets/img/portfolio/secuencia-mich.png" | relative_url }})
<figcaption style="text-align: left;">Epicentros de los sismos que conforman la secuencia sísmica del 5 de enero al 10 de
marzo de 2020 en Michoacán. Estos sismos fueron obtenidos al consultar el catálogo del SSN
(http://www2.ssn.unam.mx:8080/catalogo/) utilizando una circunferencia de 30 km de radio
centrada en las coordenadas 19.43° latitud N y 102.17° longitud W.</figcaption>

<br>

## _REDPy_ como herramienta en la detección de sismos repetitivos
Debido a que los sismos de este tipo son de bajas magnitudes es complicado detectarlos por medio de computadoras, usualmente un especialista es el que los detecta y los cataloga por medio de la observación directa de los sismogramas.

_REDPy_ es un programa relativamente sencillo (ya que no cuenta con una interfaz gráfica) para detectar sismos repetitivos. Los parámetros utilizados en el programa son de bastante utilidad ya que examinan de manera cuidadosa cada sismograma y mediante un algoritmo llamado _STA / LTA_ (Short Time Average over Long Time Average) determinan si los eventos son sismos o ruido.

El programa también cuenta con la flexibilidad de ajustar los parámetros de acuerdo a nuestras necesidades, esto nos permite realizar detecciones más precisas implementando parámetros más estrictos. _REDPy_ da como output mucha información importante, dentro de los archivos más importantes que el programa nos devuelve se encuentran archivos `html` en los que se grafican los datos procesados con una librería de Python llamada [Bokeh](https://bokeh.org/){:target="_blank" rel="noopener noreferrer"}.

{% include aligner.html
  images="portfolio/bokeh.png,portfolio/cluster.png"
%}

<figcaption>Izquierda/arriba: Resumen de los sismos repetitivos detectados. | Derecha/abajo: Cluster con una familia de sismos con un índice alto de correlación.</figcaption>

<br>

## Alcances y aplicaciones
El objetivo de aprender y experimentar con este programa así como entender sus funciones es de utilidad para procesar datos de eventos sísmicos históricos, datos que en un futuro nos podrían ayudar a detectar zonas con alto peligro sísmico que deben de estar en constante monitoreo.

Otra gran aplicación de este programa se está dando en los eventos sísmicos en volcanes, producidos principalmente por el movimento del magma debajo de la superficie, lo cual nos sugiere que la detección de dichos eventos nos podría ayudar a sondear aumentos de actividad volcánica en zonas con posible actividad volcánica.

[Aquí](https://github.com/ahotovec/REDPy){:target="_blank" rel="noopener noreferrer"} podrás encontrar el código fuente de *REDPy*, así como instrucciones para instalarlo y comenzar a utilizarlo.

<br>

#### Comentarios, sugerencias y opiniones
_Si tienes algún comentario, sugerencia u opinión házmelo saber en los comentarios de abajo, no requieres de ninguna cuenta, sólo elige un nombre de usuario (puede ser tu nombre) y un correo (opcional). Todos los comentarios son enviados a un moderador, por lo tanto tardarán un poco en publicarse._
