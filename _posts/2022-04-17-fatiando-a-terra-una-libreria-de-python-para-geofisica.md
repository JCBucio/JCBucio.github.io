---
layout: post
title: Fatiando a Terra. Una librería de Python para Geofísica
tags: [Python, Geofísica, Geodesia, Gravimetría, Magnetometría, Fatiando a Terra]
excerpt_separator: <!--more-->
permalink: /blog/:year/:title
thumbnail: "assets/img/thumbnails/fatiando-wallpaper-crop.png"
feature-img: "assets/img/thumbnails/fatiando-wallpaper.png"
---
[Fatiando a Terra](https://www.fatiando.org/){:target="_blank" rel="noopener noreferrer"} es una librería *open source* de Python que nos proporciona herramientas para el procesamiento, modelado e inversión de datos aplicados a las Geociencias. Está construida por una comunidad de geocientíficos e ingenieros de software apasionados por el buen desarrollo de herramientas que puedan ser de utilidad en la comunidad científica.

<!--more-->

> _El cómputo en la Ciencia ha evolucionado no solo porque el software lo ha hecho, sino porque nosotros, como científicos, estamos haciendo mucho más que solo aritmética de punto flotante._ Fernando Pérez, PyCon Canadá, 2012

<br>

* TOC
{:toc}

<br>

### Open Source. Una alternativa libre y descentralizada
El término **open source software** fue acuñado por [Christine Peterson en 1998](https://opensource.com/article/18/2/coining-term-open-source-software){:target="_blank" rel="noopener noreferrer"} con el objetivo de darle nombre a la idea que iría más allá de simplemente un conjunto de programas gratuitos. La idea consistía en darle nombre al conjunto de principios que proponían el desarrollo y la creación de software gratuito y de libre acceso como una manera de impulsar la descentralización del software y la creación de comunidades que se dedicaran a colaborar en la creación de herramientas que fueran de utilidad para cualquiera en internet. Los [principios de la comunidad *open source*](https://opensource.com/open-source-way){:target="_blank" rel="noopener noreferrer"} son los siguientes:

- **Transparencia**: Todos debemos tener acceso a la información y a los materiales necesarios para hacer el mejor trabajo posible, si estos recursos están disponibles podemos tomar decisiones más efectivas y comprender cómo nos afectan las decisiones en conjunto.

- **Colaboración**: Cuando somos libres de participar, podemos retroalimentar el trabajo de los demás y modificar lo que los participantes han creado, desbloqueando nuevas posibilidades. Creando proyectos en conjunto, podemos resolver problemas que nadie podría resolver por sí solo.

- **Liberación temprana y con frecuencia**: Prototipos tempranos pueden conducir a descubrimientos tempranos. Cuando somos libres de experimentar, podemos ver los problemas de maneras distintas, y a su vez, explorar diferentes respuestas.
- **Meritocracia inclusiva**: Las buenas ideas pueden venir de cualquier lugar, y las mejores ideas son las que deben permanecer. Solamente incluyendo perspectivas más diversas en nuestras conversaciones podemos estar seguros de que hemos identificado las mejores ideas.
- **Comunidad**: Las comunidades se forman de diferentes personas unidas por un propósito en común. Compartir valores guían nuestra visión hacia la toma de mejores decisiones, y las metas de una comunidad siempre se anteceden a las agendas o los intereses individuales.

<br>

## Rebanando la Tierra
El término _Fatiando a Terra_ viene del portugués _Rebanando la Tierra_, título concebido a finales del 2008 por Leonardo Uieda y Vanderlei Oliveira Jr. en la Universidad de São Paulo con la idea de desarrollar un software de código abierto para modelar el Planeta Tierra de forma completa.

<br>

{% include aligner.html images="posts-img/fatiando-logo.png" %}
<figcaption>Fatiando a Terra logo.</figcaption>

<br>

La idea de crear este software surge de implementar una alternativa propia a los software de modelado gravimétrico 2D comerciales con los que se contaban en ese entonces. El primer desarrollo del software utilizó el método de [Talwani et al. (1959)](https://doi.org/10.1029/jz064i001p00049){:target="_blank" rel="noopener noreferrer"} para modelado directo de polígonos 2D por medio del lenguaje de programación C, el cual posteriormente fue traducido a Python. A la par de este programa se desarrolló también en Python y C el algoritmo para el cálculo de campos gravitatorios de teseroides mediante la *Cuadratura de Gauss-Legendre (GLQ)*, que derivó en el lanzamiento del software *Tesseroids* [(Uieda et al., 2016)](https://doi.org/10.1190/geo2015-0204.1){:target="_blank" rel="noopener noreferrer"}.

Fue hasta 2018, que con la llegada de múltiples librerías de libre acceso creadas para el nuevo Python 3 se decidió repensar el diseño de *Fatiando a Terra* para volverlo más sustentable en el futuro. Se tomó la desición de dividir el proyecto en varios paquetes que ofrecerían funciones más específicas de acuerdo a las necesidades de la comunidad. Esto permitiría a los usuarios aprender a utilizar la librería de una manera más amigable, y a su vez, los colaboradores podían enfocarse en los paquetes que fueran de su interés en lugar de tener que entender la librería completa.

**Nota**: Las siguientes definiciones, ejemplos y fragmentos de código fueron extraídos de la tesis doctoral del Dr. Santiago Rubén Soler [^1], colaborador en el proyecto _Fatiando a Terra_.

<br>

### Verde. Procesado y grillado de datos espaciales [^2]
[Verde](https://www.fatiando.org/verde/latest/index.html){:target="_blank" rel="noopener noreferrer"} ofrece herramientas para procesar datos espaciales (datos de campo como mediciones de batimetría, topografía, altimetría, etc.) e interpolarlos sobre grillas regulares.

<br>

{% include aligner.html images="posts-img/verde-logo.png" %}
<figcaption>Verde logo.</figcaption>

<br>

La mayoría de los muestreos de datos espaciales se componen por datos irregularmente distribuidos sobre la zona de estudio, sin embargo, muchas metodologías de procesado e interpretación requieren que los datos se sitúen sobre puntos pertenecientes a una grilla regular. Este problema suele resolverse mediante la interpolación de los datos originales sobre una grilla regular, proceso que se conoce como **grillado**. Un ejemplo de un algoritmo que entra en la categoría de *interpolaciones con funciones de base radial* es el de las *splines* biarmónicas. Estos métodos asumen que podemos representar los datos observados por una combinación lineal de funciones de Green, es decir:

$$
    d_{i}=\sum_{j=1}^{M}c_{j}G(p_{i},q_{j})
$$

donde $$d_{i}$$ es el dato $$i$$-ésimo, $$p_{i}$$ es la ubicación de ese mismo punto, $$c_{j}$$ es un coeficiente escalar, $$G$$ es una función de Green y $$q_{j}$$ es la ubicación del punto que define la función de Green en el término $$j$$-ésimo. El proceso de interpolación consiste en ajustar los valores de los coeficientes $$c_{j}$$ mediante mínimos cuadrados de forma tal que se recuperen los datos observados, y luego utilizarlos para predecir valores sobre los puntos de la grilla:

$$
    d(p)=\sum_{j=1}^{M}c_{j}G(p,q_{j})
$$

donde $$p$$ es la ubicación de cualquier punto de la grilla.

Si bien estas fórmulas representan cierta complejidad podemos por medio de funciones previamente desarrolladas en *Verde* utilizarlas de una manera más sencilla sin la necesidad de expresarlas explícitamente en nuestro código. Las aproximaciones que utiliza este paquete son muy similares a las utilizadas en la librería [scikit-learn](https://scikit-learn.org/stable/){:target="_blank" rel="noopener noreferrer"} para *machine learning*. Entre los algoritmos de interpolación implementados están las *splines* biarmónicas, así como métodos más complejos como la interpolación de vectores 2D con funciones de Green. En el siguiente fragmento de código se ejemplifica el uso de la función `verde.Spline` para realizar una interpolación de datos de temperatura en Texas.

```python
import cartopy.crs as ccrs
import matplotlib.pyplot as plt
import numpy as np
import pyproj

import verde as vd

# Descargamos los datos de temperatura de Texas
data = vd.datasets.fetch_texas_wind()
coordinates = (data.longitude.values, data.latitude.values)
region = vd.get_region(coordinates)

# Usamos la proyección de Mercator para nuestra grilla Cartesiana
projection = pyproj.Proj(proj="merc", lat_ts=data.latitude.mean())

# El espaciamiento de la grilla en nuestro output será de 15 minutos de arco
spacing = 15 / 60

# Ahora podemos juntar un promedio de bloque y una función spline.
# La spline puede ser regularizada ajustando el coeficiente de amortiguamiento
# que debería ser positivo. También es una buena idea establecer la mínima
# distancia al espaciamiento promedio de datos para evitar singularidades en la spline.
chain = vd.Chain(
    [
        ("mean", vd.BlockReduce(np.mean, spacing=spacing * 111e3)),
        ("spline", vd.Spline(damping=1e-10, mindist=100e3))
    ]
)
print(chain)

# Ahora podemos evaluar la efectividad del modelo separando los datos en
# conjuntos de entrenamiento y de prueba. Usaremos el conjunto de entrenamiento
# para grillar los datos y el conjunto de prueba para validar el modelo spline.
train, test = vd.train_test_split(
    projection(*coordinates), data.air_temperature_c, random_state=0
)

# Entrenamos el modelo con el conjunto de entrenamiento
chain.fit(*train)

# Calculamos el coeficiente R^2 en el conjunto de prueba. El mejor puntaje
# posible (una predicción perfecta) es 1. Esto nos puede decir qué tan buena
# es nuestra función spline prediciendo datos que no se encontraban en la información descargada.
score = chain.score(*test)
print("\nScore: {:.3f}".format(score))

# Ahora podemos crear una grilla geográfica de la temperatura del aire
# proporcionando una función de proyección al método de grillado 
# omitiendo los puntos que están muy lejos de las observaciones.
grid_full = chain.grid(
    region=region,
    spacing=spacing,
    projection=projection,
    dims=["latitude", "longitude"],
    data_names="temperature",
)
grid = vd.distance_mask(
    coordinates, maxdist=3 * spacing * 111e3, grid=grid_full, projection=projection
)
print(grid)

# Graficamos la grilla y los puntos de nuestros datos originales
plt.figure(figsize=(8, 6))
ax = plt.axes(projection=ccrs.Mercator())
ax.set_title("Air temperature gridded with biharmonic spline")
ax.plot(*coordinates, ".k", markersize=1, transform=ccrs.PlateCarree())
tmp = grid.temperature.plot.pcolormesh(
    ax=ax, cmap="plasma", transform=ccrs.PlateCarree(), add_colorbar=False
)
plt.colorbar(tmp).set_label("Air temperature (C)")

# Usamos una función de utilidad para agregar títulos a los ejes del mapa
vd.datasets.setup_texas_wind_map(ax, region=region)
plt.show()
```
<figcaption>Interpolado de datos por medio de la función verde.Spline para el modelado de una grilla.</figcaption>

<br>

Output:
```
Chain(steps=[('mean',
              BlockReduce(reduction=<function mean at 0x7f626a6e53a0>,
                          spacing=27750.0)),
             ('spline', Spline(damping=1e-10, mindist=100000.0))])
/usr/share/miniconda3/envs/test/lib/python3.9/site-packages/verde/base/base_classes.py:359: FutureWarning: The default scoring will change from R² to negative root mean squared error (RMSE) in Verde 2.0.0. This may change model selection results slightly.
  warnings.warn(

Score: 0.856
/usr/share/miniconda3/envs/test/lib/python3.9/site-packages/verde/base/base_classes.py:463: FutureWarning: The 'spacing', 'shape' and 'region' arguments will be removed in Verde v2.0.0. Please use the 'verde.grid_coordinates' function to define grid coordinates and pass them as the 'coordinates' argument.
  warnings.warn(
<xarray.Dataset>
Dimensions:      (latitude: 43, longitude: 51)
Coordinates:
  * longitude    (longitude) float64 -106.4 -106.1 -105.9 ... -94.06 -93.8
  * latitude     (latitude) float64 25.91 26.16 26.41 ... 35.91 36.16 36.41
Data variables:
    temperature  (latitude, longitude) float64 nan nan nan nan ... nan nan nan
Attributes:
    metadata:  Generated by Chain(steps=[('mean',\n              BlockReduce(...
```

{% include aligner.html images="posts-img/spline.png" %}
<figcaption>Interpolación de datos de temperatura para Texas por medio de la función verde.Spline.</figcaption>

<br>
<br>

### Boule. Elipsoides de referencia para aplicaciones geodésicas y geofísicas [^3]
[Boule](https://www.fatiando.org/boule/latest/){:target="_blank" rel="noopener noreferrer"} es un paquete que nos permite representar elipsoides de referencia mediante objetos. Además nos ofrece herramientas para calcular los campos gravitatorios que estos elipsoides generan y realizar conversiones de coordenadas.

Un elipsoide de referencia puede definirse mediante los semiejes mayor $$a$$ y menor $$b$$, su masa total $$M$$ y su velocidad angular $$w$$. De forma alternativa pero equivalente, es posible definirlo mediante los siguientes parámetros:

- El semieje mayor $$a$$,
- el achatamiento $$f=\frac{(a-b)}{a}$$,
- la constante gravitacionel geocéntrica $$GM$$ (donde $$M$$ es la masa del elipsoide y $$G$$ la constante de gravitación universal),
- y la velocidad angular $$w$$.

*Boule* ya ofrece algunos de los elipsoides de referencia más ampliamente usados en Geodesia y Geofísica, tales como el WGS84 (`boule.WGS84`), el GRS80: *Geodetic Reference System* (`boule.GRS80`) e incluso un elipsoide de referencia para el planeta Marte definido según los parámetros disponibles en [Ardalan et al. (2009)](https://doi.org/10.1007/s11038-009-9342-7){:target="_blank" rel="noopener noreferrer"} (`boule.MARS`). Además podemos hallar elipsoides esféricos para la Luna (`boule.MOON`), Venus (`boule.VENUS`) y Mercurio (`boule.MERCURY`) definidos según [Wieczorek (2015)](https://doi.org/10.1029/2019gc008515){:target="_blank" rel="noopener noreferrer"}.

El siguiente fragmento de código ejemplifica cómo se puede utilizar *Boule* para instanciar el elipsoide WGS84, generar una grilla regular de puntos en coordenadas geodésicas elevadas por sobre la superficie del mismo y realizar tareas como el cálculo de gravedad normal o de conversión de unidades.

```python
import boule
import verde as vd

# Obtenemos el elipsoide WGS84
elipsoide = boule.WGS84

# Generamos una grilla de puntos de observación en coordenadas geodésicas
# ubicados a una altitud geométrica de 150 metros
region = (-170, 180, -90, 90)
longitud, latitud, altitud = vd.grid_coordenates(
    region=region, spacing=10, extra_coords=150
)

# Calculamos la gravedad sobre estos puntos
gravedad_normal = elipsoide.normal_gravity(latitud, altitud)

# Convertimos estos puntos a coordenadas esféricas geocéntricas
longitud, latitud_sph, radio = elipsoide.geodetic_to_spherical(
    longitud, latitud, altitud
)
```
<figcaption>Ejemplo de cálculo de gravedad normal y conversión de unidades con elipsoide de referencia WGS84 mediante Boule.</figcaption>

<br>
<br>

### Harmonica. Procesado, modelado directo e inverso de datos gravimétricos y magnéticos [^4]
[Harmonica](https://www.fatiando.org/harmonica/latest/){:target="_blank" rel="noopener noreferrer"} fue creada con la intención de ser el nuevo hogar de aquellas implementaciones de métodos de procesamiento y modelado de datos gravimétricos y magnéticos. Además, surgió como oportunidad de rediseñar algunas de estas implementaciones con el objetivo de facilitar su utilización, extensibilidad y mantenimiento a futuro.

<br>

{% include aligner.html images="posts-img/harmonica-logo.png" %}
<figcaption>Harmonica logo.</figcaption>

<br>

Una de las principales herramientas que ofrece *Harmonica* son las funciones de modelado directo para distintas geometrías y para diferentes sistemas de coordenadas. Podemos calcular los campos gravitatorios producidos por masas puntuales mediante la función `point_gravity()`. *Harmonica* también cuenta con una implementación del método de [Nagy et al. (2000)](https://doi.org/10.1007/s001900000116){:target="_blank" rel="noopener noreferrer"} para calcular los campos gravitatorios de prismas rectangulares mediante la función `prism_gravity()`. El siguiente fragmento de código ejemplifica cómo podemos utilizar esta función para calcular la aceleración de la gravedad producida por dos masas puntuales dadas en coordenadas Cartesianas.

```python
import verde as vd
import harmonica as hm

# Definimos las coordenadas de dos masas puntuales debajo
# de la superficie (en metros)
easting = [500, 1500]
northing = [700, 1300]
upward = [-50, -100]
points = (easting, northing, upward)

# Definimos las masas de cada una de ellas (en unidades SI)
masses = [3e11, -10e11]

# Definimos una grilla regular de puntos de observación (50 metros sobre
# la superficie)
coordinates = vd.grid_coordinates(
    region=(0, 2000, 0, 2000), shape=(100, 100), extra_coords=50
)

# Calculamos la componente vertical (hacia abajo) de la aceleración
# gravitatoria
gravity = hm.point_gravity(
    coordinates, points, masses, field="g_z", coordinate_system="cartesian"
)
```
<figcaption>Ejemplo de cálculo de aceleración de la gravedad producida por dos masas puntuales dadas en coordenadas Cartesianas mediante Harmonica.</figcaption>

<br>

*Harmonica* ofrece un *accessor* de la librería [Xarray](https://docs.xarray.dev/en/stable/){:target="_blank" rel="noopener noreferrer"} para poder calcular los campos gravitatorios que toda la capa genera sobre un conjunto de puntos de observación, la cual hace uso de la función `prism_gravity()`. El siguiente fragmento de código ejemplifica cómo podemos usar la función `prism_layer()` junto con el método `prism_gravity()` del *accessor* para calcular el efecto gravitatorio de la topografía de Sudáfrica sobre una grilla regular de 4000 m de altitud.

```python
import cartopy.crs as ccrs
import matplotlib.pyplot as plt
import pyproj
import verde as vd

import harmonica as hm

# Leemos los datos de topografía para Sudáfrica
south_africa_topo = hm.datasets.fetch_south_africa_topography()

# Proyectamos la grilla
projection = pyproj.Proj(proj="merc", lat_ts=south_africa_topo.latitude.values.mean())
south_africa_topo = vd.project_grid(south_africa_topo.topography, projection=projection)

# Creamos un arreglo 2D con las densidades de los prismas
# Cada valor por encima del geoide tendrá una densidad de 2670 kg/m^3
# Cada valor por debajo del geoide tendrá un contraste de densidad
# igual a la diferencia entre la densidad del océano y la densidad
# de la corteza terrestre superior: 1000 kg/m^3 - 2900 kg/m^3
density = south_africa_topo.copy()  # Copiamos la topografía a un nuevo arreglo
density.values[:] = 2670.0  # Reemplazamos todos los valores para la densidad de la topografía

# Cambiamos los valores de densidad de los puntos en el océano
density = density.where(south_africa_topo >= 0, 1000 - 2900)

# Creamos una capa de prismas
prisms = hm.prism_layer(
    (south_africa_topo.easting, south_africa_topo.northing),
    surface=south_africa_topo,
    reference=0,
    properties={"density": density},
)

# Procesamos el campo gravitatorio en una grilla regular localizada 4000 m por encima del elipsoide
coordinates = vd.grid_coordinates(
    region=(12, 33, -35, -18), spacing=0.2, extra_coords=4000
)
easting, northing = projection(*coordinates[:2])
coordinates_projected = (easting, northing, coordinates[-1])
prisms_gravity = prisms.prism_layer.gravity(coordinates_projected, field="g_z")

# Creamos una gráfica de la gravedad procesada
plt.figure(figsize=(8, 8))
ax = plt.axes(projection=ccrs.Mercator())
maxabs = vd.maxabs(prisms_gravity)
tmp = ax.pcolormesh(
    *coordinates[:2],
    prisms_gravity,
    vmin=-maxabs,
    vmax=maxabs,
    cmap="RdBu_r",
    transform=ccrs.PlateCarree()
)
ax.set_extent(vd.get_region(coordinates), crs=ccrs.PlateCarree())
plt.title("Gravitational acceleration of the topography")
plt.colorbar(
    tmp, label="mGal", orientation="horizontal", shrink=0.93, pad=0.01, aspect=50
)
plt.show()
```
{% include aligner.html images="posts-img/prisms_topo_gravity.png" %}
<figcaption>Gráfica de la aceleración gravitacional por topografía.</figcaption>

<br>
<br>

### Pooch. Descarga y almacenamiento de datos científicos de la web de forma sencilla [^5]
Muchas de las librerías de software científico hacen uso de datos de muestra para ejemplificar su funcionamiento en las secciones de la documentación que se conocen como *Galería de ejemplos*. Usualmente estos datos de muestra se incluyen dentro de los repositorios donde se aloja el mismo código fuente de la librería, sin embargo, estos archivos de datos no son empaquetados para su distribución, esto con el objetivo de reducir el tamaño de futuras instalaciones. En cambio, los datos de muestra suelen ser descargados al ser necesarios mediante código implementado dentro de cada una de estas librerías, haciendo uso de paquetes de Python para descargar archivos mediante el protocolo *HTTP* por ejemplo.

<br>

{% include aligner.html images="posts-img/pooch-logo.png" %}
<figcaption>Pooch logo.</figcaption>

<br>

[Pooch](https://www.fatiando.org/pooch/latest/){:target="_blank" rel="noopener noreferrer"} permite gestionar un registro en el cual podemos listar las direcciones de cada uno de los archivos que queremos ofrecer para su descarga, junto con el *hash* de una suma de verificación.  En el siguiente fragmento de código se ejemplifica cómo es posible utilizar la función `pooch.create()` para inicializar una instancia de la clase `pooch.Pooch`, especificando el directorio donde se descargarán los archivos, la dirección base donde se encuentran alojados los archivos de interés, y el registro donde enumeramos el nombre de los archivos y sus *hashes* de las sumas de verificación. Luego podemos solicitar la descarga de uno de los archivos mediante el método `fetch()`, el cual devuelve la ruta al archivo descargado y almacenado localmente.

```python
import pooch

# Inicializamos una instacia de la clase pooch.Pooch
odie = pooch.create(
    # Utilizamos el directorio cache por defecto de nuestro sistema operativo
    path=pooch.os_cache("my-project"),
    # Definimos la dirección base donde se encuentran los archivos a descargar
    base_url="https://www.somewebpage.org/science/data/",
    # Especificamos los archivos a descargar en el registro
    registry={
        "temperature.csv": "sha256:19uheidhlkjdwhoiwuhc0uhcwljchw9ochwochw89dcgw9dcgwc",
        "gravity-disturbance.nc": "sha256:1upodh2ioduhw9celdjhlfvhksgdwikdgcowjhcwoduchowjg8w"
    }
)

# Solicitamos la descarga de uno de los archivos
file_path = odie.fetch("gravity-disturbance.nc")
```
<figcaption>Ejemplo de descarga de archivos con Pooch mediante la clase pooch.Pooch. Este código es a modo de ejemplificación y no está escrito para ser ejecutado.</figcaption>

<br>
<br>

## Usos y aplicaciones
Si bien los ejemplos de los paquetes presentados en este post son principalmente orientados a gravimetría, podemos procesar muchos tipos de datos por medio de **Fatiando a Terra**, paquetes como **Verde** o **Harmonica** nos permiten hacer grillados o interpolaciones de cualquier tipo de información espacial, ya sea gravimétrica, magnetométrica, de temperatura, entre otras. También podemos destacar el uso del paquete **Pooch** para descargar una cantidad increíble de datos que nos pueden servir de práctica o ejemplo para aplicarlos en nuestro código, además de que está diseñado para almacenar exactamente los mismos datos que usaste la primera vez en tu código de manera que no tengas problemas al volver a correrlo en un futuro. **Boule** también representa una herramienta increíble ya que además de contar con gran cantidad de elipsoides de referencia para la Tierra y la Luna cuenta con algunos modelos para planetas como Marte, Venus y Mercurio.

A continuación podemos ver un ejemplo del uso de estos paquetes para un grillado de datos gravimétricos en todo Australia.

<br>

### Grillado de datos gravimétricos de Australia [^6]
Por medio de este estudio se demuestra cómo se pueden utilizar fuentes equivalentes potenciadas por gradiente (*Gradient-boosting*) para interpolar grandes cantidades de datos sobre una grilla regular a una altitud uniforme. Los datos procesados se conforman de alrededor de 1.7 millones de puntos que cubren gran parte del territorio australiano. El objetivo principal del estudio es crear una grilla regular de disturbios de gravedad a una altitud geométrica constante de 2127.58 m (la altitud de observación más alta presente en los datos).

Se realiza una definición de _fuentes promediadas por bloque_ separando bloques de 1.8 km de lado, obteniendo un total de 766,744 fuentes puntuales (1 minuto de arco equivale aproximadamente a 1.8 km en el ecuador). Para el procesamiento de los datos se eligió un tamaño de ventana de 225 km con el objetivo de limitar la cantidad de memoria por debajo de los 16 Gb de RAM.

También se determinaron la profundidad relativa de las fuentes y el parámetro de _amortiguamiento_ aplicando una validación cruzada de $$K$$ iteraciones (_K-Fold cross-validation_), mediante la librería de _machine learning_ [scikit-learn](https://scikit-learn.org/stable/){:target="_blank" rel="noopener noreferrer"} la cual nos permite dividir aleatoriamente los datos originales en $$k$$ conjuntos y valida el modelo de fuentes equivalentes utilizando solo los datos de $$k - 1$$ conjuntos, de esta forma valida el modelo comparando sus predicciones sobre los puntos pertenecientes al conjunto restante.

![Australia-gridding]({{ "assets/img/posts-img/australia_grid.png" | relative_url }})
<figcaption>Mapas de los valores observados (a y c) y valores interpolados (b y d) de disturbio de gravedad sobre Australia. Los valores observados en a y c se muestran como círculos coloreados. El rectángulo rojo con línea punteada señala la zona representada en los mapas c y d.</figcaption>

<br>

Una característica importante en la efectividad de este procesamiento es que fue posible estimar los coeficientes de las fuentes utilizando el conjunto completo de datos (1.7 millones de puntos) para predecir valores del disturbio de la gravedad sobre una grilla regular de 2442x2085 puntos a una altitud de 2127.58 m por encima del elipsoide. En una computadora con 16 núcleos y 16 Gb de RAM, la estimación de los coeficientes de las 796,744 fuentes mediante el algoritmo de potenciación del gradiente tomó aproximadamente 1.3 horas, y la predicción sobre los puntos de la grilla, 18 minutos.

Esto representa un enorme avance en la capacidad de cómputo, estamos hablando que sería posible procesar datos de ciudades enteras desde un ordenador personal o laptop con especificaciones modestas. No hay duda de que estos métodos y paquetes de descarga, procesamiento, modelado e interpolado de datos representan una gran ventaja para acercar la ciencia a la mayor cantidad posible de personas interesadas en estas técnicas, lo cual reduce cada vez más la barrera del conocimiento.

<br>

#### Comentarios, sugerencias y opiniones
_Espero que este post haya sido de interés para ti, si es así compártelo en tus redes. ¡Te lo agradecería mucho!_

_Si tienes algún comentario, sugerencia u opinión házmelo saber en los comentarios de abajo, no requieres de ninguna cuenta, sólo elige un nombre de usuario (puede ser tu nombre) y un correo (opcional). Todos los comentarios son enviados a un moderador, por lo tanto tardarán un poco en publicarse._

<br>

[^1]: {% include citation.html key="fatiando" %}
[^2]: {% include citation.html key="verde" %}
[^3]: {% include citation.html key="boule" %}
[^4]: {% include citation.html key="harmonica" %}
[^5]: {% include citation.html key="pooch" %}
[^6]: {% include citation.html key="australia" %}