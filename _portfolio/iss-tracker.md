---
layout: post
title: ISS Tracker
img: "assets/img/portfolio/space-station.png"
date: 15-06-2021
tags: [Portafolio]
excerpt_separator: <!--more-->
permalink: /portafolio/ISS-Tracker
---
![image]({{ "assets/img/portfolio/nasa-iss.jpg" | relative_url }})

Mini proyecto personal que consiste en un programa que establece una conexión con una _API_ (Aplication Programming Interface) la cual rastrea y nos da la posición exacta de la _ISS_ en tiempo real, así como los astronautas que se encuentran en el espacio.<!--more--> Este pequeño programa puede ser mejorado constantemente para que nos proporcione más datos de manera más estética por medio de una interfaz de usuario.

<br>

## ¿Qué es la ISS?
La _ISS_ (International Space Station) por sus siglas en inglés es el objeto en el espacio más grande construido por el ser humano, se trata de un proyecto internacional con agencias espaciales de todo el mundo, el primer módulo de la estación lanzado al espacio fue el módulo ruso _Zarya_ el 20 de noviembre de 1998. Una gran cantidad de módulos fueron enviados al espacio y acoplados en los años siguientes hasta su último módulo acoplado en 2011 con el vuelo final del _Programa del Transbordador Espacial_ en el orbitador _Discovery_.

{% include aligner.html
  images="portfolio/proton.jpg,portfolio/discovery.jpg"
%}

<figcaption> Izquierda/arriba: Cohete ruso Proton. | Derecha/abajo: Transbordador espacial americano Discovery. </figcaption>

<br>

La _ISS_ orbita la Tierra a alrededor de 400 km de altura a una velocidad aproximada de 27,600 km/h, es decir, la estación viaja a 7 kilómetros por segundo. Esto quiere decir que la estación le da una vuelta entera a la Tierra cada 90 minutos, así es, los astronautas que se encuentran en la estación ven un amanecer cada 45 minutos y un atardecer en el mismo tiempo.

El programa en el que trabajé establece una conexión con una _API_ (Aplication Programming Interface), las _APIs_ son aplicaciones web (en su mayoría) que nos permiten obtener información de plataformas de acceso público por medio de consultas a los servidores que soportan dichas plataformas. En este caso la _API_ que utilicé es [Open Notify](http://open-notify.org/Open-Notify-API/){:target="_blank"} creada por Nathan Bergey.

<br>

## Corriendo el programa
El programa completo se encuentra [aquí](https://github.com/JCBucio/ISS-Tracker){:target="_blank"} en mi perfil de Github, cualquiera lo puede descargar y modificarlo a su gusto, lo único que se requiere es tener Python instalado junto con algunas librerías. Para correr el programa sólo se da el siguiente comando a la terminal:

```
python iss-tracker.py
```

Este comando nos dará el siguiente output en la terminal:

```
##### PEOPLE IN SPACE:  10 #####
Mark Vande Hei  in  ISS
Oleg Novitskiy  in  ISS
Pyotr Dubrov  in  ISS
Thomas Pesquet  in  ISS
Megan McArthur  in  ISS
Shane Kimbrough  in  ISS
Akihiko Hoshide  in  ISS
Nie Haisheng  in  Tiangong
Liu Boming  in  Tiangong
Tang Hongbo  in  Tiangong


##### ACTUAL POSITION #####
Latitude:  16.5782
Longitude:  -3.8413
```

Como se puede observar, el programa nos está indicando el número total de personas en el espacio, independientemente del lugar del espacio en el que se encuentren. Después tenemos enlistados los nombres de los y las astronautas así como el vehículo en el que se encuentran al momento de correr el programa.

En este ejemplo podemos ver que hay 7 astronautas en la _ISS_, también es notable que hay 3 astronautas en la estación _Tiangong_, estación espacial lanzada al espacio hace unos pocos días por la _CNSA_ (Chinese National Space Administration). Como un dato extra tenemos las coordenadas de la posición exacta de la _ISS_ al momento de correr el programa.

Para hacer el programa más estético visualmente añadí un mapa proyectado con la librería [Dash](https://dash.plotly.com/){:target="_blank"}, cuando corremos el programa también recibiremos una advertencia de que se está utilizando un puerto de tu computador para proyectar el mapa de la ubicación de la *ISS*, ésto es lo que se imprimirá en pantalla:

```
Dash is running on http://127.0.0.1:8050/

 * Serving Flask app "iss-tracker" (lazy loading)
 * Environment: production
   WARNING: This is a development server. Do not use it in a production deployment.
   Use a production WSGI server instead.
 * Debug mode: on
```

Si corres el programa en tu computadora puede ser que el servidor sea distinto.

Para visualizar el mapa debemos copiar y pegar la dirección que nos arroja la terminal en un navegador, en este caso mi dirección es `http://127.0.0.1:8050/`, ahora podremos ver la ubicación de la _ISS_ con mayor precisión:

![iss-tracker]({{ "/assets/img/portfolio/iss-tracker.png" | relative_url }})

El punto azul dentro del mapa es la ubicación de la _ISS_ al momento de correr el programa, si ubicamos el mouse sobre el punto **Dash** nos dará las coordenadas del punto en la Tierra.

<br>

## Mejoras futuras
Sabemos que la estación viaja a una gran velocidad y por lo tanto cambia de posición de una manera constante, debido a esto quiero hacer que el programa actualice la información cada determinado tiempo para que de esta forma tengamos la posición exacta en tiempo real sin la necesidad de correr el programa de nuevo.

Otra implementación que quiero hacer a este programa es graficar la trayectoria de la _ISS_, de esta manera también podría trabajar en una alerta que me indique cuándo pasará cerca de una ubicación dada al programa.

<br>

#### Comentarios, sugerencias y opiniones
_Si tienes algún comentario, sugerencia u opinión házmelos saber en los comentarios de abajo, no requieres de ninguna cuenta, sólo elige un nombre de usuario (puede ser tu nombre) y un correo (opcional). Todos los comentarios son enviados a un moderador, por lo tanto tardarán un poco en publicarse._
