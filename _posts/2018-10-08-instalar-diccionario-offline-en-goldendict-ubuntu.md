---
layout: post
title: "Instalar Diccionario off-line en GoldenDict Ubuntu"
date: 2018-10-08 14:42:49
tags: ['ubuntu']
published: true
comments: true
---

<div id="table-of-contents">
<h2>&Iacute;ndice</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#sec-1">1. ¿Qué es GoldenDict?</a></li>
<li><a href="#sec-2">2. Freedict</a></li>
<li><a href="#sec-3">3. Agregar diccionarios de Ingles a Español y viceversa</a>
<ul>
<li><a href="#sec-3-1">3.1. Descargar el diccionario</a></li>
<li><a href="#sec-3-2">3.2. Indicar a GoldenDict la ubicacion del diccionario</a></li>
</ul>
</li>
</ul>
</div>
</div>


# ¿Qué es GoldenDict?<a id="sec-1" name="sec-1"></a>

[GoldenDict](https://github.com/goldendict/goldendict) es un programa, en principio Desktop, que maneja
diccionarios, como traductores y de los que dan la definición de una
palabra. 

Para realizar su función puede obtener desde diccionarios off-line,
servidores y sitios Web.

Por defecto no vienen instalado diccionarios off-line, luego de la
instalación en Ubuntu mediante el centro de software.

# Freedict<a id="sec-2" name="sec-2"></a>

[FreeDict](https://freedict.org) Es un conjunto de diccionarios bilingues en varios idiomas. 

# Agregar diccionarios de Ingles a Español y viceversa<a id="sec-3" name="sec-3"></a>

## Descargar el diccionario<a id="sec-3-1" name="sec-3-1"></a>

Para agregar a GoldenDict de Ingles-Español, la seccion de *Computers*
en [downloads](https://freedict.org/downloads/) escojer *English*.

Inmediatamente se desplegan los diccionarios de Ingles y diferentes
idiomas. Escojer el español y descargar el archivo comprimido.

Descomprimir el archivo y mover la carpeta `eng-spa` contenido en su
interior hacia `/usr/share/goldendict/`. Por ejemplo

    $ sudo mv ~/Downloads/freedict-eng-spa-0.3.dictd/eng-spa/ /usr/share/goldendict/

## Indicar a GoldenDict la ubicacion del diccionario<a id="sec-3-2" name="sec-3-2"></a>

Una vez descargado el diccionario, se debe indicar su ubicacion. En la
barra de menú escojer `Edit->Dictionaries...` para abrir una ventana
con varias pestañas.

En la pestaña `Sources` y el panel derecho presionar `Add..` para
indicar la ruta del diccionario. Seleccionar
`/usr/share/goldendict/eng-spa/` (la carpeta entera) en la nueva
ventana. Luego en `Open` para cerra el diálogo actual.

En mismo panel del botón `Add..`, en la parte inferior presionar
`Rescan now`. Fin.