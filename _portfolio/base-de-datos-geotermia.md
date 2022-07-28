---
layout: post
title: Mapa interactivo de Geotermia en México
img: "assets/img/portfolio/geothermal.png"
date: 29-06-2021
tags: [Portafolio]
excerpt_separator: <!--more-->
permalink: /portafolio/mapa-interactivo-de-geotermia-en-méxico
---
![image]({{ "assets/img/portfolio/geotermia.jpg" | relative_url }})

Con este proyecto realicé mi servicio social de la licenciatura, se trata de utilizar una base de datos con más de 18,000 registros de manifestaciones geotérmicas en el país y crear un mapa interactivo junto con una interfaz para actualizar la base de datos.<!--more--> La base de datos en la que estaré trabajando está construida con PostgreSQL, un programa para crear bases de datos relacionales para ser consultadas o modificadas por medio de _SQL_ (Structured Query Language), un lengüaje para solicitar o ingresar información a este tipo de bases de datos.

<br>

## ¿Qué es la Geotermia?
La Geotermia es una rama de la Geofísica que se dedica al estudio del calor interno de la Tierra, está fuertemente relacionada a la Geoquímica y ligada a la presencia de volcanes, fumarolas, aguas termales, géiseres, etc. Es, a grandes rasgos, la ciencia que estudia las fuentes y la distribución del calor desde el núcleo interno terrestre hasta la superficie. Existen muchos procesos que generan calor en el interior de la Tierra, éstos son algunos:

- **Calor latente de cristalización**: Reacciones exotérmicas de cristalización entre el núcleo interno y el núcleo externo.
- **Calor remanente de la formación planetaria**: Calor aún presente producto de las colisiones entre los residuos estelares del disco protoplanetario al formarse la Tierra.
- **Calor cinético o de rozamiento**: Energía liberada a causa del movimiento entre el núcleo externo y el manto.
- **Reacciones fisicoquímicas exotérmicas**: Se producen en el manto, la alta presión y temperatura producen cambios de fase en minerales inestables, las cuales generan calor.
- **Descomposición radiogénica de isótopos**: Las rocas ricas en elementos radioactivos como los isótopos $$^{235}$$U, $$^{238}$$U, $$^{232}$$Th, $$^{40}$$K generan un decaimiento debido a su inestabilidad, el cual produce calor.

<br>

## Base de datos relacional de Geotermia
Para liberar mi servicio social trabajé con la [Dra. Ruth Esther Villanueva](https://www.researchgate.net/profile/Ruth-Villanueva){:target="_blank" rel="noopener noreferrer"} del [IGUM](http://igum.geofisica.unam.mx/){:target="_blank" rel="noopener noreferrer"} (Instituto de Geofísica Unidad Michoacán) que se dedica al estudio de la química del agua en acuíferos y pozos en el país, la doctora junto con otros investigadores han creado una base de datos a manera de repositorio en donde se han almacenado 18,122 registros de manifestaciones termales hasta el 2019 en todo México. Dichos registros vienen de literatura de libre acceso (tesis, artículos científicos, resúmenes en congreso) y literatura gris (informes técnicos).

Este proyecto fue realizado en conjunto con mis compañeros de licenciatura Alejandro Maldonado Medina, Andrea Sánchez Ruiz, Luz Dinorah Martínez Gómez y Yarco Miriel Álvarez Olivera, junto con quienes se desarrolló la página web así como el formateo e ingreso de nueva información a la base de datos.

Para este proyecto se desarrolló una base de datos relacional que consiste en almacenar los datos de las entidades en tablas, y como su nombre lo dice, relacionarlos con los datos de otras tablas. La base de datos se desarrolló con el programa [PostgreSQL](https://www.postgresql.org/){:target="_blank" rel="noopener noreferrer"} debido a su compatibilidad con [QGIS](https://www.qgis.org/es/site/){:target="_blank" rel="noopener noreferrer"} (Sistema de Información Geográfica open source), también se utilizó [PgAdmin](https://www.pgadmin.org/){:target="_blank" rel="noopener noreferrer"} para administrar la base de datos mediante un entorno gráfico.

<br>

## Mapa interactivo
La página web que contiene el mapa interactivo fue desarrollada en [NodeJS](https://nodejs.org/es/){:target="_blank" rel="noopener noreferrer"} y [ExpressJS](https://expressjs.com), *frameworks* del lenguaje de programación *JavaScript* para crear páginas web, específicamente las lógicas de los servidores que administran las bases de datos y envían la información al cliente. Para las vistas de la página se utilizó [Bootstrap 5](https://getbootstrap.com/docs/5.0/getting-started/introduction/){:target="_blank" rel="noopener noreferrer"}, un *template* de `html` que nos permite desarrollar páginas web con una estructura limpia, sencilla y responsiva.

El mapa interactivo fue trabajado en un script de *JavaScript* por medio de un framework llamado [Leaflet](https://leafletjs.com/){:target="_blank" rel="noopener noreferrer"} que nos permite georeferenciar la información almacenada en la base de datos y enviarla al usuario en una forma más agradable y dinámica.

<br>

<iframe title="Mapa interactivo de Geotermia en México"
    width='1500px' height='800px' scrolling='no' frameborder='0'
    src="http://geotermia.geofisica.unam.mx/map#map-template" target="">
</iframe>

<br>

Para ver la página web completa puedes visitar el siguiente link: [geotermia.geofisica.unam.mx](http://geotermia.geofisica.unam.mx){:target="_blank" rel="noopener noreferrer"}

<br>

### Alcances y aplicaciones
Un gran beneficio de hacer esta información accesible para cualquiera es que se podría convertir en una fuente confiable de información para proyectos relacionados con la Geotermia o la Geoquímica en México. Tener una base de datos tan completa y con la posibilidad de seguir creciendo alentaría a instancias gubernamentales de todo el país a hacer sus datos accesibles para todos, de esta forma evitaríamos estudios o muestreos de campo repetitivos y contaríamos con un registro histórico para proyectos con un mayor alcance.

<br>

#### Comentarios, sugerencias y opiniones
_Si tienes algún comentario, sugerencia u opinión házmelo saber en los comentarios de abajo, no requieres de ninguna cuenta, sólo elige un nombre de usuario (puede ser tu nombre) y un correo (opcional). Todos los comentarios son enviados a un moderador, por lo tanto tardarán un poco en publicarse._
