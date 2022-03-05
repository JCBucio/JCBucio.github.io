---
layout: post
title: Automatizar reportes por email con Python
tags: [Python, SMTP, Matplotlib, Pandas]
excerpt_separator: <!--more-->
permalink: /blog/:year/:title
thumbnail: "assets/img/thumbnails/terminal.jpg"
feature-img: "assets/img/thumbnails/terminal.jpg"
---

[Python](https://www.python.org/){:target="blank" rel="noopener noreferrer"} es un lenguaje de programación muy popular en la actualidad, sus aplicaciones se encuentran en la ciencia de datos, _machine learning_, desarrollo web, _blockchain_, entre otros. En este post veremos cómo este lenguaje puede ayudarte a automatizar tareas en tu ordenador.

<!--more-->

Es bastante común que cuando se trata de procesamiento de datos esta acción se torne tediosa ya que requiere ingresar comandos en la terminal de manera repetitiva, la mayoría de estos procesos suelen tomar bastantes horas, o incluso hasta días.

También es muy común que en el procesamiento de dichos datos necesitemos realizar alguna clase de reporte o de actualización del proceso para mantenernos a nosotros o a nuestro equipo de trabajo al día respecto a los avances del proyecto que estemos realizando.

<br>

## Ejecutar comandos en la terminal desde Python
Si queremos realizar una serie de tareas en la terminal que implican esperar a que se realicen procesos lentos y revisar el avance de dichos procesos consume mucho tiempo, podemos escribir un pequeño script en Python que nos puede ayudar a ejecutar estos comandos uno tras otro de forma consecutiva, así como escribir el *standard output* o el *standard error* que el programa genere a un archivo de texto que los guarde por nosotros.

```python
import subprocess

# Se ejecuta el comando deseado con subprocess.run()
subprocess.run('python initialize.py', shell=True)

# Se escribe el standard output dentro de un archivo de texto llamado log.txt
with open('log.txt', 'w') as f:
    p1 = subprocess.run('python backfill.py -v -s 2004-09-15 -e 2004-09-24', 
    shell=True, 
    stdout=f,
    stderr=f, 
    text=True)
```
<figcaption>run_command.py</figcaption>

<br>

En este script importamos la librería `subprocess` la cual nos servirá para ejecutar comandos mientras nuestro script esté corriendo. También hay algunos parámetros importantes al llamar esta función:

- `shell=True`: Este parámetro nos permite ingresar múltiples argumentos en nuestro comando.
- `stdout=f`: Aquí asignamos el *standard output* a la variable f para escribirlo en nuestro archivo de texto.
- `stderr=f`: En el caso de que nuestro comando devuelva un error, el *standard error* se asigna a la variable f para escribirlo en nuestro archivo de texto.
- `text=True`: Este parámetro decodifica el output para poder ser leído a manera de texto.

En el código de ejemplo se ejecutan 2 comandos, el primero no escribe el *standard output* ni el *standard error* en ningún lugar ya que es un comando que crea archivos para almacenar datos, el segundo comando lo utilizo para procesar datos sísmicos con el programa [REDPy](https://github.com/ahotovec/REDPy){:target="blank" rel="noopener noreferrer"}, este comando toma más tiempo y escribe el output en el archivo de texto `log.txt`.

<br>

## Enviar un email a través de Python
Si nosotros quisiéramos recibir un correo con los datos que hemos procesado o con actualizaciones de los procesos que se están llevando a cabo en nuestra computadora podemos crear un script para realizar dicha tarea. El programa se definiría de la siguiente manera:

1.- Primero es necesario importar las librerías que nos van a permitir darle formato a nuestro email y conectarnos al servidor del email que utilicemos con mayor frecuencia:

```python
import os
import smtplib
import socket
from email.mime.text import MIMEText
from email.mime.image import MIMEImage
from email.mime.application import MIMEApplication
from email.mime.multipart import MIMEMultipart
```
<figcaption>parte 1/3 mail_notify.py</figcaption>

<br>

2.- Ahora definimos la función que le dará formato a nuestro mensaje, se le añadirá el contenido, asunto y parámetros que nos permitan enviar archivos adjuntos o imágenes en caso de ser necesario:

```python
def message(subject="Python Notification", text="", img=None, attachment=None):
    # Crea el contenido del mensaje
    msg = MIMEMultipart()
    msg['Subject'] = subject    # Agrega el asunto
    msg.attach(MIMEText(text))  # Agrega el texto del contenido

    # Revisa si tenemos una entrada en el parámetro img
    if img is not None:
        # Si tenemos una entrada accesamos a ella y revisamos que sea una lista
        if type(img) is not list:
            img = [img] # Si no es una lista la convertimos en una
        
        # Ahora nos movemos a través de la lista
        for one_img in img:
            img_data = open(one_img, 'rb').read()   # Se leen los datos binarios de la imagen
            
            # Se agregan los datos de la imagen a MIMEMultipart usando MIMEImage,
            # le agregamos el nombre de archivo usando os.basename
            msg.attach(MIMEImage(img_data, name=os.path.basename(one_img)))
    
    # Hacemos lo mismo que realizamos en imágenes para los archivos adjuntos
    if attachment is not None:
        if type(attachment) is not list:
            attachment = [attachment]

        for one_attachment in attachment:
            with open(one_attachment, 'rb') as f:
                # Se lee el documento adjunto con MIMEApplication
                file = MIMEApplication(
                    f.read(),
                    name = os.path.basename(one_attachment)
                )
            # Se editan los metadatos de los archivos adjuntos
            file['Content-Disposition'] = f'attachment; filename="{os.path.basename(one_attachment)}"'
            msg.attach(file)    # Finalmente añadimos los archivos adjuntos al mensaje
    
    return msg
```
<figcaption>parte 2/3 mail_notify.py</figcaption>

<br>

3.- Ahora generamos la función que va a enviar nuestro correo por medio de un servidor `SMTP`:

```python
# Si queremos utilizar gmail, asignamos el servidor SMTP de gmail
def send(msg, server='smtp.gmail.com', port='587'):
    # Se intenta el siguiente código dentro de un bloque try-except en caso de una falla en la red
    try:
        # Inicia una conexión con el servidor seleccionado de email
        smtp = smtplib.SMTP (server, port)
        # Este es el comando 'Extended Hello', realiza un 'saludo' al servidor SMTP o ESMTP
        smtp.ehlo()
        # Ésta es la línea del comando 'Start Transport Layer Security', nos dice que el servidor
        # se estará comunicando con una encriptación TLS
        smtp.starttls()

        # Se leen el email y la contraseña de archivos de texto separados en el directorio '/data'
        with open('../data/email.txt', 'r') as fp:
            email = fp.read()
        with open('../data/pwd.txt', 'r') as fp:
            pwd = fp.read()
        
        # Se inicia sesión en el servidor
        smtp.login(email, pwd)
        # Se envía la notificación al mismo correo
        # Si se quiere enviar a otro destinatario se debe de especificar el correo en lugar 
        # del segundo parámetro de 'email'
        smtp.sendmail(email, email, msg.as_string())
        # Se cierra la sesión
        smtp.quit()
    # En caso de que se produzca una falla en la red, se imprime un mensaje de error
    except socket.gaierror:
        print("\n Network connection error, mail not sent. \n") 
```
<figcaption>parte 3/3 mail_notify.py</figcaption>

<br>

### Crear una gráfica con los datos procesados y enviarla por email
Muchas veces queremos que nuestros datos se vean reflejados en gráficas que nos permitan interpretarlos de una manera más rápida y sencilla. En este ejemplo se utiliza _matplotlib_ y _pandas_ para darle formato a los datos y graficarlos de manera que se puedan realizar interpretaciones más precisas:

```python
import pandas as pd
import matplotlib.pyplot as plt

# Se carga el archivo que nos dará los datos a graficar, en este caso 'dailycounts.csv'
data = pd.read_csv("dailycounts.csv")

# Se le da el formato correcto a los datos con pandas para poder ser graficados en matplotlib
data["Date"] = pd.to_datetime(data["Date"])
months = data.groupby(pd.Grouper(key="Date", freq="1M")).sum()
months.index = months.index.strftime('%B')
months.drop(index=months.index[0], axis=0, inplace=True)

# Una vez listos los datos se asignan a las variables 'x' y 'y'
x = months.index
y = months["Total"]

# Utilizamos matplotlib para personalizar nuestras gráficas
fig, (ax1, ax2) = plt.subplots(2, 1, figsize=(12, 12))

ax1.set_title("Repetitive earthquakes detected one year before the Mayor Cucapah in 2010-04-04\nStations: CI.WES, CI.DRE, CI.SWS", 
fontsize=16, fontfamily='serif')
ax1.bar(x, y, edgecolor='black', color='teal')
ax1.set_ylabel("Number of events", fontweight='bold', fontsize=12)

ax2.plot(x, y, marker='o', color='darkcyan')
ax2.set_xlabel("Months", fontweight='bold', fontsize=12) 
ax2.set_ylabel("Number of events", fontweight='bold', fontsize=12)
ax2.grid()

fig.autofmt_xdate()
plt.tight_layout()

# Descargamos las gráficas creadas con formato .png para después enviarlas por correo
plt.savefig("events_per_month.png")
```
<figcaption>data_analysis.py</figcaption>

<br>

En este script se le dió formato a un archivo llamado `dailycounts.csv` que contiene 365 filas y 862 columnas sobre detecciones de sismos repetitivos, claramente sería muy complicado modificar este archivo en un documento de excel, es por eso que la librería [pandas](https://pandas.pydata.org/){:target="blank" rel="noopener noreferrer"} nos ayuda a realizar las estadísticas y el formato de la tabla sin la necesidad de ver los datos en pantalla.

De igual manera [matplotlib](https://matplotlib.org/){:target="blank" rel="noopener noreferrer"} juega un papel importante ya que nos va a ayudar a generar una gráfica personalizada a nuestro gusto para hacer un análisis más visiblemente detallado de los datos, esta es la gráfica que genera el script:

![REDPy_graphic]({{ "assets/img/posts-img/events_per_month.png" | relative_url }})
<figcaption>Número de sismos repetitivos detectados por 3 estaciones sísmicas un año antes del evento conocido como el Mayor Cucapah de magnitud 7.2Mw con epicentro al norte de Baja California, ocurrido el 4 de abril del 2010.</figcaption>

<br>

## Integrando todas las partes
Ya tenemos nuestro script con las funciones para generar y mandar nuestro email, así como también tenemos nuestro programa que le da formato a nuestros datos y los grafica. Sólo nos queda integrar todos nuestros comandos en el primer script de este post: *run_commands.py*. Tendríamos algo como esto:

```python
import mail_notify
import subprocess

# Se ejecuta el comando deseado con subprocess.run()
subprocess.run('python initialize.py', shell=True)

# Se escribe el standard output dentro de un archivo de texto llamado log.txt
with open('log.txt', 'w') as f:
    p1 = subprocess.run('python backfill.py -v -s 2004-09-15 -e 2004-09-24', 
    shell=True, 
    stdout=f,
    stderr=f, 
    text=True)

# Se ejecuta el script que graficará nuestra información
subprocess.run('python data_analysis.py', shell=True)

# Se crea el objeto para darle formato al correo que notificará que el programa ha sido
# ejecutado de manera exitosa
msg = mail_notify.message(
    subject="REDPy run finished",
    text="Your data is ready to be used.",
    img='events_per_month.png',
    attachment='log.txt'
)

# Se llama la función mail_notify.send() del script mail_notify.py con el parámetro
# del nuevo mensaje y se envía el email
mail_notify.send(msg)
```

<br>

### Más usos y ejemplos
Debido a que Python es un lenguaje muy flexible y lleno de librerías para procesar todo tipo de información podemos darle el uso a estos scripts para prácticamente cualquier proceso que estemos llevando a cabo en nuestro ordenador. Los scripts detallados arriba pueden ser de bastante utilidad en diferentes áreas de la ciencia de datos que están fuera del alcance de este post, éstos son algunos ejemplos:

- Entrenamiento de _machine learning_: [Your First Machine Learning Project in Python](https://machinelearningmastery.com/machine-learning-in-python-step-by-step/){:target="blank" rel="noopener noreferrer"}
- Procesamiento de  _redes neuronales_: [Your First Deep Learning Project in Python](https://machinelearningmastery.com/tutorial-first-neural-network-python-keras/){:target="blank" rel="noopener noreferrer"}
- Reconocimiento de imágenes con _computer vision_: [Start Here with Computer Vision, Deep Learning, and OpenCV](https://www.pyimagesearch.com/start-here/){:target="blank" rel="noopener noreferrer"}
- Análisis de la bolsa de valores y graficación OHLC (_Open, High, Low, Close_): [3 Basic Steps of Stock Market Analysis in Python](https://towardsdatascience.com/3-basic-steps-of-stock-market-analysis-in-python-917787012143){:target="blank" rel="noopener noreferrer"}

<br>

#### Comentarios, sugerencias y opiniones
_Espero que este post haya sido de interés para ti, si es así compártelo en tus redes. ¡Te lo agradecería mucho!_

_Si tienes algún comentario, sugerencia u opinión házmelo saber en los comentarios de abajo, no requieres de ninguna cuenta, sólo elige un nombre de usuario (puede ser tu nombre) y un correo (opcional). Todos los comentarios son enviados a un moderador, por lo tanto tardarán un poco en publicarse._
