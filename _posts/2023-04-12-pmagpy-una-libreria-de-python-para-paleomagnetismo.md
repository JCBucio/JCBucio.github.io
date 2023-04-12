---
layout: post
title: PmagPy. Una librería de Python para Paleomagnetismo
tags: [Python, Geofísica, PmagPy, Paleomagnetismo, Magnetismo]
excerpt_separator: <!--more-->
permalink: /blog/:year/:title
thumbnail: "assets/img/thumbnails/nasa-unsplash.jpg"
feature-img: "assets/img/thumbnails/nasa-unsplash.jpg"
---
[PmagPy](https://github.com/PmagPy/PmagPy){:target="_blank" rel="noopener noreferrer"} es una librería *open source* de *Python* con una serie de herramientas para el procesamiento, análisis e interpretación de datos paleomagnéticos. Esta librería cuenta con un conjunto de funciones escritas en *Python* para ser utilizadas en scripts ó *Jupyter Notebooks*.

<!--more-->

💡 Parte del contenido de este post fué creado con ayuda de ChatGPT[^2] y Github Copilot[^3], dos herramientas de IA que generan texto y código mediante el uso de modelos de lenguaje natural. Todo el contenido generado por medio de dichas herramientas fué revisado cuidadosamente.

* TOC
{:toc}

<br>

## Paleomagnetismo. Midiendo el campo magnético de las rocas
El **Paleomagnetismo** es el estudio de las propiedades magnéticas de las rocas a lo largo del tiempo. Es una de las disciplinas de la Geofísica más aplicable en múltiples áreas como el geomagnetismo, tectónica, paleocenografía, vulcanología, paleontología, y sedimentología, entre otras.

Para poder comprender cómo las rocas adquieren propiedades magnéticas es necesario entender el funcionamiento del Campo Magnético Terrestre (CMT). El CMT es, como su nombre lo indica, el campo magnético que rodea la Tierra, generado desde la formación de la Tierra misma. Este campo magnético es generado por corrientes eléctricas en el núcleo externo de la Tierra, que está compuesto principalmente de hierro líquido y níquel.

El proceso de formación del campo magnético terrestre está relacionado con la convección del material fundido en el núcleo externo de la Tierra. Esta convección crea corrientes eléctricas que generan el campo magnético.

Además, la rotación de la Tierra también contribuye al campo magnético terrestre, ya que las corrientes eléctricas generadas por la convección del núcleo interactúan con la rotación de la Tierra para producir un efecto dínamo.

<!-- Include a gif -->

<br>

{% include aligner.html images="posts-img/reversalanimation.gif" %}
<figcaption>Modelo numérico tridimensional de una inversión del campo geomagnético (Glatzmaier & Roberts, 1995). Recuperado de <a href="https://www.nature.com/articles/377203a0" target="_blank" rel="noopener noreferrer">https://www.nature.com/articles/377203a0</a></figcaption>

<br>

## PmagPy. Un paquete completo para análisis paleomagnéticos
*PmagPy*[^5] es un conjunto de herramientas escritas en *Python* para el análisis de datos paleomagnéticos. Esta librería facilita la interpretación de estudios magnéticos como la desmagnetización de rocas u obtención de paleointensidades. El paquete está hosteado en [Github](https://github.com/PmagPy/PmagPy){:target="_blank" rel="noopener noreferrer"} y puede ser instalado por medio de [PyPI](https://pypi.org/project/pmagpy/){:target="_blank" rel="noopener noreferrer"}. A su vez, *PmagPy* está diseñada para trabajar con el formato de la base de datos [MagIC](https://earthref.org/MagIC){:target="_blank" rel="noopener noreferrer"}, descrita más adelante en este post.

Algunos de los principales usos y utilidades de *PmagPy* incluyen:

- **Procesamiento de datos**: *PmagPy* incluye herramientas para el procesamiento y filtrado de datos paleomagnéticos, como la desmagnetización térmica o de campo alternante. Estas herramientas ayudan a eliminar cualquier ruido o señales no deseadas en los datos.

- **Análisis direccional**: *PmagPy* incluye una serie de herramientas para el análisis direccional, como el cálculo de direcciones medias, polos geomagnéticos virtuales y estadísticas de variación paleosecular. Estas herramientas ayudan a caracterizar la dirección e intensidad del campo magnético de la Tierra en el momento en que se formaron las rocas.

- **Análisis de magnitud**: *PmagPy* incluye herramientas para estimar la paleointensidad del campo magnético de la Tierra utilizando una variedad de métodos como el método de *Thellier-Coe* y sus variaciones, el método *Shaw*, así como el protocolo *IZZI*.

- **Pruebas estadísticas**: *PmagPy* incluye una serie de pruebas estadísticas para datos paleomagnéticos, como la prueba de pliegues, la prueba de inversión y la prueba de conglomerados. Estas pruebas se utilizan para evaluar la fiabilidad y significancia de los datos paleomagnéticos.

- **Visualización de datos**: *PmagPy* incluye herramientas para visualizar datos paleomagnéticos, como estereogramas, gráficas para temperaturas de *Curie*, gráficas de *Day*, entre otras. Estas herramientas ayudan a identificar patrones y tendencias en los datos y a comunicar los resultados a otros.

<br>

{% include aligner.html images="posts-img/pmagpy_logo.png" %}
<figcaption>Logo de PmagPy.</figcaption>

<br>

*PmagPy* tiene los siguientes formatos disponibles:

- **Módulos con funciones para tratamiento de datos**: En esta sección se encuentra un conjunto de herramientas para cálculos (`pmagpy.pmag`), graficación (`pmagpy.pmagplotlib`), así como análisis de datos con mayor nivel de complejidad (`pmagpy.ipmag`) que pueden ser realizados por medio de Python en un *Jupyter Notebook* o *Jupyter Lab*.

- **Una interfaz gráfica de usuario (GUI)**: Una *GUI* ó *Graphical User Interface* por sus siglas en inglés, es cualquier aplicación de escritorio que permite su uso de una manera más sencilla por medio de un diseño más intuitivo para el usuario. La *GUI* de *PmagPy* permite a los usuarios obtener datos en formato *MagIC* o bien, convertirlos a este mismo formato.

- **Programas para línea de comandos (CLIs)**: Las *CLIs* ó *Command Line Interfaces* por sus siglas en inglés, son programas diseñados para realizar tareas o cálculos muy específicos que no requieren de una interfaz de usuario y pueden ser ejecutados mediante una línea de comandos. Estos programas se pueden encontrar en el [repositorio de PmagPy](https://github.com/PmagPy/PmagPy){:target="_blank" rel="noopener noreferrer"}.

**NOTA:** Este post se centra en el uso de *PmagPy* como **librería de Python**. Para conocer más sobre la *GUI* de *PmagPy* y los programas de línea de comandos, se recomienda visitar la [documentación oficial](https://pmagpy.github.io/PmagPy-docs/intro.html){:target="_blank" rel="noopener noreferrer"}.

<br>

### Ejemplo de uso: Procesamiento de datos de rocas provenientes de flujos de lava del volcán Xitle, México

En este ejemplo se muestra el uso de *PmagPy* junto con otras librerías de *Python* para realizar el procesamiento de datos de rocas provenientes de flujos de lava del volcán Xitle, México, que recibieron tratamientos magnéticos mediante campos alternos progresivos.[^4]

Las librerías de *Python* utilizadas en este ejemplo son:

- **[PmagPy](https://pmagpy.github.io/PmagPy-docs/intro.html){:target="_blank" rel="noopener noreferrer"}**: Análisis y procesamiento de datos paleomagnéticos.
- **[Pandas](https://pandas.pydata.org/){:target="_blank" rel="noopener noreferrer"}**: Análisis y manipulación de datos mediante `DataFrames`.
- **[Numpy](https://numpy.org/){:target="_blank" rel="noopener noreferrer"}**: Herramientas para cómputo científico.
- **[Matplotlib](https://matplotlib.org/){:target="_blank" rel="noopener noreferrer"}**: Visualización de datos mediante gráficas y figuras.
- **[os](https://docs.python.org/es/3.10/library/os.html){:target="_blank" rel="noopener noreferrer"}**: Herramientas para el manejo de archivos y directorios.
- **[time](https://docs.python.org/3/library/time.html){:target="_blank" rel="noopener noreferrer"}**: Herramientas para manipular fechas, horas o añadir cronometraje.

**NOTA:** Las siguientes celdas de código llevan una descripción con el orden en el que deben ser ejecutadas (*Parte 1/5*...). Esto es de utilidad para aquellos que deseen reproducir el ejemplo en una *Jupyter Notebook* ó un script de *Python*.

```python
import pmagpy.pmag as pmag
import pmagpy.ipmag as ipmag
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import os
import time
```
<figcaption>Parte 1/4. Importación de librerías en Python.</figcaption>

<br>

#### Tratamiento de datos en formato `.jr6`

El formato `.jr6` es generado por el instrumento [AGICO JR-6](https://www.agico.com/text/products/jr6/jr6.php){:target="_blank" rel="noopener noreferrer"} el cual se utiliza para medir la magnetización remanente de rocas basado en principios clásicos (no cuánticos y no criogénicos). Su sensibilidad permite medir rocas con una magnetización remanente muy débil, por ejemplo, varias rocas sedimentarias.

El formato en el que el instrumento JR-6 guarda los datos es `.jr6`, este formato es un archivo de texto plano en el que cada línea representa una medición del campo magnético de la roca junto con varias columnas que contienen información de cada medición. A continuación se muestra un ejemplo de las columnas que contiene un archivo `.jr6` utilizado en el estudio del volcán Xitle:

| Columna | Descripción |
| --- | --- |
| *sample* | Nombre de la muestra |
| *step* | Valor máximo del campo aplicado en cada paso de desmagnetización en $$mT$$ |
| *mx*, *my* y *mz* | Componentes de la magnetización medida en cada paso en coordenadas de la muestra |
| *exp* | Exponente base 10 al que hay que convertir los valores de $$M$$ |
| *dec* | Declinación magnética |
| *inc* | Inclinación magnética |

Para realizar el procesamiento de datos de este ejemplo se hizo la conversión de  `.jr6` a `.csv` mediante una pequeña rutina elaborada en *Python*. A continuación se muestra el código utilizado para realizar la conversión:

```python
jr6_format = 'xitle_data/jr6_format/' # Directorio con los archivos jr6
txt_format = 'xitle_data/txt_format/' # Directorio donde se guardarán los archivos txt
csv_format = 'xitle_data/csv_format/' # Directorio donde se guardarán los archivos csv

jr6_files = [f for f in os.listdir(jr6_format) if f.endswith('.jr6')]

for file in jr6_files: # Iterar sobre los archivos jr6
    file_name = file.split('.')[0]
    with open(jr6_format + file, 'r') as f:
        lines = f.readlines()
        data = [line.split() for line in lines]

    with open(txt_format + file_name + '.txt', 'w') as f: # Guardar los datos en formato txt
        f.write('sample\tstep\tmx\tmy\tmz\texp\tdec\tinc\n')
        for line in data:
            f.write('\t'.join(line))
            f.write('\n')

    df = pd.DataFrame(columns=['sample', 'step', 'mx', 'my', 'mz', 'exp', 'dec', 'inc']) # Generar un DataFrame con los datos
    for line in data:
        df = df.append({'sample': line[0], 'step': line[1], 'mx': line[2], 'my': line[3], 'mz': line[4], 'exp': line[5], 'dec': line[6], 'inc': line[7]}, ignore_index=True)

    df.to_csv(csv_format + file_name + '.csv', index=False) # Guardar los datos en formato csv
```
<figcaption>Parte 2/4. Código para la conversión de archivos jr6 a csv.</figcaption>

<br>

*PmagPy* también cuenta con funciones que nos permiten realizar conversiones de formatos que generan diferentes instrumentos de medición. Algunas conversiones que *PmagPy* puede realizar mediante el módulo `pmagpy.convert_2_magic` son:

- `._2g_asc_magic()`: Conversión de archivos 2G ascii a formato MagIC.
- `._2g_bin_magic()`: Conversión de archivos 2G binarios a formato MagIC.
- `.jr6_jr6_magic()`: Conversión de archivos del spinner AGICO JR6 a formato MagIC.
- `.jr6_txt_magic()`: Conversión de archivos de texto AGICO JR6 a formato MagIC.
- `.agm_magic()`: Conversión de archivos de magnetización de fuerza de gradiente alterno (AGM) a formato MagIC.

Para obtener más información sobre las funciones de conversión de *PmagPy* se puede consultar la documentación oficial de la librería en [ este enlace](https://pmagpy.github.io/PmagPy-docs/documentation_notebooks/PmagPy_MagIC.html#conversion-scripts){:target="_blank" rel="noopener noreferrer"}.

<br>

#### Cálculos de magnetización total, declinación e inclinación

Una vez obtenidos los `csv` con el formato correcto se crearon las siguientes 4 funciones para realizar los cálculos correspondientes de las columnas faltantes (*M(A/m)*, *Dec.*, *Inc.*):

```python
def inclination(x, y, z):
    inc = np.arctan(z / (np.sqrt((x**2) + (y**2))))
    return np.degrees(inc)

def declination(x, y):
    dec = np.arctan(y / x)
    return np.degrees(dec)

def mag_total(x, y, z):
    mag = np.sqrt((x**2) + (y**2) + (z**2))
    return mag

def mag_rel(m, max_m):
    return m / max_m
```
<figcaption>Parte 3/4. Funciones para el cálculo de magnetización total, declinación e inclinación.</figcaption>

<br>

Donde:

- `inclination(x, y, z)`: Calcula la inclinación magnética de una muestra a partir de las componentes de la magnetización en coordenadas de la muestra.

$$ I = \arctan \left( \frac{M_z}{\sqrt{(M_x^2 + M_y^2)}} \right) $$

- `declination(x, y)`: Calcula la declinación magnética de una muestra a partir de las componentes de la magnetización en coordenadas de la muestra.

$$ D = \arctan \left( \frac{M_y}{M_x} \right) $$

- `mag_total(x, y, z)`: Calcula la magnetización total de una muestra a partir de las componentes de la magnetización en coordenadas de la muestra.

$$ M = \sqrt{(M_x^2 + M_y^2 + M_z^2)} $$

- `mag_rel(m, max_m)`: Calcula la magnetización relativa de una muestra a partir de la magnetización total y la magnetización máxima.

$$ M_r = \frac{M}{M_{max}} $$

<br>

Finalmente, mediante un *loop* se realiza el cálculo para cada medición de cada muestra:

```python
csv_format_path = 'xitle_data/csv_format/'
files = os.listdir(csv_format_path)

for file in files:
    df = pd.read_csv(dir_path + file)

    df['calc_inc'] = inclination(df['mx'], df['my'], df['mz'])
    df['calc_dec'] = declination(df['mx'], df['my'])
    df['m'] = mag_total(df['mx'], df['my'], df['mz'])
    df['M'] = mag_rel(df['m'], max(df['m']))

    df.to_csv(csv_format_path + file, index=False)
```
<figcaption>Parte 4/4. Loop para el cálculo de las columnas faltantes.</figcaption>

<br>

#### Estereogramas ó *equal area projections*
En Paleomagnetismo, a menudo deseamos comparar direcciones de partes distantes del globo. Hay una dificultad al comparar direcciones magnéticas de lugares lejanos debido a que la inclinación magnética varía mucho con la latitud. Para solucionar esto, se puede utilizar una técnica matemática llamada **proyección de área igual** ó *equal area projection*, por su definición en inglés, que permite representar los datos en un mapa de forma que la dirección esperada del campo magnético en cada sitio de muestreo sea el centro de la proyección. Esto facilita la comparación de las direcciones magnéticas entre diferentes sitios de muestreo.[^1]

En *PmagPy* se pueden generar este tipo de proyecciones, también llamadas estereogramas mediante el uso de las funciones `ipmag.plot_net()` para graficar el estereograma y `ipmag.plot_di()` para graficar las direcciones de los datos. A continuación se muestra un ejemplo de la graficación de un estereograma para una de nuestras muestras:

**NOTA:** A partir de esta sección los bloques de código **NO** deben seguir un orden específico para que el código funcione correctamente.

```python
example = pd.read_csv('xitle_data/dec_inc_calculated/95X001A.csv') # Cargamos los datos de la muestra 95X001A

# Pasamos las columnas con las declinaciones e inclinaciones a listas
ex_dec = example['calc_dec'].to_list()
ex_inc = example['calc_inc'].to_list()

plt.figure(figsize=(10, 10)) # Definimos el tamaño de la figura
ipmag.plot_net(fignum=1) # Graficamos el estereograma
ipmag.plot_di(dec=ex_dec, inc=ex_inc, color='red', markersize=20, label='95X001A') # Graficamos las direcciones de los datos
plt.legend() # Mostramos la leyenda
plt.show()
```
<figcaption>Bloque de código para la graficación de una proyección de área igual (estereograma).</figcaption>

<br>

Output:

{% include aligner.html images="posts-img/95X001A_estereo.png" column=1 %}
<figcaption>Estereograma de la muestra 95X001A.</figcaption>

<br>

#### Diagramas de Zijderveld ó proyecciones ortogonales

El proceso de desmagnetización utilizado por los paleomagnetistas para estudiar la magnetización remanente de las rocas consiste en someter la muestra a una serie de pasos de desmagnetización y medir la magnetización después de cada paso hasta que se aísla el componente más estable, a este punto se le llama magnetización remanente característica o *ChRM*.[^1]

La visualización de los datos de desmagnetización es un problema complicado porque los datos son tridimensionales, por lo que los paleomagnetistas suelen usar un conjunto de dos proyecciones de los vectores, una en el plano horizontal y otra en el plano vertical, llamadas **diagramas de Zijderveld** ó **proyecciones ortogonales**.

En *PmagPy* se pueden generar estas proyecciones ortogonales y otras gráficas para análisis de resultados de desmagnetización con la función `pmagplotlib.plot_zed()`, la cual genera un estereograma, un diagrama de Zijderveld (proyección ortogonal) y un diagrama de desmagnetización. Debido a que esta función genera 3 gráficas por default, no es tan personalizable. Para fines más visuales se generó el siguiente código para generar solamente las proyecciones ortogonales de manera más personalizada:

```python
example = pd.read_csv('xitle_data/dec_inc_calculated/95X001A.csv') # Cargamos los datos de la muestra 95X001A

# Pasamos las columnas de las direcciones a listas
x = example['mx'].to_list()
y = example['my'].to_list()
z = example['mz'].to_list()

plt.figure(figsize=(10, 10))

plt.title('95X001A')
plt.plot(x, y, 's--', c='red', label='Mx vs My', markersize=4) # Graficamos la proyección horizontal
plt.plot(x, z, 's--', c='blue', label='Mx vs Mz', markersize=4) # Graficamos la proyección vertical
plt.axhline(0, c='black', alpha=0.5) # Graficamos la línea horizontal en 0
plt.axvline(0, c='black', alpha=0.5) # Graficamos la línea vertical en 0

# Anotamos los pasos de desmagnetización en las proyecciones
for i, txt in enumerate(example['step']):
    plt.annotate(txt, (x[i], y[i]), size=10, xytext=(4.5, 4.5), textcoords='offset points')
    plt.annotate(txt, (x[i], z[i]), size=10, xytext=(4.5, 4.5), textcoords='offset points')

plt.grid(alpha=0.5)
plt.legend(loc='upper left')
plt.show()
```
<figcaption>Bloque de código para la graficación de proyecciones ortogonales.</figcaption>

<br>

Output:

<div style="text-align:center">
{% include aligner.html images="posts-img/95X001A_ortogonal.png" column=1 %}
<figcaption>Proyecciones ortogonales de la muestra 95X001A.</figcaption>
</div>

<br>

#### Diagramas de desmagnetización
Cuando un imán se expone a altas temperaturas, el calor puede causar que los dominios magnéticos dentro del material se agiten y se desorganicen. Los dominios magnéticos son áreas dentro del imán donde el campo magnético es uniforme y apunta en la misma dirección. Al calentarse, la energía térmica puede hacer que estos dominios se muevan, giren o incluso se inviertan de dirección, lo que hace que el campo magnético global del imán se debilite o desaparezca por completo. La temperatura a la que esto ocurre depende del tipo de imán y su composición, pero en general, cuanto más alta sea la temperatura, más rápidamente perderá sus propiedades magnéticas el imán.

Es debido a esto que cuando tenemos objetos que contienen imanes y estos se exponen a altas temperaturas, pierden su magnetismo y por lo tanto, dejan de funcionar correctamente. Por ejemplo, las tarjetas de crédito que se pasan por la secadora dejan de funcionar en los cajeros, así como las antiguas cintas de cassettes que se dejaban en el tablero del coche bajo el sol, dejaban de sonar igual o perdían el audio por completo. En el siguiente video se explica este efecto de una manera más gráfica:

<br>

<iframe width="100%" height="600" src="https://www.youtube-nocookie.com/embed/Gv7ODvxQ14I" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
<figcaption>Magnetización y desmagnetización explicada.</figcaption>

<br>

De la misma manera, las rocas contienen muchos imanes pequeños y con el tiempo estos pueden cambiar de dirección o incluso crecer, lo que puede dificultar saber la dirección de magnetización original. Sin embargo, algunas partes de la roca aún pueden tener la dirección de magnetización original. Una ventaja es que las partes magnéticas débiles de la roca son más propensas a cambiar o aleatorizarse con el tiempo en comparación con las partes magnéticas más fuertes que mantienen la dirección magnética antigua.[^1]

Un diagrama de desmagnetización muestra la magnetización remanente de una muestra de roca en función del campo magnético aplicado durante la desmagnetización. La magnetización remanente es la cantidad de magnetismo que queda después de que la muestra se ha desmagnetizado. La magnetización remanente se mide en unidades de magnetización como amperios por metro $$(A/m)$$ o en unidades de polarización magnética como los teslas $$(T)$$.

En *PmagPy* se pueden generar estos diagramas de desmagnetización con la función `ipmag.plot_dmag()`, a continuación se muestra un ejemplo de su uso:

```python
example = pd.read_csv('xitle_data/dec_inc_calculated/95X001A.csv') # Cargamos los datos de la muestra 95X001A

# Renombramos las columnas para que sean compatibles con la función
example.rename(columns={'sample': 'specimen', 'step': 'treat_ac_field', 'M': 'magn_moment'}, inplace=True)

# Si no contamos con una columna de calidad, la creamos y la llenamos con el valor default 'g',
# esto indica que los datos son confiables
example['quality'] = 'g'

plt.figure(figsize=(10, 5)) # Creamos una figura de 10x5
ipmag.plot_dmag(data=example, title="95X001A", fignum=1) # Graficamos el diagrama de desmagnetización
plt.grid(alpha=0.3) # Agregamos una cuadrícula
plt.tight_layout() # Ajustamos el layout
plt.show()
```
<figcaption>Bloque de código para la graficación de diagramas de desmagnetización.</figcaption>

<br>

Output:

{% include aligner.html images="posts-img/95X001A_demag.png" column=1 %}
<figcaption>Diagrama de desmagnetización de la muestra 95X001A.</figcaption>

<br>


#### Estadísticas de Fisher
Las estadísticas de Fisher son un conjunto de técnicas matemáticas utilizadas en paleomagnetismo para analizar la distribución de orientaciones magnéticas en las rocas. Estos métodos fueron desarrollados por *Ronald A. Fisher*, un estadístico británico, a principios de la década de 1950.

Las estadísticas de Fisher se basan en el análisis de los vectores que representan las direcciones magnéticas registradas en la roca. Permiten a los paleomagnetistas determinar si un conjunto de datos es consistente con una cierta dirección del campo geomagnético y calcular los límites de confianza en la estimación de la dirección.

> _It is sometimes said that statistical analyses are used by scientists in the same manner that a drunk uses a light pole: more for support than for illumination. Although this might be true, statistical analysis is fundamental to any paleomagnetic investigation._ Lisa Tauxe, Essentials of Paleomagnetism: Fifth Web Edition, 2018.

En *PmagPy* podemos obtener las estadísticas de Fisher por medio de la función `ipmag.fisher_mean()`, la cual toma como parámetros las inclinaciones y declinaciones medidas de una muestra. A continuación se muestra un ejemplo de su uso:

```python
example = pd.read_csv('xitle_data/dec_inc_calculated/95X001A.csv') # Cargamos los datos de la muestra 95X001A

# Se convierten las columnas de declinación e inclinación a listas
example_decs = example['calc_dec'].to_list()
example_incs = example['calc_inc'].to_list()

# Se calculan las estadísticas de Fisher
fisher_example = ipmag.fisher_mean(example_decs, example_incs)
print(fisher_example)
```
<figcaption>Bloque de código para el cálculo de las estadísticas de Fisher.</figcaption>

<br>

Output:

```
{
    'dec': 44.89886450502263, 
    'inc': -44.07076593082369, 
    'n': 17, 
    'r': 16.978915065585724, 
    'k': 758.8356541989995, 
    'alpha95': 1.295732152200954, 
    'csd': 2.9404320972016995
}
```

<br>

Donde:

- `dec`: Promedio de los valores de declinación.
- `inc`: Promedio de los valores de inclinación.
- `n`: Número de direcciones medidas.
- `r`: Longitud del vector resultante.
- `k`: Parámetro de precisión de Fisher.
- `alpha95`: Radio angular de confianza del 95%.
- `csd`: *Circular Standard Deviation*.

<br>

## Magnetics Information Consortium (MagIC)
El [Consorcio de Información Magnética (*MagIC*)](https://www2.earthref.org/MagIC){:target='_blank' rel='noopener noreferrer'} por sus siglas en inglés, es una organización que mejora la capacidad de investigación en las Ciencias de la Tierra manteniendo un repositorio digital comunitario y abierto para datos paleomagnéticos, con portales que permiten a los usuarios archivar, buscar, visualizar, descargar y combinar estos conjuntos de datos versionados. *MagIC* apoya a las comunidades internacionales dedicadas al paleomagnetismo y se esfuerza por hacer accesibles para todos los datos de archivos privados, haciéndolos (re)utilizables para nuevas actividades científicas y educativas.

<br>

### Base de datos de MagIC
El formato de base de datos MagIC para datos paleomagnéticos es un formato estandarizado utilizado para archivar y compartir datos paleomagnéticos de manera consistente. Es un formato de archivo de texto delimitado por tabuladores que contiene columnas específicas para varios tipos de datos, incluyendo información de la muestra, sitio y espécimen, mediciones paleomagnéticas y metadatos asociados.

A continuación se muestra un ejemplo corto del formato *MagIC* en el que `--` simbolizan un tabulador:

```
tab delimited--contribution
id--version--timestamp--contributor--data_model_version--reference
11927--1--2017-06-22T05:09:47.959Z--@njarboe--3--10.1002/2017GC007049
>>>>>>>>>>
tab delimited--locations
location--location_type--geologic_classes--lithologies--lat_s--lat_n--lon_w--lon_e--continent_ocean--country--age--age_sigma--age_unit
Eastern Sheep Creek--Stratigraphic Section--Extrusive:Igneous:Subaerial--Basaltic-Andesite:Basalt:Andesite--40.70923--40.70923--243.17595--243.17595--North America--United States of America--15.23--0.26--Ma
>>>>>>>>>>
tab delimited--sites
site--location--method_codes--citations--geologic_classes--geologic_types--lithologies--bed_dip--bed_dip_direction--lat--lon--age--age_sigma--age_unit--dir_dec--dir_inc--dir_alpha95--dir_k--dir_n_sample--analysts
E28--Eastern Sheep Creek--GM-ARAR:LT-AF-Z:SO-SM:LP-DIR-AF:FS-FD--This study--Extrusive:Igneous--Lava Flow--Basaltic Lava--6--79.6--40.7--243.2--15.23--0.26--Ma--357.3--47.6--1.4--1949.1--7--Bogue
```

En la [documentación](https://www2.earthref.org/MagIC/help/text-file-format){:target='_blank' rel='noopener noreferrer'} también se incluye un archivo de Excel en el que se encuentran las columnas requeridas para cada sección del formato *MagIC*, esta es una forma más sencilla de comprender los datos necesarios para utilizar este formato.

En la siguiente imagen se describe el proceso que seguiría un proyecto de Paleomagnetismo desde la recolección de muestras, su procesamiento y la conversión de datos a formato *MagIC*.

<br>

<div style="text-align:center">
{% include aligner.html images="posts-img/magic_process.jpg" column=1 %}
<figcaption>Flujo de trabajo de un proyecto típico de Paleomagnetismo que utiliza PmagPy y se integra con la base de datos MagIC. Recuperado de <a href="https://doi.org/10.1002/2016GC006307">https://doi.org/10.1002/2016GC006307</a>.</figcaption>
</div>

<br>

*PmagPy* puede utilizarse de manera independiente a la base de datos *MagIC*, sin embargo, muchos componentes de la librería de Python, así como la GUI (*Graphical User Interface*) y la CLI (*Command Line Interface*) están diseñados para trabajar con datos en formato *MagIC*. Por lo tanto, si se le quiere sacar el máximo provecho a *PmagPy* es recomendable que los datos se encuentren en este formato.[^5]

<br>

#### Comentarios, sugerencias y opiniones
_Espero que este post haya sido de interés para ti, si es así compártelo en tus redes. ¡Te lo agradecería mucho!_

_Si tienes algún comentario, sugerencia u opinión házmelo saber en los comentarios de abajo, no requieres de ninguna cuenta, sólo elige un nombre de usuario (puede ser tu nombre) y un correo (opcional). Todos los comentarios son enviados a un moderador, por lo tanto tardarán un poco en publicarse._

<br>

[^1]: {% include citation.html key="tauxe" %}
[^2]: {% include citation.html key="chatgpt" %}
[^3]: {% include citation.html key="copilot" %}
[^4]: {% include citation.html key="xitle" %}
[^5]: {% include citation.html key="pmagpy" %}