---
layout: post
title: Cómo hacer este sitio
tags: [Jekyll, GithubPages, HTML, CSS]
excerpt_separator: <!--more-->
permalink: /blog/:year/:title
thumbnail: "assets/img/thumbnails/computer.jpeg"
feature-img: "assets/img/thumbnails/computer.jpeg"
---

En este *meta-post* quiero explicar de manera general cómo fue que creé mi sitio web usando Jekyll y Github Pages, así como los conocimientos y recursos básicos que necesitas si quieres crear tu propio sitio web.

<!--more-->

[Jekyll](https://jekyllrb.com/){:target="_blank" rel="noopener noreferrer"} es un generador de sitios web estáticos, los sitios web estáticos son aquellos que suelen tener una estructura simple, no requieren de una conexión a una base de datos y siempre muestran el mismo contenido a todos los usuarios, por lo tanto dichos sitios son más rápidos. Los sitios web estáticos son ideales para crear blogs, sitios de presentación personal o de documentación.

{% include aligner.html images="posts-img/jekyll-logo.png" %}

<br>

## Requerimientos
Crear un sitio web estático con Jekyll requiere de habilidades y conocimientos muy fáciles de obtener por medio de tutoriales o cursos online, algunos de estos conocimientos se muestran a continuación:
- Tener conocimientos básicos de la terminal del sistema (cmd)
- Nociones en la estructura de HTML y CSS
- Entender las funciones de las [RubyGems](https://rubygems.org/){:target="_blank" rel="noopener noreferrer"}
- *Opcional:* Manejo de repositorios de [Github](https://github.com/){:target="_blank" rel="noopener noreferrer"}

También se requieren recursos como:
- Un editor de texto de tu preferencia (yo utilizo [VScode](https://code.visualstudio.com/){:target="_blank" rel="noopener noreferrer"})
- Descargar e instalar [Ruby](https://www.ruby-lang.org/es/){:target="_blank" rel="noopener noreferrer"} en tu ordenador
- *Opcional:* Crear una cuenta en [Github](https://github.com/){:target="_blank" rel="noopener noreferrer"}

**Importante:** *Esta documentación está pensada en Windows 10, sin embargo, no difiere mucho de sistemas macOS o Linux.*

<br>

## Instalando Jekyll
Lo primero que debemos hacer es instalar Jekyll en nuestro ordenador (aquí estoy asumiendo que ya tienes Ruby instalado):
- [_Tutorial de instalación de Ruby en Windows y Mac._](https://youtu.be/LfP7Y9Ja6Qc){:target="_blank" rel="noopener noreferrer"}

\>> Abrimos una terminal, puedes dar clic en "Buscar" y teclear cmd (también se suele llamar "Símbolo del sistema"):

{% include aligner.html images="posts-img/windows_cmd.png" column=1 %}

\>> Introducimos los siguientes comandos en la terminal:

Con este comando tendremos a Jekyll instalado en nuestro sistema:
```bash
gem install jekyll bundler
```

Ahora iremos al directorio en donde queramos almacenar nuestro sitio web de manera local (aún no estará en línea):
```bash
cd ruta/a/tu/directorio
```

Una vez que nos encontremos en nuestro directorio podemos crear nuestros archivos básicos con Jekyll:
```bash
jekyll new nombre-de-tu-sitio
```

Con estos comandos Jekyll creará los archivos básicos para comenzar a crear tu sitio web.

<br>

## Visualizar mi sitio web
Si quieres visualizar el sitio en un navegador introduce los siguientes comandos en tu terminal.

Para que Jekyll establezca el servidor de tu sitio de manera local debes de encontrarte en la carpeta que contiene todos los archivos que Jekyll acaba de crear:
```bash
cd nombre-de-tu-sitio
```

Cuando establecemos el servidor local para nuestro sitio web por primera vez es necesario introducir el siguiente comando:
```bash
bundle exec jekyll serve
```

Después de la primera vez, solamente será necesario el comando `jekyll serve` para iniciar el servidor.

La terminal nos arrojará la dirección `http://127.0.0.1:4000/` (la dirección puede variar en tu sistema operativo) la cual corresponde al servidor en el que visualizaremos nuestro sitio web, copia la dirección completa y pégala en tu navegador.

Ahora puedes visualizar todos los cambios que hagas en tu sitio, solamente modifica tus documentos desde tu editor de texto, guarda los cambios, y vuelve a cargar tu página. Los cambios pueden tardar un poco en reflejarse en tu página dependiendo de la capacidad de tu computadora.

<br>

## Añadir contenido y personalizar
De aquí en adelante el diseño de tu sitio y su contenido depende de ti, puedes agregar y quitar el contenido que quieras, incluso puedes buscar más temas gratuitos de tu preferencia en [Jekyll Themes](https://jekyllthemes.io/free){:target="_blank" rel="noopener noreferrer"}, cada tema contiene sus instrucciones de uso y algunos ejemplos para que puedas darte una idea de cómo se ve el sitio web. El tema en el que me basé para crear mi sitio se llama [Type-on-Strap](https://github.com/sylhare/Type-on-Strap){:target="_blank" rel="noopener noreferrer"}.

<br>

## Hosting
Elegir el hosting para tu sitio web es tu decisión, existen muchos servicios de hosting tanto gratuitos como de paga que ofrecen distintas herramientas para que puedas manejar tu página de una manera más sencilla. Yo elegí [Github Pages](https://pages.github.com/){:target="_blank" rel="noopener noreferrer"} ya que es gratuito, seguro y fácil de editar tratándose de páginas como la que estás viendo, lo único que necesitas es una cuenta de Github y seguir las instrucciones para poner tu sitio en línea.

{% include aligner.html images="posts-img/githubpages.jpg" column=1 %}

También puedes ver el código fuente de mi página en [mi perfil de Github](https://github.com/JCBucio){:target="_blank" rel="noopener noreferrer"}, está abierto al público y puede ser reutilizado por cualquiera. Para hacer este sitio me inspiré en la página web del [Dr. Christopher Lovell](https://www.christopherlovell.co.uk/){:target="_blank" rel="noopener noreferrer"}, dale un vistazo! Tiene muy buen contenido.

En mi [portafolio](/portafolio/Mi-sitio-web) escribí acerca de mi experiencia realizando este proyecto, también añadí recursos útiles para sacarle todo el provecho a Jekyll, así como las fuentes que utilicé para crear el sitio.

<br>

#### Comentarios, sugerencias y opiniones
_Espero que este post haya sido de interés para ti, si es así compártelo en tus redes. ¡Te lo agradecería mucho!_

_Si tienes algún comentario, sugerencia u opinión házmelo saber en los comentarios de abajo, no requieres de ninguna cuenta, sólo elige un nombre de usuario (puede ser tu nombre) y un correo (opcional). Todos los comentarios son enviados a un moderador, por lo tanto tardarán un poco en publicarse._
