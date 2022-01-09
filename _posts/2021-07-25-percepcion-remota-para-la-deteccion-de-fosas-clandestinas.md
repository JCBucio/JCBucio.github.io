---
layout: post
title: Percepción Remota para la detección de fosas clandestinas
tags: [Percepción Remota, Machine Learning, Sensores multiespectrales]
excerpt_separator: <!--more-->
permalink: /blog/:year/:title
thumbnail: "assets/img/thumbnails/decorrelation_new.jpg"
feature-img: "assets/img/thumbnails/decorrelation_new.jpg"
---

La Percepción Remota se ha planteado en varios estudios de la última década como una técnica que podría ayudar en la detección de fosas clandestinas en el país por su empleo de nuevas tecnologías como los sensores multiespectrales.

<!--more-->

La aparición de fosas clandestinas en México es un conflicto que ha ido creciendo en los últimos años, no solamente por el aumento de la corrupción y la violencia en el país, si no por el hecho de que con el paso de los años se han implementado nuevas técnicas y tecnologías, las cuales han revelado una gran cantidad de fosas y de la misma manera establecen grandes probabilidades de que existan más.

<br>

### Cifras y antecedentes
En México existe un grave problema con la desaparición de personas a causa del narcotráfico y la corrupción en todo el país. Los datos oficiales reportados por fiscalías o procuradurías de 23 estados del país desde 2006 hasta 2017 registran **1,608 fosas clandestinas** descubiertas, de las cuales se han exhumado **3,043 cuerpos** [^1].

Los estados que reportan la mayor cantidad de fosas son:

- Tamaulipas
- Guerrero
- Sinaloa
- Veracruz
- Zacatecas
- Jalisco

Estos estados representan un 70.77% del total de fosas registradas por instituciones gubernamentales. Hay que resaltar que en la recopilación de estos datos **no** todas las instancias gubernamentales de los estados del país facilitaron información al respecto, debido a "no contar con registros" ó porque "no se tiene registrada alguna fosa clandestina" [^2]. 

<br>

## ¿Qué es la Percepción Remota?
La Percepción Remota es una disciplina basada en ciencia y  tecnología que permite  desarrollar, capturar, procesar y analizar imágenes, junto con otros datos físicos de la Tierra, obtenidos  desde sensores en el espacio, sensores aerotransportados y con sensores que capturan datos de mediciones in situ [^3].

![subsidence]({{ "assets/img/posts-img/Mexico_City_subsidence.jpg" | relative_url }})
<figcaption> Múltiples mediciones del satélite Sentinel-1A adquiridas del 3-Oct-2014 al 2-Dic-2014 en donde se muestra la subsidencia de la Ciudad de México. Fuente: ESA (European Space Agency). </figcaption>

<br>

Existen muchas aplicaciones de la Percepción Remota tanto para las Ciencias de la Tierra como para cuestiones de impacto social. Algunas aplicaciones son el monitoreo de desastres como deslizamientos, inundaciones, incendios, etc. La PR también es ampliamente utilizada para estimar el crecimiento de la mancha urbana, desarrollar catastro o en el caso de este post, la detección de fosas clandestinas.

<br>

## PR para detectar fosas clandestinas
En la Convocatoria 2014 de Problemas Nacionales se desarrolló un proyecto llamado _Viabilidad de las imágenes híperespectrales para la detección de fosas clandestinas en México_ [^4] coordinado por el Dr. José Luis Silván Cárdenas, en el cual se realizaron 2 simulaciones en 2 sitios diferentes: Yautepec, Morelos, y Milpa Alta, CDMX. Se utilizaron cerdos de granja de manera que se pudiera simular de manera más cercana a la realidad los cuerpos humanos. Para dicho estudio se utilizaron un conjunto de técnicas diferentes para comprobar los resultados y comparar la información con la obtenida después de las simulaciones.

#### Caracterización de suelo
Antes y después de las simulaciones se realizan caracterizaciones físico-químicas en las que se miden las variaciones en el gradiente del suelo. Después de alrededor de cuatro meses se analiza el suelo, de entre los cambios importantes podemos encontrar los siguientes:

- Incremento de la concentración de materia orgánica
- Incremento en la concentración de nitrógeno (_N_)
- Decremento en la conductividad eléctrica

El incremento de materia orgánica y nitrógeno (_N_) se debe a la descomposición de los cuerpos, mientras que el decremento de la conductividad elétrica se explica por la reducción en la porosidad, retención de agua y el incremento de la temperatura del suelo.


#### Comparación de sensores comerciales
Algunos sensores disponibles en el mercado para el análisis híperespectral son:

- **Landsat:** Constelación de satélites con sensores multiespectrales.
- **World View SWIR:** Satélite comercial de alta resolución espacial.
- **Micro MCA12:** Cámara multiespectral para aplicaciones forestales y de agricultura de precisión.
- **AVIRIS:** Sensor híperespectral operado por el _[JPL](https://www.jpl.nasa.gov/){:target="_blank"} (Jet Propulsion Laboratory)_, cubre todo el rango óptico de onda corta (400-2500nm).
- **Pika NIR:** Cámara híperespectral, su peso de 2.7kg sin _GPS_ ni _IMU_(orientación) representa una limitación para drones pequeños.
- **OCI-F-SWIR:** Cámara híperespectral, cubre el mismo rango que la Pika NIR a menor costo y peso (820g).

#### Separabilidad con sensor óptimo
La separabilidad espectral se ve influida por el número de cuerpos que se encuentran en las fosas y el tiempo transcurrido desde el entierro, de esta forma solamente se podrían detectar con más de 3 cuerpos en dos ventanas de tiempo, la más evidente es a 30 días desde el entierro, la segunda es aproximadamente a 120 días desde el entierro dependiendo del sensor utilizado. A partir del quinto mes (día ~162) ya no se detecta reflectancia.

![sensors]({{ "assets/img/posts-img/sensors_graphs.png" | relative_url }})
<figcaption style="text-align: left;"> Análisis de separabilidad espectral de varios sensores multiespectrales (arriba) e híperespectrales (abajo). El modelo basado en PLS y SWR (SWRmodel) se muestra en ambos casos para fines de comparación. </figcaption>

<br>

#### Detección mediante modelos no lineales y _machine learning_
Con el fin de detectar hasta qué punto el modelo lineal representa una limitación en la detección se empleó un modelo de [_machine learning_](https://www.ibm.com/mx-es/analytics/machine-learning){:target="_blank"} llamado [_programación genética_](https://www.researchgate.net/publication/257527398_Programacion_Genetica_Introduccion_y_Aspectos_Generales){:target="_blank"} basada en la teoría de evolución de Darwin. En este método los individuos evolucionan a partir de operaciones genéticas de recombinación, mutación, selección, etc. para conformar otros individuos en una siguiente generación. La probabilidad de que una variable sea transferida a la siguiente generación depende, en este caso, del *índice de Kappa* (índice para evaluar la concordancia en un conjunto de datos).

#### Monitoreo térmico
Existen 2 razones por las que el suelo tiende a calentarse o enfriarse con menor rapidez cuando hay cuerpos enterrados:

- Cuando se tiene un cuerpo que aún no se ha descompuesto totalmente y en el cual hay un contenido de agua mayor que el del suelo, de esta forma existe una tendencia a conservar su temperatura.
- Tras la descompsición se quedan espacios vacíos que actúan como aislante térmico de tal forma que dichas áreas se calientan más despacio que el suelo alrededor.

![sensors]({{ "assets/img/posts-img/termic_graphs.png" | relative_url }})
<figcaption style="text-align: left;"> Análisis diferencial termográfico para tomas con un mes de diferencia con respectivo acercamiento (derecha) para el área de interés. El rectángulo rojo indica el áera de interés. </figcaption>

<br>

#### Hallazgos y mejoras
1. La detección de fosas masivas (>180kg) sería factible con cámaras multiespectrales. No es posible detectar fosas con uno o dos individuos por medio de sensores híperespectrales.
2. El tiempo de adquisición de las imágenes a partir del entierro es fundamental para una separablidad efectiva.
3. El empleo de _machine learning_ permite construir modelos que mejoran la detección con menos información (bandas en este caso).

Mejoras y correcciones:

1. Considerar detecciones en diferentes condiciones climáticas y de suelo.
2. Considerar la conjunción de técnicas de PR con técnicas geofísicas.
3. Emplear muestras humanas para hacer una simulación más cercana a la realidad, aunque esto conlleva cuestiones éticas mayores.

## Alcances y aplicaciones
La PR cuenta con una amplia gama de técnicas y tecnologías que podrían ponerse a disposición de la sociedad para aportar soluciones a conflictos como el que se plantea aquí. El uso correcto de dichas herramientas, así como encontrar nuevos alcances en los que el uso de la PR y técnicas afines puedan ser de contribución a alguna problemática significaría un gran avance científico y social.

<br>

#### Comentarios, sugerencias y opiniones
_Espero que este post haya sido de interés para ti, si es así compártelo en tus redes. ¡Te lo agradecería mucho!_

_Si tienes algún comentario, sugerencia u opinión házmelo saber en los comentarios de abajo, no requieres de ninguna cuenta, sólo elige un nombre de usuario (puede ser tu nombre) y un correo (opcional). Todos los comentarios son enviados a un moderador, por lo tanto tardarán un poco en publicarse._

<br>

[^1]: {% include citation.html key="informe_cmdpdh" %}
[^2]: {% include citation.html key="informe_ibero" %}
[^3]: {% include citation.html key="centrogeo" %}
[^4]: {% include citation.html key="informe_pr" %}
