---
layout: post
title: "Reseña: The Cathedral & The Bazaar"
tags: [Reseña]
excerpt_separator: <!--more-->
permalink: /blog/:year/:title
thumbnail: "assets/img/thumbnails/liubov_popova-composition_with_figures.jpg"
feature-img: "assets/img/thumbnails/liubov_popova-composition_with_figures.jpg"
---

*The Cathedral & The Bazaar* es un libro escrito por el desarrollador de software Eric S. Raymond, muchas veces también descrito como uno de los mejores historiadores del movimiento *open-source*, definido ampliamente en este libro. *The Cathedral & The Bazaar* nos muestra cómo es que este movimiento permitió el desarrollo de Linux, uno de los sistemas operativos que cambiaría al mundo por completo.

<!--more-->

Este libro es un conjunto de ensayos escritos entre 1992 y 1999, que describen (en palabras del autor) *software open-source, el proceso de aprovechar sistemáticamente el desarrollo abierto y la revisión por pares descentralizada para reducir costes y mejorar la calidad del software.*

> **NOTA:** A lo largo de este post utilizaré la palabra *hacker* para referirme a los que Raymond denomina como los *verdaderos programadores*, aquellas personas que creaban software por diversión cuando las computadoras eran una novedad.

En este post podrás encontrar un pequeño resumen de cada uno de los capítulos del libro seguido de mi experiencia al leerlo.

* TOC
{:toc}

## A Brief History of Hackerdom
En este primer capítulo, Raymond nos remonta a los orígenes de la cultura *hacker*, en 1961, cuando el MIT compró su primera PDP-1, una de las primeras "minicomputadoras" de ese entonces. Antes de este ordenador, la mayoría de las computadoras funcionaban en modo *batch*, es decir, se ingresaban programas en tarjetas perforadas y la computadora lo procesaba. El PDP-1 permitió interacción directa con la máquina, usando teclado, interruptores y pantallas. 

<div class="container" align="center">
    {% include aligner.html images="posts-img/PDP-1.jpeg" column=1 %}
    <figcaption>Ordenador PDP-1 (Programmed Data Processor-1). Imagen de Matthew Hutchinson - <a rel="nofollow" class="external free" href="https://www.flickr.com/photos/hiddenloop/307119987/">https://www.flickr.com/photos/hiddenloop/307119987/</a>, <a href="https://creativecommons.org/licenses/by/2.0" title="Creative Commons Attribution 2.0">CC BY 2.0</a>, <a href="https://commons.wikimedia.org/w/index.php?curid=1587541">Enlace</a></figcaption>
</div>

<br>

La comunidad *hacker* del MIT tuvo mayor influencia después de 1969, cuando el proyecto ARPANET (Advanced Research Projects Agency Network) se hizo una realidad, inicialmente se trataba de un proyecto del Departamento de Defensa de Estados Unidos para hacer la primera red transcontinental de computadoras pero eventualmente se convirtió en una red que conectó un gran número de universidades, creando un espacio de colaboración e innovación. DARPA (Defense Advanced Research Projects Agency), notó el crecimiento de la red al grado de tener mucha actividad no autorizada, la cual dejó pasar por alto como un pequeño precio a pagar por atraer a una generación de gente brillante al campo del cómputo.

<br>

### The Rise of Unix
Al momento en el que ARPANET surgió, Ken Thompson creó Unix, un sistema operativo multiusuario y multitarea. A la par del desarrollo de Thompson, Dennis Ritchie desarrolló el lenguaje de programación C, el cual reemplazaría gran parte del código ensamblador de Unix para convertirlo en un sistema operativo portátil que pudiera ejecutarse en un gran número de computadoras. Las implicaciones que tuvo tener un sistema operativo que funcionara en diferentes ordenadores cambiaba completamente el panorama para los usuarios, ya que no sería necesario pagar por diseños de ordenadores completamente nuevos cuando quedaran obsoletos. En pocas palabras, esto le dió a los hackers una plataforma común para desarrollar sus programas sin la necesidad de reinventar la rueda en cada ordenador.

Desde 1970 hasta 1990 hubo un boom de sistemas operativos, herramientas y esfuerzos por comercializar las computadoras. Para 1975, la Altair 8800 se consideró la primera computadora personal en salir al mercado, en la cual Bill Gates y Paul Allen desarrollaron Altair BASIC, el primer producto importante de Microsoft. Un año después se estaría lanzando la Apple I, la cual ponía en marcha una carrera comercial en computadoras personales.

<div class="container" align="center">
    {% include aligner.html images="posts-img/Altair_8800.jpeg" column=1 %}
    <figcaption>Kit de la Altair 8800 con 8 KB de memoria. Imagen de MITS staff - Scanned from the August 1975 Radio-Electronics magazine (page 1) by Michael Holley <a href="//commons.wikimedia.org/wiki/User:Swtpc6800" title="User:Swtpc6800">Swtpc6800</a>, Dominio público, <a href="https://commons.wikimedia.org/w/index.php?curid=7219892">Enlace</a></figcaption>
</div>

<br>

Con el lanzamiento de Windows por parte de Microsoft en 1985 y su gran poderío de marketing, la prensa hablaba bastante de la desaparición inminente de Unix, a pesar de que Windows era un sistema operativo bastante inferior a lo que ofrecía Unix en ese entonces.

<br>

### The Early Free Unixes
Por fortuna para la comunidad open source, en 1991, en la Universidad de Helsinki, un estudiante de 21 años llamado Linus Torvalds inició el desarrollo de un kernel de Unix gratuito para máquinas 386 (Microprocesador Intel 32-bit), más tarde, este exitoso proyecto tomaría el nombre de *Linux*. En sus inicios, la característica más relevante de Linux no era su alcance técnico, sino el social. 

Hasta este momento, se creía que un software tan complejo como un sistema operativo debía desarrollarse de manera cuidadosamente coordinada, por grupos de trabajo pequeños o empresas con mucha experiencia, es aquí donde se menciona por primera vez en el libro el término **Cathedral** para referirse a un modelo de desarrollo cerrado, centralizado y estrictamente controlado, modelos que existen hoy en día en las grandes empresas de tecnología.

Linux evolucionó de una manera completamente distinta, su crecimiento se vió influenciado por un enorme número de desarrolladores colaborando en el mismo proyecto solamente coordinados por internet. La calidad del kernel se mantenía a través de *releases* continuas (se liberaba una versión nueva prácticamente cada semana), y con estas releases se obtenían cientos de revisiones de todos los desarrolladores que participaban en el proyecto. Raymond lo llama una *selección Darwiniana* de cada nueva versión. Para 1993, bajo este modelo de trabajo, Linux ya competía con muchas versiones comerciales de Unix. El autor hace referencia a este modelo de trabajo como el **Bazaar**.

<br>

## The Cathedral & The Bazaar
El estilo de desarrollo de Linus Torvalds se definió como *liberar versiones de manera temprana y rápida, delega todo lo que puedas y sé lo más abierto posible*. En este capítulo, el autor nos proporciona una serie de 19 "acuerdos" mediante un programa de su creación para desarrollar un proyecto al estilo de Linux. Aquí dejo los que más me gustaron.

- Los buenos programadores saben qué escribir. Los excelentes programadores saben qué reescribir (y reutilizar).
- "Plan to throw one away; you will, anyhow." ó bien, prepárate para empezar de cero al menos una vez.
- Libera pronto. Libera con frecuencia.
- "Given enough eyeballs, all bugs are shallow."
- Las estructuras de datos inteligentes y el código simple funcionan mucho mejor que al revés.
- "Perfection (in design) is achieved not when there is nothing more to add, but rather when there is nothing more to take away."
- Para resolver un problema interesante, comienza por encontrar un problema que sea interesante para ti.

Raymond utiliza su proyecto de ejemplo para describir y comprobar cada uno de los puntos que menciona a partir de su propia experiencia mientras compara sus resultados con lo que en ese entonces era Linux.

Una de las mejores formas de describir lo que se quiere comunicar en este capítulo es con la "Ley de Conway".

> Organizations which design systems are constrained to produce designs which are copies of the communication structures of these organizations.

<br>

## Homesteading The Noosphere
En este capítulo, el autor toca un tema muy relevante sobre el uso que se le daría al software *open source* en los años siguientes al boom de Linux. En distintos subcapítulos nos habla sobre algunos tecnicismos de licencias *open source* y de cómo la cultura hacker se fue transformando para adaptarse a un mundo en el que el software comercial ganaba cada vez más terreno. Una parte bastante interesante de este capítulo es la meción de la "Teoría de Locke" sobre el título de propiedades. Esta teoría se refiere principalmente a obtener o poseer tierras, pero Raymond adapta estos conceptos a la cultura *open source* y a la forma en la que se debe gestionar un proyecto. En esta teoría hay 3 maneras de obtener tierras (o en este caso, software).

Donde existen tierras que jamás han tenido dueño, uno puede adueñarse del terreno por el simple hecho de ocuparlo, se considera propio por el trabajo de mantenimiento que se realiza en esa tierra, y se defiende como una propiedad.

Otra manera, y una muy común, es mediante la transferencia de la tierra por medio del dueño anterior, la prueba de propiedad es una "cadena" de los propietarios de la tierra hasta su origen.

Finalmente, una tierra puede obtenerse por abandono del propietario anterior, de esta manera, aquel que quiera hacerse cargo y trabajar la tierra, puede ser el propietario de la misma.

Raymond hace su propia comparativa de esta "Teoría de Locke" aplicada al software *open source* mediante sus experiencias trabajando en un proyecto propio y en un proyecto ajeno que eventualmente se le fue delegado por el simple hecho de trabajar en él, esta parte la considero sumamente interesante ya que describe de manera bastante detallada las "reglas" no escritas en la cultura hacker sobre lo que debería suceder con cualquier proyecto *open source*. Raymond nos proporciona las siguientes 6 reglas que considera relevantes:

1. Si no funciona tan bien como me han hecho creer que lo hará, no sirve para nada, por muy ingenioso y original que sea.
2. Es mejor realizar un trabajo que amplíe la noosfera que uno que duplique un área funcional ya existente.
3. El trabajo que llega a una distribución importante es mejor que el que no. El trabajo que se publica en todas las distribuciones importantes es el más prestigioso.
4. El uso del software es la forma más sincera de halago, y los líderes de categoría son mejores que los mediocres.
5. La dedicación constante al trabajo duro y aburrido (como la depuración o la redacción de documentación) es más loable que ser selectivo para hacer solo lo fácil y divertido.
6. Las extensiones de funciones que no son triviales son mejores que los parches de bajo nivel y la depuración.

Este capítulo entra en muchos detalles sobre todas estas reglas no escritas por los hackers y la cultura *open source*, para personas que están adentrándose en el mundo del desarrollo de software puede llegar a ser muy interesante.

<br>

## The Magic Cauldron
Este capítulo se centra en las diferentes maneras que existen de hacer negocio con el software, Raymond describe los diferentes modelos mediante los cuales obtiene su valor el software. También nos demuestra por qué existen algunas asumpciones respecto al costo del software que son falsas.

Por ejemplo, Raymond menciona que en los inicios del software comercial su valor se le daba de una manera similar que en una cadena de producción de bienes materiales, como un valor proporcional al costo de su producción, sin embargo, asumir esto es incorrecto. A lo largo del capítulo se mencionan las características más relevantes que dan valor al software, desde su creación, su mantenimiento y su eventual necesidad de actualizarse.

Uno de los puntos más relevantes de este capítulo es la comparativa que se realiza sobre "abrir" un software comercial o bien, mantenerlo privado. Raymond explora muchos escenarios en los que esta estrategia puede ser beneficiosa para alguna organización con fines de lucro, algo que para el momento en el que se escribió este libro era sumamente raro.

Mi ejemplo favorito es el de la decisión de *Netscape Communications*, la entonces compañía fundadora de *Netscape Navigator*, de abrir el código fuente de su navegador en 1998 para no seguir perdiendo ganancias contra el famoso *Internet Explorer* de Microsoft. Esta estrategia funcionó a la perfección y dió origen al navegador *Mozilla Firefox*, el cual sigue siendo *open source* hoy en día. Raymond utiliza muchos otros ejemplos como este para hacerle saber al lector las distintas estrategias que desde entonces (y hasta la actualidad) han sido de utilidad en el software comercial.

Algo que me intrigaba mucho desde que empecé a adentrarme en el mundo *open source* era ¿cómo un software gratuito y abierto puede ser un buen negocio?, este capítulo responde rotundamente a esta pregunta.

<br>

## The Revenge of The Hackers

> *"OSS (open-source software) poses a direct, short term revenue and platform threat to Microsoft -- particularly in server space. Additionally, the intrinsic parallelism and free idea exchange in OSS has benefits that are not replicable with our current licensing model and therefore present a long term developer mindshare threat."* 
>
> --- Microsoft Internal Strategy Document (a.k.a. Halloween Memo)

Raymond utiliza este capítulo para compartir su experiencia mientras se convertía en una de las figuras más relevantes de la propaganda *open source*. Aquí se describe cómo después del boom del software libre se llevó este movimiento a cada rincón del mundo, sobre todo después del gran efecto que tendría la filtración del *Halloween Memo*, el cual asumía el *open source* como una amenaza para los modelos de negocio de los gigantes de la tecnología en ese entonces.

<br>

## Author's Afterword: Beyond Software?
Raymond cierra esta entretenida recopilación de ensayos con algunas ideas de cómo se podría aplicar el movimiento *open source* fuera del software, ya sea en artes, política o por sí solo, como un debate filosófico.

Finalmente, el autor nos deja algunos recursos y tips para consultar que pueden ser de gran interés para quien quiera profundizar más en el mundo *open source*.

<br>

**Comentarios, sugerencias y opiniones**
<br>
_Espero que este post haya sido de interés para ti, si es así compártelo en tus redes. ¡Te lo agradecería mucho!_

_Si tienes algún comentario, sugerencia u opinión házmelo saber en los comentarios de abajo, no requieres de ninguna cuenta, sólo elige un nombre de usuario (puede ser tu nombre) y un correo (opcional). Todos los comentarios son enviados a un moderador, por lo tanto tardarán un poco en publicarse._

<br>

[^1]: {% include citation.html key="chatgpt" %}
[^2]: {% include citation.html key="copilot" %}