---
layout: post
title: "Exploración geofísica en La Mintzita, Michoacán"
tags: [Geofísica, Métodos eléctricos, Georadar, Magnetometría, Gravimetría, Sísmica]
author: geos
excerpt_separator: <!--more-->
permalink: /blog/:year/:title
thumbnail: "assets/img/thumbnails/la_mintzita.jpg"
feature-img: "assets/img/thumbnails/la_mintzita.jpg"
---

En esta práctica de campo realizada del 21 al 24 de junio en La Mintzita, Michoacán se aplicaron 5 métodos de exploración geofísica (Resistividad, Magnetometría, Georadar, Gravimetría y Sísmica) con el objetivo de plantear un perfil de trabajo y conocer la instrumentación de cada método así como el procesamiento e interpretación de los datos.

<!--more-->

<br>

* TOC
{:toc}

<br>

## Contexto geológico
En la zona sureste de la capital michoacana se encuentra una localidad llamada “La Mintzita”, región de diversas fallas geológicas activas que han originado [semi grabens](https://www.geovirtual2.cl/Geoestructural/gestr04f.htm){:target="_blank" rel="noopener noreferrer"} y [grabens](https://www.geovirtual2.cl/Geoestructural/gestr04f.htm){:target="_blank" rel="noopener noreferrer"} de diferentes dimensiones, que están relacionados con la alineación de la litología de la zona y con el vulcanismo monogenético en el Holoceno, viéndose afectados a su vez los estados de Michoacán y Jalisco debido a la actividad de fallas y de vulcanismo. La zona de estudio, localizada sobre el Cinturón Volcánico Transmexicano, se caracteriza por la presencia de rocas volcánicas, las cuales se relacionan estrechamente a su origen y a los procesos tectónicos posteriores que disminuyeron o aumentaron su permeabilidad.

La zona de la Mintzita está ubicada en el sistema de fallas llamado Morelia-Acambay, el cual se originó durante el Mioceno con un desarrollo de movimientos laterales izquierdos y transtensivos hace aproximadamente 6-12 Ma (Millones de años).

<br>

{% 
    include aligner.html 
    images="posts-img/mintzita_geology.png" 
    column=1 
    caption="Figura 1. Geología de La Mintzita, Michoacán. Carta E14A23. Fuente: INEGI."
%}

<br>

Las direcciones de este sistema de fallas son E-O, ENE-OSO y NE-SO. En la parte sur del área se definieron la presencia de 4 fallas normales importantes que controlan la dirección del flujo subterráneo de la zona y a ellas se asocia la presencia de manantiales y pozos. La falla normal El Águila de dirección NE-SO y que presenta un escarpe de altura máxima de 47 m. La falla normal Cointzio presenta NE-SO hasta E-O, se alinea a partir de la población de Cointzio y continúa al occidente hasta la población de La Joya de Buenavista, presenta un escarpe de más de 130 m y sobre ella se manifiestan los manantiales de Cointzio.[^1]

<br>

## Métodos de exploración geofísica

Para aplicar los métodos geofísicos en la zona de la Mintzita, se realizó un reconocimiento general para poder escoger un perfil en el cual se hizo un análisis y estudio de las condiciones y propiedades del entorno debido a su respuesta con las diferentes técnicas aplicadas. Se escogió un perfil de dirección O-E que empieza en el final de la propiedad donde se nos permitió trabajar, sigue un pequeño camino que atraviesa perpendicular a un gasoducto del cual se conoce su ubicación ya que hay señalizaciones que indican la sección en la que se puede encontrar y así evitar que ese espacio sea perforado.

<br>

{% 
    include aligner.html 
    images="posts-img/perfil_oersted.png" 
    column=1 
    caption="Figura 2. Perfil de estudio Oersted (distancia de 175 m) Fuente: Google Earth."
%}

<br>

### Método de resistividad
El [método de resistividad](https://geologiaweb.com/geofisica/resistividad-electrica/){:target="_blank" rel="noopener noreferrer"} forma parte de los métodos eléctricos de exploración geofísica, en él, las corrientes eléctricas generadas artificialmente se introducen en el suelo por medio de electrodos y las diferencias de potencial resultantes se miden en la superficie.

Para poder realizar este método geofísico se utilizó el instrumento [*Syscal Junior*](https://www.iris-instruments.com/syscal-junior.html){:target="_blank" rel="noopener noreferrer"} con su respectiva batería de coche, además de cables de corriente los cuales se conectaron a los electrodos. Los electrodos se colocaron con una separación de 5 m entre cada uno de modo que abarcaran una distancia de 115 m con 24 electrodos.

Se configuró el software [*Electre Pro*](https://www.iris-instruments.com/download.html){:target="_blank" rel="noopener noreferrer"} de modo que se obtuvieran lecturas en los arreglos *Dipolo-Dipolo*, *Wenner* y *Wenner-Schlumberger* para que se reflejara una profundidad de ~23 m. El procedimiento anterior se realizó igual para el *Roll-along* que se tuvo que hacer para complementar el espacio sobrante del perfil (175 m) con la mitad del arreglo inicial, obteniendo un total de 36 electrodos.

Se obtuvieron un total de 743 lecturas para posteriormente ser procesadas en el software [*Earth Imager 2D*](https://www.agiusa.com/agi-earthimager-2d){:target="_blank" rel="noopener noreferrer"}. El archivo ingresado al programa se editó para ser configurado como `.urf` (Universal Resistivity Format) el cual recibe los datos de geometría de nuestros electrodos a lo largo de nuestro perfil, las configuraciones de los cuadripolos en cada medición, una columna de resistencia, otra de corriente inducida y finalmente una columna con el error asociado a cada registro.

<br>

{% 
    include aligner.html 
    images="posts-img/syscal.jpg,posts-img/andy_resistividad.jpg" 
    column=2
%}

<figcaption>Figura 3. Izquierda: Instrumento Syscal Junior de IRIS Instruments. | Derecha: Andrea Sánchez colocando los electrodos del perfil.</figcaption>

<br>

Mediante la toma de datos con los arreglos *Dipolo-Dipolo*, *Wenner* y *Wenner-Schlumberger*, con un total de 36 electrodos con una extensión de 175 m, se obtuvieron 743 lecturas en total. Por medio del software *Earth Imager 2D* se obtuvo la siguiente tomografía de resistividad eléctrica en 2D donde nos indica las mediciones de la resistividad aparente en cada pseudo sección, el cálculo de la resistividad aparente y la inversión de resistividad en la sección del perfil.

<br>

{% 
    include aligner.html 
    images="posts-img/ert_inversion_roll-along.png" 
    column=1
    caption="Figura 4. Tomografía de resistividad eléctrica en 2D, indica los valores de resistividad aparente (Ω•m) por medio del software Earth Imager 2D."
%}

<br>

Como se puede observar en la tomografía los valores de resistividad van desde los 7.6 - 500 $$\Omega \cdot m$$, donde el valor menor de 7.6 $$\Omega \cdot m$$ tiene lugar en la parte más somera (tonos azules), los valores de resistividad más bajos de la tomografía eléctrica corresponden a la constante dieléctrica baja causada por la alta humedad del subsuelo. Los valores altos de resistividad que se aproximan a los 500 $$\Omega \cdot m$$ indican estructuras del basamento cristalino en el subsuelo con profundidades aproximadas de 6 m (tonos rojizos).

No es posible visualizar el gasoducto debido a que tiene una dimensión de 88 pulgadas y el perfil tiene una separación de 5 m entre electrodos, por lo tanto la resolución de la tomografía no es suficiente para detectar este tipo de objetos. De acuerdo a las señalizaciones el gasoducto podría estar localizado entre los electrodos 10, 11 y 12.

<br>

### Magnetometría
La [magnetometría](https://geologiaweb.com/geofisica/metodo-magnetico/){:target="_blank" rel="noopener noreferrer"} es un método geofísico que mide las anomalías magnéticas del campo magnético terrrestre, permitiendo detectar objetos en el subsuelo con estas características.

Para realizar esta técnica geofísica se utilizó el magnetómetro [*GSM-19* de efecto *Overhauser*](https://gemsys.ca/spanish-landing/){:target="_blank" rel="noopener noreferrer"} que obtiene 10 muestras por segundo y tiene una resolución de 0.01 nT, se tomaron 197 lecturas ya que cada medición se realizó con 1 m de separación desde el inicio del perfil hasta el final.

El armado del equipo consistió en colocar un magnetómetro a una altura de 2 m, otro magnetómetro a 1 m del primero y un sensor *GPS* a 50 cm del segundo magnetómetro, dando una altura total de 3.5 m. La finalidad de que se colocaran dos magnetómetros fue poder obtener un gradiente que pueda detectar mejor las anomalías a identificar. Se consideró también que al momento de tomar las lecturas hubiera un aumento en el valor de los datos cuando se pasaba cerca de construcciones con objetos metálicos (bardas de concreto, casa habitacional, varillas, etc.) o si se pasaba por debajo de postes con cables de luz que alimentan las casas de la zona.

Dentro de la configuración del magnetómetro se tuvieron que considerar ciertos parámetros de acuerdo a la zona en que nos encontrábamos, se consideró el *datum WGS84* en la zona 14Q y se utilizó un filtro AC de 60 Hz. Las mediciones fueron realizadas por los integrantes de brigada Alejandro Maldonado y Yarco Álvarez.

<br>

{% 
    include aligner.html 
    images="posts-img/magnetometro_instalacion.jpg,posts-img/levantamiento_magnetometro.jpg" 
    column=2
%}

<figcaption>Figura 5. Izquierda: Instalación del magnetómetro GSM-19 por miembros de la brigada Oersted | Derecha: Alejandro Maldonado y Yarco Álvarez tomando mediciones de campo magnético.</figcaption>

<br>

Una vez obtenidos los datos del magnetómetro *GSM-19*, siendo un total de 197 lecturas, se compilaron los datos en un documento `.txt` que posteriormente fue procesado por medio de un *CLI* (Command Line Interface) llamado [MagnetoPy](https://github.com/JCBucio/MagnetoPy){:target="_blank" rel="noopener noreferrer"} escrito por Juan Carlos Bucio para poder crear un documento `.csv` donde se puedan procesar los datos de la estación base, que se obtiene del [Observatorio Magnético de Teoloyucan](http://areas.geofisica.unam.mx/magnetico/observatorio-teoloyucan.html){:target="_blank" rel="noopener noreferrer"}, y de las estaciones móviles tomadas en campo.

El documento `.csv` contiene los datos de fecha, tiempo, campo magnético total, coordenadas, elevación, error, diferencia de tiempo, variación diurna, corrección por variación diurna, intensidad del [IGRF](https://www.ngdc.noaa.gov/IAGA/vmod/igrf.html){:target="_blank" rel="noopener noreferrer"} y la intensidad del campo magnético residual. El documento `.csv` obtenido de *MagnetoPy* fue procesado en el software [*Oasis Montaj*](https://www.seequent.com/es/productos-y-soluciones/geosoft-oasis-montaj/){:target="_blank" rel="noopener noreferrer"} para utilizar los valores de corrección por variación diurna y poder obtener el siguiente modelo:

<br>

{% 
    include aligner.html 
    images="posts-img/magnetometria_primera_derivada.png" 
    column=1
    caption="Figura 6. Modelo magnético procesado con el filtro de primera derivada por medio del software Oasis Montaj."
%}

<br>

Para el modelo anterior se tuvo que procesar el mapa de corrección por variación diurna al cual se le aplicó el filtro de Primera Derivada, el cual se utiliza para resaltar fuentes someras (frecuencias altas, longitudes de onda cortas), ya que nos interesaba poder ubicar el gasoducto que cruza perpendicular al perfil y que no se encuentra enterrado muy profundo.

Se puede observar que hay valores que van desde -132,404,162.6 nT hasta 132,088,968.9 nT, y que hay una geometría tipo cilindro en color azul rey que presenta un valor magnético muy bajo, podemos interpretarlo como si éste fuera el gasoducto por el tamaño y la ubicación en el modelo y el mapa de la zona, la cual coincide con las mediciones realizadas en campo (50-60 m desde el origen del perfil), alrededor del mismo se observan anomalías muy altas porque se relacionan con las construcciones que existen cercanas al gasoducto.

<br>

### Georadar (GPR)
El [georadar ó *GPR* (Ground Penetrating Radar)](https://www.ocsa-geofisica.com/georadar.html){:target="_blank" rel="noopener noreferrer"}  por sus siglas en inglés, es una técnica geofísica basada en la detección de pulsos electromagnéticos de corta duración (1-60 nanosegundos). Estos pulsos pueden ser detectados por una antena que produce un pulso y al mismo tiempo recibe la señal producida por el subsuelo. Este es un método ampliamente utilizado para detectar anomalías someras que van desde 3 m hasta 40 m con antenas más sofisticadas.

Para realizar este método se utilizó el instrumento [*MALA Vision*](https://www.guidelinegeo.com/product/mala-groundexplorer/){:target="_blank" rel="noopener noreferrer"} con el cual se realizaron 5 perfiles utilizando una antena de 250 MHz en la zona del perfil de la brigada (Figura 2), cada uno de ellos tenía un ancho de 2.5m - 3m. El recorrido tuvo una extensión de 136 m considerando solo una dirección lo cual permitió hacer un modelo 2D de los resultados obtenidos con el equipo, cada perfil tomó 20 minutos y en total el estudio tuvo una duración de 1 hora. Además, se tuvieron que rodear montículos de huizache por lo que los primeros tres perfiles no fueron en su totalidad rectos, a pesar de esto los datos obtenidos fueron adecuados. Finalmente, para poder procesar los datos obtenidos se utilizó el [software en línea *MALA Vision*](https://www.guidelinegeo.com/product/mala-vision/){:target="_blank" rel="noopener noreferrer"}.

<br>

{% 
    include aligner.html 
    images="posts-img/dinorah_gpr.jpg" 
    column=1
    caption="Figura 7. Levantamiento de datos por medio del instrumento MALA Vision por Luz Dinorah Martínez."
%}

<br>

Al haber procesado los archivos correspondientes 0707, 0708, 0709, 0710, 0711 con extensión `.rd3` y `.rad` en el software indicado anteriormente, se realizó el perfil 2D con georadar (Figura 8). Para realizar el procesamiento de los datos obtenidos se aplicaron 3 filtros con la finalidad de reducir el ruido y mejorar la resolución de la información. Se aplicó el filtro de señal *DC* que le resta a todos los valores el promedio de las señales obtenidas, el filtro *AGC* (Automatic Gain Control) que compensa la pérdida por la propagación de ondas basándose en la diferencia en amplitudes entre el valor promedio de la señal y el valor máximo, finalmente se aplicó el filtro de supresión de fondo que como su nombre lo indica remueve el ruido de fondo provocado por la oscilación de la antena.

<br>

{% 
    include aligner.html 
    images="posts-img/gpr.png" 
    column=1
    caption="Figura 8. Resultados obtenidos de GPR por medio del software online MALA Vision."
%}

<br>

En los primeros 35 m del perfil se detectan conjuntos de líneas superpuestas en disposición horizontal marcadas con recuadros azules que podrían estar asociadas a capas de sedimentos las cuales se pueden ver también en otras zonas del perfil, en los recuadros amarillos se delimitan puntos de difracción que suelen asociarse a estructuras de colapso como fallas o fracturas, los recuadros rojos nos indican la presencia de cimientos de una construcción que se encuentra en los últimos 30 m del perfil los cuales coinciden y finalmente el par de puntos rojos delimitan la sección en la cual debería encontrarse el gasoducto de 88 pulgadas.

<br>

### Gravimetría
La [gravimetría](https://geologiaweb.com/geofisica/metodo-gravimetrico/){:target="_blank" rel="noopener noreferrer"} es un método geosífico que mide las variaciones gravitacionales de la Tierra en un punto o en un conjunto de puntos a lo largo de un perfil o mallado de estudio, este método puede emplearse para detectar anomalías subterráneas o bien, para medir la marea terrestre.

Durante la recolección de datos para el método gravimétrico se utilizó el gravímetro *Lacoste & Romberg* Modelo G-247, se estableció un punto de medición en una de las construcciones para mantener el equipo estable y siempre tomando en cuenta que este equipo trabaja a una temperatura interna de 50.5°C con un *crosshead* de 3.2 para poder tomar los datos, que en este caso fueron para analizar la marea terrestre.

Al haber nivelado correctamente el equipo, se estableció un tiempo de dos horas y media para tomar las medidas cada 5 minutos al igual que la hora en la que se reportaban en horario *UTC*, obteniendo un total de 26 mediciones.

Posteriormente utilizamos el *GPS Garmin* para determinar las coordenadas del punto de muestreo, las cuales son 19.6413806 N, -101.281325 O; la toma de datos se hizo de manera manual, los integrantes de la brigada Alejandro Maldonado, Juan Carlos Bucio y Yarco Álvarez tomaron 5 lecturas cada uno, y Dinorah Martínez y Andrea Sánchez tomaron 8 lecturas cada una.

<br>

{% 
    include aligner.html 
    images="posts-img/lacoste-romberg.jpg,posts-img/alex_gravimetria.jpg" 
    column=2
%}

<figcaption>Figura 9. Izquierda: Gravímetro Lacoste & Romberg Modelo G-247. | Derecha: Medición de la marea terrestre por Alejandro Maldonado.</figcaption>

<br>

Se sabe que la Tierra es un sólido elástico y que es afectada por fuerzas que la atraen, especialmente por factores como la posición en la que nos encontramos con respecto al Sol y a la Luna, es por ello que el planeta llega a tener una forma de equilibrio dependiendo de la gravedad y de las fuerzas que se generan.

Entonces, al haberse colocado un gravímetro sobre una superficie, éste registra las variaciones periódicas de la gravedad que se encuentra influenciada por la atracción del Sol y la Luna haciendo que la Tierra se distorsione generando un pequeño desequilibrio en el equipo de medición; este fenómeno pudo observarse en el gravímetro *Lacoste & Romberg*, el cual es de alta precisión. Al obtener las mediciones, se pudo identificar que desde la hora 16:31:33 *UTC* hasta las 17:37:37 *UTC* las mediciones no cambiaron de manera significativa, debido a esto se hizo la suposición de que nos encontrábamos en uno de los valles de la variación semiduirna gravitacional, ya que durante el tiempo 18:24:17 *UTC* los valores comenzaron a aumentar. Este fenómeno se pudo identificar gracias al procesamiento realizado con el [software *TSoft*](http://seismologie.oma.be/en/downloads/tsoft){:target="_blank" rel="noopener noreferrer"} el cual nos muestra el rango en el que los valores obtenidos con el gravímetro coinciden con la gráfica (Figura 9).

<br>

{% 
    include aligner.html 
    images="posts-img/marea_terrestre.png" 
    column=1
    caption="Figura 9. Resultados levantamiento gravimétrico procesados con el software Tsoft."
%}

<br>

### Sísmica
La [sísmica ó sísmica de prospección](https://geologiaweb.com/geofisica/metodos-sismicos/){:target="_blank" rel="noopener noreferrer"} es un método geofísico que consiste en generar ondas sísmicas por una fuente artificial controlada (por el golpe de un mazo, ruido sísmico, etc.) que se propagan a través del subsuelo. La sísmica de prospección mide las velocidades de propagación de las ondas en el subsuelo con la finalidad de detectar cuerpos de distintas composiciones.

Durante el levantamiento de este método se empleó el [sismógrafo *ES-3000* de *Geometrics*](https://www.geometrics.com/product/es-3000-exploration-seismograph/){:target="_blank" rel="noopener noreferrer"} con una configuración de 24 geófonos de 4.5 Hz y una separación de 5 m a lo largo de una línea de 115 m iniciando al final de nuestro perfil, esto con la intención de intersectar el perfil de la brigada *Las Metamórficas* con dirección N-S. La toma de los datos se realizó por medio del método *MASW* (Multichannel Analysis of Surface Waves) que como su nombre lo indica, se caracteriza por registrar las ondas sísmicas superficiales producidas por el golpe del mazo en puntos preestablecidos. Las ubicaciones de cada trigger producido por el golpe se establecieron en los siguientes puntos: 5 m antes de g1 (g1=geófono 1), g1, g6, g12-g13, g18, g24 y 5 m después de g24.

Para registrar los datos se utilizó el software [*Surface Wave Wizard*](https://www.geometrics.com/software/seisimager-sw/){:target="_blank" rel="noopener noreferrer"} donde se especifica la configuración del perfil, la separación entre geófonos y la ubicación de los triggers en cada lectura.

<br>

{% 
    include aligner.html 
    images="posts-img/yarco_sismica.jpg" 
    column=1
    caption="Figura 10. Yarco Álvarez realizando levantamiento de datos sísmicos."
%}

<br>

El análisis de datos se realizó con el proceso de *MAM* (Microtremor Array Measurement) en el software [*SeisImager 2D*](https://www.geometrics.com/software/seisimager-2d/){:target="_blank" rel="noopener noreferrer"} utilizando los archivos que se obtuvieron al realizar el levantamiento, estos fueron los documentos 21 a 27 con extensión `.dat`.

En un inicio, se hizo el procesamiento tomando en cuenta que los datos se habían tomado como *MASW*, sin embargo, se observaba que el formato o la configuración que se hizo con el equipo durante el levantamiento no fue la adecuada, ya que no se detectaba una señal coherente con el tipo de procesamiento que se estaba realizando en un inicio, debido a esto, se consultó con el Dr. Luis Antonio Domínguez quien hizo la recomendación de tratar los datos como ruido sísmico.

<br>

{% 
    include aligner.html 
    images="posts-img/sismica.png" 
    column=1
    caption="Figura 11. Resultados de sísmica procesados por el método MAM con el software SeisImager 2D."
%}

<br>

Para observar los datos, se determinó una frecuencia mínima de 2 Hz ya que el software podrá escoger los puntos de amplitud máxima, al utilizarse geófonos de 4.5 Hz la energía que se registra puede variar debido a la sensibilidad del instrumento. Al haber aplicado estos parámetros con la herramienta *Surface Wave Analysis* se obtuvieron los puntos de dispersión los cuales se necesitaron para generar el modelo de velocidad aparente que se observa en la (Figura 11). El modelo se aproxima al rango de valores identificados en las barras de color gris.

<br>

## Usos y aplicaciones
Como ya se describió en este estudio, la aplicación de distintos métodos geofísicos puede ser de gran utilidad para la detección de estructuras subterráneas, la finalidad de utilizar distintos métodos es establecer la **no unicidad** de las distintas técnicas, esto se define como la imposibilidad de determinar una única solución para la existencia de un conjunto finito de datos. En pocas palabras, se requieren más métodos para respaldar los resultados de una misma técnica.

Entre las aplicaciones más comunes de los métodos de exploración geofísica se encuentran:

- Identificación de cambios en la litología del subsuelo (composición de las rocas, minerales, etc.)
- Delimitación de sistemas de fallamiento
- Prospección minera
- Prospección de hidrocarburos
- Detección de pozos acuíferos
- Aplicaciones forenses (detección de cuerpos, fosas, etc.)
- Detección de cimientos y tuberías
- Arqueología (detección de objetos antiguos, estructuras de valor histórico, etc.)

<br>

#### Comentarios, sugerencias y opiniones
_Espero que este post haya sido de interés para ti, si es así compártelo en tus redes. ¡Te lo agradecería mucho!_

_Si tienes algún comentario, sugerencia u opinión házmelo saber en los comentarios de abajo, no requieres de ninguna cuenta, sólo elige un nombre de usuario (puede ser tu nombre) y un correo (opcional). Todos los comentarios son enviados a un moderador, por lo tanto tardarán un poco en publicarse._

<br>

[^1]: {% include citation.html key="arko" %}