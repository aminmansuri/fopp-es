..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: func-1-
   :start: 1

Introducción a las funciones
===============================

.. video:: function_intro
   :controls:
   :thumb: ../_static/function_intro.png

   http://media.interactivepython.org/thinkcsVideos/FunctionsIntro.mov
   http://media.interactivepython.org/thinkcsVideos/FunctionsIntro.webm

En Python, una **función** es un fragmento de código que realiza alguna operación que es significativa para una persona para considerarla como una unidad completa, por ejemplo, calcular el GPA de un estudiante en un sistema de aprendizaje o responder a la acción de salto en un videojuego. Una vez que se ha definido una función y está satisfecho de que hace lo que se supone que debe hacer, comenzará a pensar en términos de la operación más grande que realiza en lugar de las líneas específicas de código que hacen que funcione.

Este desglose de una tarea o problema es crucial para la implementación exitosa de cualquier programa de más de 50 líneas (y muchas más pequeñas también). Por ejemplo, el programa que muestra la página de inicio de Instagram está compuesto por funciones que:

* muestra la barra de encabezado
* muestra las publicaciones de tus amigos
* muestra las historias de tus amigos
* muestra el anuncio en la parte inferior de la pantalla recomendando que uses la aplicación

Y cada uno de esos está compuesto de funciones también. Por ejemplo, la función que muestra las publicaciones de tus amigos es un bucle for que llama a una función para:

* mostrar una sola publicación que a su vez llama a las funciones para:
* mostrar la foto y el nombre de la persona que publica la historia
* mostrar la foto en sí
* mostrar "Me gusta" de otros usuarios a la historia
* mostrar los comentarios en la historia
* etc.

En este capítulo aprenderá sobre funciones con nombre, funciones a las que se puede hacer referencia por nombre cuando desee ejecutarlas.


Temas
------

* funciona como un medio de abstracción
* alcance local y global
* efectos secundarios

Objetivos de aprendizaje
-------------------------

Al final de este capítulo, debería poder:

* Identificar parámetros formales y valores de parámetros en una muestra de código
* Predecir el valor de retorno de una función dados los valores de parámetros de muestra
* Definir funciones con nombres apropiados para el parámetro formal
* Evitar el uso de variables globales en las definiciones de funciones creando parámetros formales para todos los valores necesarios
* Identificar si una función tiene algún efecto secundario
