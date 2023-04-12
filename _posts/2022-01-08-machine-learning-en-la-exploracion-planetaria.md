---
layout: post
title: Machine Learning en la exploración planetaria
tags: [IA, Machine Learning, Deep Learning, Marte]
excerpt_separator: <!--more-->
permalink: /blog/:year/:title
thumbnail: "assets/img/thumbnails/Perseverance-Close-Up.jpeg"
feature-img: "assets/img/thumbnails/Perseverance-Close-Up-Figure_2.jpg"
---
El desarrollo de rovers autónomos ha sido clave en las misiones de exploración planetaria llevadas a cabo en los últimos años, y lo seguirá siendo durante las misiones futuras debido a su efectividad y el aprovechamiento de recursos que estas tecnologías plantean.

<!--more-->

Uno de los principales problemas de la exploración planetaria a nivel de superficie ha sido el difícil terreno por el cual se deben desplazar los rovers de exploración. Durante años, muchas de estas misiones se han visto afectadas por estos obstáculos, un ejemplo de ello fue el del rover [_Spirit_](https://solarsystem.nasa.gov/missions/spirit/in-depth/){:target="_blank" rel="noopener noreferrer"}, el cual terminó su misión de 7 años terrestres debido a que quedó atascado en la arena de Marte. Los algoritmos de *Machine Learning* ó "Inteligencias artificiales" como se les suele llamar popularmente han representado una solución oportuna para este problema.

<iframe width="100%" height="600" src="https://www.youtube.com/embed/HfdyUC0TDiM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<figcaption> Rovers Opportunity (aterrizó en 2004) y Curiosity (aterrizó en 2012) quedando momentáneamente atascados en la arena durante sus misiones de exploración en Marte. </figcaption>

<br>

### El problema y sus antecedentes
La exploración de cuerpos celestes por medio de plataformas tipo rover controladas a distancia ha sido posible desde 1970 cuando la en ese entonces Unión Soviética alunizó exitosamente su rover [*Lunojod 1*](https://es.wikipedia.org/wiki/Lunojod_1){:target="_blank" rel="noopener noreferrer"} con el objetivo de explorar y enviar las primeras imágenes de la superficie lunar de regreso a la Tierra. Fue hasta 1997 que la *NASA* logró el objetivo de poner su rover *Sojourner* de la misión [*Mars Pathfinder*](https://mars.nasa.gov/mars-exploration/missions/pathfinder/){:target="_blank" rel="noopener noreferrer"} en la superficie de Marte como una tecnología para demostrar que era posible llevar instrumentos a la superficie del planeta rojo.

Como se mencionó antes, un rover pionero en la exploración de Marte fue el *Spirit*, el cual tocó la superficie del planeta el 4 de enero del 2004. Esta plataforma tuvo un papel importante en el desarrollo de tecnologías que tendrían un impacto mayor en misiones futuras ya que al extender su vida útil de 90 días a 7 años fue posible que la plataforma permitiera explorar más allá de lo planeado y por lo tanto encontrarse con mayores problemas de desplazamiento, debido a esto fue necesario el desarrollo de un [parche en el software](https://mars.nasa.gov/mer/mission/rover-status/spirit/2004/all/#sol94){:target="_blank" rel="noopener noreferrer"} que le permitió tomar decisiones autónomas basadas en las lecturas de sus instrumentos, de esta manera la plataforma podía ser más efectiva al adentrarse en terrenos difíciles.

<iframe src='https://solarsystem.nasa.gov/gltf_embed/2370' width='100%' height='500px' frameborder='0' scrolling='no'></iframe>
<figcaption>Modelo 3D del rover de exploración Spirit. Fuente: NASA Visualization Technology Applications and Development (VTAD). Publicado: Abril 22, 2019.</figcaption>

<br>

## Aproximación con modelos de *machine learning*
Una definición muy acertada para el concepto de *machine learning* es la que se plantea en el artículo de [*Gavin Edwards "Machine Learning | An Introduction"*](https://towardsdatascience.com/machine-learning-an-introduction-23b84d51e6d0){:target="_blank" rel="noopener noreferrer"}:

> **Machine learning** is a tool for turning information into knowledge.

Como su nombre lo dice, esta tecnología se basa en modelos que aprenden conforme reciben información, mientras mayor sea la base de datos de la cual se alimenta el modelo, mejores serán sus predicciones. Ejemplos cotidianos de esta aproximación son los algoritmos que implementan redes sociales como *Twitter*, que basa sus recomendaciones en relación al número de likes, comentarios, tiempo viendo un tweet, etc. que un usuario tiene respecto a cierto tema o persona en especial. El caso del [algoritmo de *Netflix*](https://help.netflix.com/es/node/100639){:target="_blank" rel="noopener noreferrer"} también es muy interesante ya que además de basar sus recomendaciones en las películas que el usuario normalmente ve, también modifica las portadas de las películas o series que aparecen en pantalla para que sean más atractivas para el cliente en base a sus gustos. Si te interesa saber más de este algoritmo [aquí](https://medium.com/@springboard_ind/how-netflixs-recommendation-engine-works-bd1ee381bf81){:target="_blank" rel="noopener noreferrer"} puedes encontrar un análisis más detallado de su funcionamiento.

En la Geología Planetaria, estos modelos representan un avance increíble para el procesamiento de grandes cantidades de información como es el caso de las misiones con rovers de exploración planetaria, específicamente los rovers *Curiosity* y *Perseverance* que aterrizaron en 2012 y 2020 en Marte respectivamente.

<iframe src='https://mars.nasa.gov/layout/embed/model/?s=6' width='100%' height='500px' scrolling='no' frameborder='0' allowfullscreen></iframe>
<figcaption>Modelo 3D del rover de exploración Perseverance. Fuente: NASA/JPL - Caltech.</figcaption>

<br>

El mayor reto para la implementación de estos modelos es la capacidad de cómputo y la distancia para enviar y recibir datos. En la siguiente tabla se hace una comparación de las distancias y tiempos que implican establecer comunicaciones a cuerpos tan lejanos como Marte.

<div class="container" align="center">
    <table class="table">
    <thead>
        <tr>
            <th scope="col">Especificaciones</th>
            <th scope="col">Tierra - Luna</th>
            <th scope="col">Tierra - Marte</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th scope="row">Distancia</th>
            <td>~384,400 km</td>
            <td>~59,000,000 km</td>
        </tr>
        <tr>
            <th scope="row">Tiempo en comunicaciones (ida y vuelta)</th>
            <td>~3.6 segundos</td>
            <td>~9.1 minutos</td>
        </tr>
        <tr>
            <th scope="row">Tiempo de traslado</th>
            <td>4 - 5 días</td>
            <td>7 - 9 meses</td>
        </tr>
    </tbody>
    </table>
</div>
<figcaption>*La distancia a la Luna es un promedio de su órbita respecto a la Tierra</figcaption>
<figcaption>*La distancia entre la Tierra y Marte es la más corta de sus órbitas</figcaption>
<figcaption>*El tiempo de traslado a cada astro se considera tomando en cuenta las últimas misiones enviadas a ellos</figcaption>

<br>

## Soluciones con modelos de *ML*
Tomando en cuenta los retos antes mencionados, se han hecho múltiples propuestas por medio de modelos de *ML* para lidiar con el problema del desplazamiento. Es importante mencionar que las computadoras que estos vehículos cargan a bordo no suelen ser muy potentes en cuanto a su capacidad de procesamiento de datos ya que están enfocadas en recopilar información importante para ser enviada y analizada en la Tierra. Para no sobrecargar las computadoras de los rovers los modelos son entrenados en computadoras con mayor capacidad en la Tierra, posteriormente los modelos entrenados son cargados al software del rover, este proceso puede durar varias horas o incluso días dependiento de la actualización de software.

<br>

### *Deep learning* con Redes Neuronales Convolucionales
Una solución oportuna se encontró en el **deep learning**, una subcategoría del *machine learning* que basa su funcionamiento en la forma que el cerebro humano reconoce el medio que lo rodea. El *deep learning* funciona en "capas" que abstraen la información que se le introduce al algoritmo, de esta manera cada capa puede reconocer patrones en la información que se le da al modelo (imágenes, videos, texto, etc.), por medio de estos patrones el algoritmo aprende mientras recibe más y más información. Aquí podemos ver un ejemplo de cómo funciona el *deep learning* en el reconocimiento facial:

1. Se hace la detección del rostro en la imagen
2. Se analizan las características faciales por separado
3. Se comparan las características con otros rostros para encontrar patrones
4. Se realiza la predicción

![FacialRecognition]({{"https://content.codecademy.com/courses/deeplearning-with-tensorflow/what-is-deep-learning/facial_rec.gif"}})

Las **Redes Neuronales Convolucionales**, *CNN* por sus siglas en inglés, son un algoritmo de *deep learning* que como su nombre lo dice, se basa en el funcionamiento de las neuronas del cerebro humano, cada una de estas neuronas artificiales se encarga de reconocer un patrón específico, que después será complementado por las demás neuronas en la red para hacer una operación matemática llamada **convolución**, que a grandes rasgos expresa cómo una capa de nuestra red neuronal está siendo afectada por la capa procesada anteriormente, cada vez filtrando los datos con una mayor precisión en cada capa hasta obtener la predicción final. Si te interesa leer un poco más de cómo funcionan las redes neuronales puedes consultar estos 3 artículos:

- ["Introduction to Convolutional Neural Networks (CNN)" by Manav Mandal](https://www.analyticsvidhya.com/blog/2021/05/convolutional-neural-networks-cnn/){:target="_blank" rel="noopener noreferrer"}
- ["A Comprehensive Guide to Convolutional Neural Networks — the ELI5 way" by Sumit Saha](https://towardsdatascience.com/a-comprehensive-guide-to-convolutional-neural-networks-the-eli5-way-3bd2b1164a53){:target="_blank" rel="noopener noreferrer"}
- ["Neural networks made easy" by Ophir Tanz and Cambron Carter](https://techcrunch.com/2017/04/13/neural-networks-made-easy/){:target="_blank" rel="noopener noreferrer"}

<br>

## Soil Property and Object Classification (SPOC)
En 2016, el *Jet Propulsion Laboratory (JPL)* presentó un software que es capaz de identificar distintos tipos de terrenos y rocas tanto a nivel superficie como a nivel orbital por medio de imágenes. El software *SPOC* [^1], por sus siglas en inglés, está construido con redes neuronales convolucionales, gracias a este método de *deep learning* es posible que el software aprenda de una pequeña cantidad de ejemplos provistos por expertos en Geología Planetaria, para que después el modelo aplique ese procesamiento a un volumen de datos mayor y haga predicciones cada vez más acertadas.

Este software fue entrenado inicialmente con aproximadamente 700 imágenes manualmente clasificadas por expertos, estas imágenes incluyen la identificación de tipos de rocas como regolitos, arenas, rocas fracturadas, etc, y tipos de terrenos como afloramientos escarpados o con tipos de rocas predominantes, incluso puede identificar fácilmente las marcas de las ruedas en los rovers. *SPOC* es capaz de hacer clasificaciones de rocas y terrenos de hasta 30 metros de distancia del rover. Es importante mencionar que este modelo no solamente se limita a clasificar tipos de terrenos o de rocas, también se implementó una predicción para calcular el ángulo de pendiente en ciertas zonas que podrían ser peligrosas para el rover. 

El equipo que se encargó de desarrollar *SPOC* creó una página web en donde puedes leer más sobre este algoritmo, también hay una versión ligera del software que es *open-source* y puedes descargar y utilizar para algún proyecto personal:

- [SPOC website. A Deep Learning-based Terrain Classifier for Mars Rovers](https://nasa-jpl.github.io/SPOC/){:target="_blank" rel="noopener noreferrer"}
- [SPOC-Lite. Open-source software](https://github.com/nasa-jpl/spoc_lite){:target="_blank" rel="noopener noreferrer"}

<br>

### AI4Mars. Una herramienta pública para entrenar algoritmos de rovers en Marte
Como una iniciativa para involucrar al público en el desarrollo de estas nuevas tecnologías se creó [AI4Mars](https://www.zooniverse.org/projects/hiro-ono/ai4mars){:target="_blank" rel="noopener noreferrer"}, una herramienta que le permite a cualquier persona ayudar en la clasificación de tipos de rocas y terrenos para entrenar los algoritmos que ayudan a los rovers de exploración a manejar de manera completamente autónoma en los difíciles terrenos de Marte. La herramienta incluye una gran colección de imágenes tomadas en la superficie del planeta rojo, el usuario tiene indicaciones en cada imagen con las cuales puede clasificar varias características del terreno como fracturas, arenas, pendientes, etc. De esta manera es más sencillo obtener bases de datos más grandes que sirvan de entrenamiento para hacer modelos de mayor precisión, y a su vez, el público se puede familiarizar con las tecnologías que se emplean en la actualidad para la exploración planetaria.

![AI4Mars]({{ "assets/img/posts-img/ai4mars.jpg" | relative_url }})
<figcaption>Tres imágenes de la herramienta pública AI4Mars muestran diferentes tipos de terrenos marcianos mientras los diferencía por medio de un algoritmo de clasificación. Las imágenes fueron tomadas por el rover de exploración Curiosity.</figcaption>

<br>

#### Comentarios, sugerencias y opiniones
_Espero que este post haya sido de interés para ti, si es así compártelo en tus redes. ¡Te lo agradecería mucho!_

_Si tienes algún comentario, sugerencia u opinión házmelo saber en los comentarios de abajo, no requieres de ninguna cuenta, sólo elige un nombre de usuario (puede ser tu nombre) y un correo (opcional). Todos los comentarios son enviados a un moderador, por lo tanto tardarán un poco en publicarse._

<br>

[^1]: {% include citation.html key="spoc_mars" %}