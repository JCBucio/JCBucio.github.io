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

Mini proyecto personal que consiste en un programa que establece una conexión con una _API_ (Aplication Programming Interface) la cual rastrea y nos da la posición exacta de la _ISS_ en tiempo real, así como los astronautas que se encuentran en el espacio.<!--more--> Este pequeño programa cuenta con una interfaz sencilla hecha con **HTML** y **JavaScript** para visualizar en un mapa el movimiento de la _ISS_.

<br>

## ¿Qué es la ISS?
La _ISS_ (International Space Station) por sus siglas en inglés es el objeto en el espacio más grande construido por el ser humano, se trata de un proyecto internacional con agencias espaciales de todo el mundo, el primer módulo de la estación lanzado al espacio fue el módulo ruso _Zarya_ el 20 de noviembre de 1998. Una gran cantidad de módulos fueron enviados al espacio y acoplados en los años siguientes hasta su último módulo acoplado en 2011 con el vuelo final del _Programa del Transbordador Espacial_ en el orbitador _Discovery_. Desde entonces se han hecho pequeñas modificaciones para mantener la estación en uso continuo.

{% include aligner.html
  images="portfolio/proton.jpg,portfolio/discovery.jpg"
%}

<figcaption> Izquierda/arriba: Cohete ruso Proton. | Derecha/abajo: Transbordador espacial americano Discovery. </figcaption>

<br>

La _ISS_ orbita la Tierra a alrededor de 400 km de altura a una velocidad aproximada de 27,600 km/h, es decir, la estación viaja a 7 kilómetros por segundo. Esto quiere decir que la estación le da una vuelta entera a la Tierra cada 90 minutos, así es, los astronautas que se encuentran en la estación ven un amanecer cada 45 minutos y un atardecer en el mismo tiempo.

El programa en el que trabajé establece una conexión con una _API_ (Aplication Programming Interface), la cual nos permite programar consultas de manera automática para obtener información en tiempo real. En este caso la _API_ que utilicé es [Open Notify](http://open-notify.org/Open-Notify-API/){:target="_blank" rel="noopener noreferrer"} creada por Nathan Bergey. Si quieres leer más acerca de las *APIs* te dejo este post en el que se explica de manera detallada su funcionamiento y aplicaciones:

- [Red Hat. ¿Qué es una API?](https://www.redhat.com/es/topics/api/what-are-application-programming-interfaces){:target="_blank" rel="noopener noreferrer"}

<br>

### Cross-Origin Resource Sharing (CORS)
Al generar la interfaz visual con **HTML** y **JavaScript** tuve problemas al solicitar los datos de la _API_ debido a un problema muy común llamado **Cross-Origin Resource Sharing** (CORS). Esto sucede cuando una página web solicita datos de otra página web que no es de su propiedad de manera que el navegador no puede acceder a esos datos. Para arreglar este problema desarrollé una _API_ propia que solicita los recursos necesarios y los devuelve en formato `JSON` permitiendo las solicitudes `http` consideradas como _cross-origin_ (fuera de su propiedad).

Esta pequeña _API_ está programada con [Flask](https://flask.palletsprojects.com/en/2.1.x/){:target="_blank" rel="noopener noreferrer"}, un framework de *Python* para crear aplicaciones web de manera sencilla y muy minimalista. De esta manera la interfaz de mi programa se conecta directamente a mi *API* y obtiene los datos necesarios para visualizarlos. Aquí puedes obtener más información sobre el manejo de CORS:

- [MDN Web Docs. Cross-Origin Resource Sharing (CORS)](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS){:target="_blank" rel="noopener noreferrer"}

<br>

## ISS Tracker
Aquí podemos visualizar el movimiento de la _ISS_ en un mapa en tiempo real, así como la cantidad de astronautas en el espacio junto con el vehículo en el que se encuentran actualmente. La razón de que en la información se incluya el vehículo es debido a que en órbita también se encuentra la estación espacial china [Tiangong](https://en.wikipedia.org/wiki/Tiangong_space_station){:target="_blank" rel="noopener noreferrer"}, la cual también suele albergar astronautas, o *taikonautas* de la [Agencia Espacial China](http://www.cnsa.gov.cn/english/){:target="_blank" rel="noopener noreferrer"} (CNSA, por sus siglas en inglés).

<iframe title="ISS Javascript Tracker"
    width='100%' height='800px' scrolling='no' frameborder='0'
    src="https://jcbucio.github.io/iss-javascript-tracker">
</iframe>

Es posible que en un futuro cercano también se incluya la información de *cosmonautas* de la Agencia Espacial Federal de Rusia (*Roscosmos*) que sean enviados al espacio a su propia estación espacial que se encuentra todavía en desarrollo.

**NOTA:** No se incluye el sitio web de la Agencia Espacial Federal de Rusia debido a que está bloqueado en múltiples países por conflictos políticos.

<br>

### Mejoras futuras
Sabemos que la estación viaja a una gran velocidad y por lo tanto cambia de posición de una manera constante, debido a esto quiero graficar la trayectoria de la _ISS_, por medio del cálculo de su trayectoria podría trabajar en una alerta que me indique cuándo pasará cerca de una ubicación dada al programa.

<br>

#### Comentarios, sugerencias y opiniones
_Si tienes algún comentario, sugerencia u opinión házmelo saber en los comentarios de abajo, no requieres de ninguna cuenta, sólo elige un nombre de usuario (puede ser tu nombre) y un correo (opcional). Todos los comentarios son enviados a un moderador, por lo tanto tardarán un poco en publicarse._
