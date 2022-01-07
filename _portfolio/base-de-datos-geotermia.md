---
layout: post
title: Base de datos Geotermia
img: "assets/img/portfolio/geothermal.png"
date: 29-06-2021
tags: [Portafolio]
excerpt_separator: <!--more-->
permalink: /portafolio/Base-de-datos-Geotermia
---
![image]({{ "assets/img/portfolio/geotermia.jpg" | relative_url }})

Con este proyecto estoy liberando mi servicio social, se trata de recopilar un conjunto de datos sobre química de agua de distintos acuíferos del país, añadirlos a una base de datos y crear una interfaz para consultar los datos.<!--more--> La base de datos en la que estaré trabajando está construida con PostgreSQL, un programa para crear bases de datos relacionales para ser consultadas o modificadas por medio de _SQL_ (Structured Query Language), un lengüaje para solicitar o ingresar información a este tipo de bases de datos.

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
Para liberar mi servicio social estoy trabajando con la [Dra. Ruth Esther Villanueva](https://www.researchgate.net/profile/Ruth-Villanueva){:target="_blank"} del [IGUM](http://igum.geofisica.unam.mx/){:target="_blank"} (Instituto de Geofísica Unidad Michoacán) que se dedica al estudio de la química del agua en acuíferos y pozos en el país, la doctora junto con otros investigadores han creado una base de datos a manera de repositorio en donde se han almacenado 18,122 registros de manifestaciones termales hasta el 2019 en todo México. Dichos registros vienen de literatura de libre acceso (tesis, artículos científicos, resúmenes en congreso) y literatura gris (informes técnicos).

Para este proyecto se desarrolló una base de datos relacional que consiste en almacenar los datos de las entidades en tablas, y como su nombre lo dice, relacionarlos con los datos de otras tablas. La base de datos se desarrolló con el programa [PostgreSQL](https://www.postgresql.org/){:target="_blank"} debido a su compatibilidad con [QGIS](https://www.qgis.org/es/site/){:target="_blank"} (Sistema de Información Geográfica open source), también se utilizó [PgAdmin](https://www.pgadmin.org/){:target="_blank"} para administrar la base de datos mediante un entorno gráfico.

Con la intención de hacer el repositorio accesible haré una interfaz web para que cualquier persona pueda hacer consultas a la base de datos relacional, y de la misma forma seguir añadiendo información para que sea una base de datos que pueda seguir creciendo.

![Diagrama Entidad-Relación]({{"/assets/img/portfolio/base_relacional.png" | relative_url }})
<figcaption style="text-align: left;">Diagrama Entidad-Relación de la base de datos de geotermia</figcaption>

<br>

## Alcances y aplicaciones
Un gran beneficio de hacer este repositorio accesible para cualquiera es que se podría convertir en una fuente confiable de información para proyectos relacionados con la Geotermia o la Geoquímica. Tener una base de datos tan completa y con la posibilidad de seguir creciendo alentaría a instancias gubernamentales de todo el país a hacer sus datos accesibles para todos, de esta forma evitaríamos estudios o muestreos de campo repetitivos y contaríamos con un registro histórico para proyectos con un mayor alcance.

<br>

#### Comentarios, sugerencias y opiniones
_Si tienes algún comentario, sugerencia u opinión házmelo saber en los comentarios de abajo, no requieres de ninguna cuenta, sólo elige un nombre de usuario (puede ser tu nombre) y un correo (opcional). Todos los comentarios son enviados a un moderador, por lo tanto tardarán un poco en publicarse._
