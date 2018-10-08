---
layout: post
title: "Imagen de fondo, imagen mezclado con texto, paginas pares e impares en LaTeX"
date: 2018-10-07 23:42:49
tags: ['latex']
published: true
comments: true
---

# Resumen

Con este tuto el lector podrá poner una imágen de fondo o marca de
agua como también se le conoce, en un artículo hecho en LaTeX. Así
mismo, poner numerados de páginas en disposición para imprimir a dos
caras, es decir, que se haga distición de páginas pares e
impares. También, insertar una imagen --en alguna seccion-- y hacer que
el texto rodee la imágen.


**Nota**: Puedes obtener la versión del post: [Imágen de fondo, imagen mezclado con texto, paginas pares e impares en LaTeX](https://www.dropbox.com/s/hyu05jzu457je6j/imagen-fondo-imagen-mezclado-con-texto-en-Latex.pdf?dl=0) en fomato pdf.

# Imagen de fondo

Poner una imagen de fondo, en un documento tipo *article*, requiere
basicamente de tres instrucciones que van en el preámbulo, y una que
va entre `\begin{document}...\end{document}`.

Las tres instrucciones en el preámbulo son:
- El paquete *graphicx* para la inserción de graficos.
- El paquete *eso-pic* que permitirá una imágen de fondo.
- La definición de un comando llamado *imgFondo* para la inserción de la imágen de fondo.

Prácticamente sería de insertar los siguente:

{% highlight latex  %}
\usepackage{graphicx} % graficos en jpg, png, svg, etc.
\usepackage{eso-pic} % imagen de fondo

\newcommand\imgFondo{ %
   \put(0,0){ %
     \parbox[b][\paperheight]{\paperwidth}{ %
       \vfill
       \centering
       \includegraphics[width=\paperwidth,height=\paperheight, %
       keepaspectratio]{miImagen.png} %
       \vfill
}}}  
{% endhighlight %}

A grandes rasgos, el comando utiliza un tipo de caja ( `\parbox` ) que
cubre todo el alto del papel ( `\paperheight` ) y todo el ancho (
`\paperwidth` ). Dentro de esta caja se inserta un imágen, también
cubriendo todo el ancho y alto del papel, centrándose verticalmente
con `\vfill` y horizontalmente con `\centering` . Mediante
`\includegraphics` se incluye el fondo llamado *miImagen.png*, en este
caso en formato png.

Ahora, se coloca `\AddToShipoutPictureBG*{\imgFondo}` en donde se quiera
la imágen de fondo. Si se quiere en todas las páginas se coloca:

{% highlight latex  %}
\AddToShipoutPictureBG{\imgFondo}
{% endhighlight %}
imediatamente despues de `\begin{document}`.

# Páginas pares, impares

La distición entre páginas pares e impares del documento, pdf
generalmente, resultante, acomoda los margenes y la numeración de las
mismas a fin de garantizar la correcta visualización al momento en que
éstas sean impresas y ordenadas en forma de revista o libro.

En primera instancia se elije la opción twoside en la instrucción `\documentclass`:

{% highlight latex  %}
\documentclass[twoside,10pt]{article}
{% endhighlight %}

a continuación se coloca lo siguiente en el preámbulo, justo antes de
`\begin{document}` puede ser

{% highlight latex  %}
\pagestyle{headings} % elegir estilo de pagina
\setlength{\oddsidemargin}{8 mm} 
\setlength{\evensidemargin}{2 mm}
{% endhighlight %}
eso es todo.

# Imagen con texto

Fundir una imágen con texto es los que puede hacerse con los paquetes
`graphicx` y `wrapfig`.

El texto bordea la imágen dando un aspecto ideal. Para ello se cargan
los paquetes mencionados asi:

{% highlight latex  %}
\usepackage{graphicx} 
\usepackage{wrapfig}
{% endhighlight %}

A continuación se pone el código de inserción en el punto donde se
requiera su visualización en el pdf resultante

{% highlight latex  %}
\begin{wrapfigure}{l}{6cm}
\caption{Imagen rodeada}
\includegraphics[height=4cm, width=5cm]{miImagen.png}
\end{wrapfigure}
{% endhighlight %}

La letra "l" dice que la imágen será puesta al margen izquierdo,
también puede ponerse "r" si se quiere del lado derecho. Los "6cm"
indica la anchura del espacio que se correrá el texto. La imágen a
insertar es llamada miImagen.png dandole un alto de cuatro centímetros
y un ancho de cinco centímetros.