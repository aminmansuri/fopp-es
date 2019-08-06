..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: debug-1-
   :start: 1

Introducción a la Depuración
============================

.. rst-class:: blockquote

    "El arte de la depuración es descubrir lo que realmente le dijo a su programa que hiciera en lugar de lo que creía que le dijo que hiciera". - Andrew Singer


Este capítulo pasará un tiempo hablando de lo que sucede cuando se producen errores y de cómo solucionarlo.
Los errores que inevitablemente encontrarás.

Antes de que las computadoras se vuelvan digitales, la depuración podría significar buscar insectos que impidan el funcionamiento de los relés físicos como en este caso `apocryphal tale <https://www.computerworld.com/article/2515435/app-development/moth-in-the-machine--debugging-the-origins-of--bug-.html>`_ acerca de `Admiral Grace Hopper <https://en.wikipedia.org/wiki/Admiral_Grace_Hopper>`_, un pionero de la programación.

Hoy en día, la depuración no implica la eliminación de errores en toda la computadora, pero aún puede ser igual de frustrante. Para hacer frente a esta frustración, este capítulo presentará algunas estrategias para ayudarlo a comprender por qué el programa que escribió no se comporta según lo previsto.

Metas de Aprendizaje
--------------------

* Entender buenas estrategias de programación para evitar errores.
* Comprender tipos comunes de excepciones y sus posibles causas.


Objetivos
---------

* Dado un código, identifique los errores de sintaxis basados ​​en mensajes de error
* Dado un fragmento de código, encuentre el (ValueError, TypeError, SyntaxError, ParseError, NameError)