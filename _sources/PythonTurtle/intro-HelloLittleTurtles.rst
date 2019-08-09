..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: turtle-1-
   :start: 1

.. index::
    object, invoke, method, attribute, state, canvas
    single: module
    single: function
    single: function definition
    single: definition; function
    single: turtle module

.. _turtles_chap:

¡Hola pequeñas tortugas!
========================

.. video:: turtleintrovid
    :controls:
    :thumb: ../_static/turtleintro.png

    http://media.interactivepython.org/thinkcsVideos/turtleintro.mov
    http://media.interactivepython.org/thinkcsVideos/turtleintro.webm

Hay muchos *módulos* en Python que proporcionan características muy potentes que podemos usar en nuestros propios programas.
Algunos de estos pueden enviar correos electrónicos o buscar páginas web. Otros nos permiten realizar cálculos matemáticos complejos.
En este capítulo presentaremos un módulo que nos permite crear un objeto llamado **tortuga** que puede usarse para hacer dibujos

.. turtles and get them
.. turn left, etc.  Your turtle's tail is also endowed with the ability to leave
.. to draw shapes and patterns.

Los gráficos con **turtle**, como se le conoce, se basan en una metáfora muy simple. Imagina que tienes una tortuga que
entiende inglés Puedes decirle a tu tortuga que haga comandos simples como avanzar y girar a la derecha. A medida que la tortuga
se mueve, si su cola está hacia abajo tocando el suelo, dibujará una línea (dejará un rastro) mientras se mueve. Si le  dice
a su tortuga que levante la cola, todavía puede moverse pero no dejará rastro. Como verás, puedes hacer algunos dibujos bastante sorprendentes con esta capacidad simple.

.. note::

    Las tortugas son divertidas porque nos permiten visualizar lo que está haciendo nuestro código, pero el verdadero propósito del capítulo es enseñarnos un poco más de Python y desarrollar nuestro tema de pensamiento computacional. Primero dibujarás formas geométricas simples con las tortugas, y luego resumiremos los conceptos y la sintaxis que has aprendido, en particular, las clases, las instancias y las invocaciones de métodos. Estos conceptos son los componentes básicos de la programación orientada a objetos, un paradigma para estructurar un programa que está muy extendido en todos los lenguajes de programación modernos.

Metas de aprendizaje
--------------------

* Comprender el uso de bucles como una forma de repetir acciones
* Comprender el control de flujo y la iteración a través del ciclo for
* Comprender la idea de secuencia (o lista) de números
* Introducir la idea de buscar patrones al resolver problemas
* Distinguir entre instancias, atributos y métodos.

Objectivos
-----------

* Escribir un programa multilínea (usando el framework de turtle)
* Invocar métodos y establecer atributos usando la notación de puntos
* Use la función de rango para crear la secuencia correcta de números
* Use el bucle for para dibujar formas geométricas comunes con la tortuga

