---
layout: post
title: MagnetoPy
img: "assets/img/portfolio/magnetic-field.png"
date: 08-04-2022
tags: [Portafolio]
excerpt_separator: <!--more-->
permalink: /portafolio/MagnetoPy
---
{% include aligner.html images="portfolio/magnetic-field.png" %}

<br>

_MagnetoPy_ es una CLI (_Command Line Interface_) _open source_ escrita en Python, diseñada para procesar datos magnéticos. Con un conjunto robusto de comandos, _MagnetoPy_ tiene como objetivo simplificar el análisis y la manipulación de datos magnéticos para los geofísicos en el campo.<!--more--> Este es mi proyecto de tesis de la licenciatura en Ciencias de la Tierra, el cual sigue en desarrollo y en constante actualización.

En este post escribí un poco de la teoría y los fundamentos bajo los cuales está escrito este software. Si quieres ir directo a la sección de cómo utilizar _MagnetoPy_ puedes seleccionar el enlace **Utilizando _MagnetoPy_** en el índice de contenidos.

> **Última actualización:** 25 de junio de 2024.

* TOC
{:toc}

<br>

## Resumen

El Campo Magnético Terrestre (CMT) se conforma de diferentes magnitudes vectoriales representadas desde un punto en la superficie terrestre; las componentes horizontal $$(H)$$ y vertical $$(Z)$$, donde $$(H)$$ se caracteriza por contar con un norte $$(X)$$ y este $$(Y)$$ geográficos. La relación angular entre $$(H)$$ y $$(X)$$ se define como la declinación $$(D)$$, mientras que la relación angular entre $$(H)$$ y el campo total $$(N)$$, corresponde a la inclinación $$(I)$$ [^1]. En un levantamiento magnetométrico, un dato magnético medido en una estación $$(P)$$ a un tiempo $$(t)$$ es una superposición de efectos, incluyendo el campo principal interno, la inducción de fuentes externas y la inducción debida a cuerpos anómalos magnetizados. El campo geomagnético no es constante en el tiempo, sino que tiene una variación lenta, estas variaciones se conocen como variaciones seculares, las cuales se producen por el movimiento convectivo del núcleo externo. Asimismo, existen variaciones externas que son producidas en rangos menores de tiempo (desde algunas horas hasta meses), principalmente generadas por cambios en las corrientes eléctricas en la atmósfera superior. Debido a que el campo principal interno representa un 95% del dato magnético, es necesario aplicar correcciones que puedan aislar la componente de interés [^2].

{% include aligner.html 
  images="portfolio/north_south_magnetic_field.png,portfolio/earth_magnetic_field_components.png" 
  column=2
%}
<figcaption>Componentes del campo magnético terrestre. Recuperado de Hinze et al., 2013.</figcaption>

<br>

Este trabajo busca generar un _software open source_ que incluya diferentes reducciones y filtros necesarios para realizar un correcto procesamiento e interpretación de datos obtenidos de levantamientos magnetométricos.

<br>

## Introducción

Las mediciones de anomalías magnéticas de campo total son ampliamente utilizadas en la exploración geofísica debido a su bajo costo y a su facilidad de adquisición. Durante un levantamiento magnetométrico, la adquisición de datos se ve afectada por variaciones temporales causadas por corrientes eléctricas ionosféricas, un efecto que se encuentra presente todo el tiempo y el cual puede ser compensado mediante mediciones de una estación base, a su vez, las variaciones seculares representan una fuente importante de ruido para los datos recopilados, es por ello que la _International Association of Geomagnetism and Aeronomy_ (IAGA) desarrolló el _International Geomagnetic Reference Field_ (IGRF), una serie de armónicos esféricos para representar el campo global en cuatro dimensiones: latitud, longitud, distancia geocéntrica (altitud), y tiempo [^2].

Debido a que la medición del campo magnético consiste en una superposición de múltiples fuentes, el proceso para eliminar o atenuar estos efectos se vuelve de gran importancia para la interpretación de las anomalías. Existen técnicas que permiten aislar la componente de interés mediante filtros o transformaciones, un ejemplo de las mismas es la reducción al polo, la cual permite trasladar el punto de observación al polo geomagnético para visualizar la anomalía como si se estuviera justo encima. Esta técnica permite eliminar las variaciones horizontales producidas por el campo geomagnético y proporciona un mejor punto de interpretación para la fuente observada [^2]. 

<br>

<div style="text-align:center">
  {% include aligner.html images="portfolio/magnetic_anomalies.png" column=1 %}
  <figcaption>Superposición de anomalías magnéticas. Recuperado de Hinze et al., 2013.</figcaption>
</div>

<br>

Actualmente se cuenta con una amplia variedad de software que realiza estas correcciones de manera automática, sin embargo, pocos de estos programas permiten el acceso al código fuente, el cual facilita entender las transformaciones que realiza a los datos, y a su vez, proporciona flexibilidad al usuario para manipular los parámetros de las mismas.

<br>

## ¿Qué es el IGRF?
El IGRF (_International Geomagnetic Reference Field_) por sus siglas en inglés es un conjunto de coeficientes esféricos armónicos que pueden ser introducidos en un modelo matemático para describir la porción a gran escala y variable en el tiempo del campo magnético interno de la Tierra entre épocas desde 1900 d.C. hasta la actualidad. El IGRF es calculado y producido por un grupo de trabajo internacional de científicos denominado IAGA (_International Association of Geomagnetism and Aeronomy_). La actual decimotercera generación del IGRF ha sido derivada de observaciones recopiladas por satélites, observatorios en tierra y estudios magnéticos en todo el mundo.[^3]

Las series de modelos matemáticos utilizadas para calcular el Campo Magnético Terrestre pueden representarse en la siguiente expresión:

$$
  V(r,\theta ,\phi ,t)=a\sum_{N}^{n=1}\sum_{n}^{m=0}(\frac{a}{r})^{n+1}[g_{n}^{m}cos(m\phi )+h_{n}^{m}(t)sin(m\phi )]P_{n}^{m}(cos\theta )
$$

<br>

{% include aligner.html
  images="portfolio/total-field.png,portfolio/mag-poles.png"
  column=2
%}

<figcaption>Izquierda: Mapa de la intensidad total del CMT para 2020 | Derecha: Cambio de los polos magnéticos norte y sur desde 1900 d.C. <br>Fuente: International Geomagnetic Reference Field: the thirteenth generation.</figcaption>

<br>

## Utilizando _MagnetoPy_
_MagnetoPy_ funciona como CLI y por lo tanto se puede ejecutar desde la terminal, sin embargo, yo recomiendo utilizar el IDE (_Integrated Development Environment_) [PyCharm](https://www.jetbrains.com/pycharm/download/) debido a que permite administrar los ambientes virtuales de nuestra máquina en el caso de tener múltiples proyectos de _Python_ para evitar conflictos de versiones, además de que facilita la configuración de los diferentes parámetros de _MagnetoPy_, los cuales pueden ser muy extensos para algunos comandos.

<br>

### Preparación del ambiente de trabajo
Para utilizar _MagnetoPy_ es necesario tener instalado lo siguiente:

- [Python 3.11.0](https://www.python.org/downloads/) o superior.
- [Git](https://git-scm.com/downloads) para clonar el repositorio.
- [PyCharm](https://www.jetbrains.com/pycharm/download/) (recomendado).

<br>

### Instalación
Para instalar _MagnetoPy_ es necesario clonar el repositorio desde la terminal con el siguiente comando:

```bash
git clone https://github.com/JCBucio/MagnetoPy.git
```

Posteriormente, abriremos el proyecto en PyCharm de la siguiente manera:
1. Abrimos PyCharm.
2. Seleccionamos la opción _Open_.
3. Buscamos la carpeta _MagnetoPy_ y la seleccionamos.
4. Copiamos la carpeta `runConfigurations` en la carpeta `.idea` del proyecto.

> **Nota**: Si la carpeta `.idea` no aparece en los archivos del proyecto, puedes intentar cerrar PyCharm y volver a abrirlo. Si aún no aparece, puedes copiar la carpeta `runConfigurations` en la carpeta `.idea` de manera manual en el explorador de archivos.

Antes de ejecutar cualquier comando de _MagnetoPy_ es necesario crear un ambiente virtual para el proyecto, para realizar esto en PyCharm sigue los siguientes pasos:

1. Abre el proyecto en PyCharm.
2. Dirígete a `File > Settings`.
3. En la ventana de configuración selecciona `Project: MagnetoPy` > `Python Interpreter`.
4. Haz clic en el engrane y selecciona `Add`.
5. Selecciona `Virtualenv Environment`.
6. En la opción de `Location` selecciona la carpeta en donde quieres crear el ambiente virtual del proyecto (yo recomiendo crearlo en la carpeta del proyecto).
7. Haz clic en `OK`.

> **Nota**: PyCharm nos solicitará crear el ambiente virtual en una carpeta vacía, puedes crear una con el nombre que tú desees (yo recomiendo nombrarla `env`) en la carpeta del proyecto.

Para instalar las dependencias del proyecto en el ambiente virtual sigue los siguientes pasos:

1. Abre el proyecto en PyCharm.
2. Abre el archivo `requirements.txt` del proyecto.
3. Haz clic en `Install requirements`.

<br>

### Ejecutando _MagnetoPy_

Para consultar una descripción de _MagnetyoPy_ y de cada uno de los comandos disponibles, ejecuta el siguiente comando en la terminal:

```
python magnetopy.py --help
```

O bien:
  
```
python magnetopy.py <command> --help
```

Por ejemplo, para consultar la descripción del comando `diurnal-variation` ejecuta el siguiente comando:

```
python magnetopy.py diurnal-variation --help
```

<br>

### Comandos disponibles

_MagnetoPy_ sigue en desarrollo y por lo tanto se irán agregando más comandos y funciones a la CLI, a continuación se muestra una lista de los comandos disponibles hasta la fecha:

- `diurnal-variation`: Corrección por variación diurna utilizando datos de una estación base.
- `calculate-igrf`: Corrección por IGRF calculando el campo magnético total.

<br>

### Mejoras futuras
_MagnetoPy_ sigue en desarrollo y es posible que tenga algunos pequeños errores si no se introducen los datos de manera correcta, sigo trabajando para hacer esta _CLI_ mucho más sencilla y rápida de utilizar.

<br>

#### Comentarios, sugerencias y opiniones
_Si tienes algún comentario, sugerencia u opinión házmelo saber en los comentarios de abajo, no requieres de ninguna cuenta, sólo elige un nombre de usuario (puede ser tu nombre) y un correo (opcional). Todos los comentarios son enviados a un moderador, por lo tanto tardarán un poco en publicarse._

<br>

[^1]: {% include citation.html key="blakely" %}
[^2]: {% include citation.html key="hinze" %}
[^3]: {% include citation.html key="igrf-13" %}
