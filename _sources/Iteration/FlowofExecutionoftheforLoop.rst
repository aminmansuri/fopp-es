..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: iter-3-
   :start: 1

.. index:: control flow, flow of execution

Flujo de ejecución del bucle for
---------------------------------

A medida que se ejecuta un programa, el intérprete siempre realiza un seguimiento de qué enunciado es
a punto de ser ejecutado. Llamamos a esto el **flujo de control**, o el **flujo de
ejecución** del programa. Cuando los humanos ejecutan programas, a menudo usan su
dedo para señalar cada declaración a su vez. Entonces podrías pensar en el flujo de control
como "dedo en movimiento de Python".

El flujo de control hasta ahora ha sido estrictamente de arriba a abajo, una declaración a la vez
hora. Llamamos a este tipo de control **secuencial**.
Se supone siempre que el flujo secuencial de control es el comportamiento predeterminado para un programa
de computadora. La declaración ``for`` cambia esto.

El flujo de control a menudo es fácil de visualizar y comprender si dibujamos un diagrama de flujo.
Este diagrama de flujo muestra los pasos exactos y la lógica de cómo se ejecuta la instrucción ``for``.

.. image:: Figures/new_flowchart_for.png
      :width: 300px
      :align: center

.. note::

    ¿No está seguro de qué es un diagrama de flujo? Mira esta versión divertida, en `XKCD <http://xkcd.com/518/>`_. `Y esta otra <http://xkcd.com/1195/>`_.


Una demostración en codelens es una buena manera de ayudarlo a visualizar exactamente cómo fluye el control
funciona con el bucle for. Intente avanzar y retroceder por el programa presionando los botones. Puede ver
el cambio del valor de ``nombre`` a medida que el ciclo recorre la lista de amigos.

.. codelens:: vtest
    :python: py3

    for name in ["Joe", "Amy", "Brad", "Angelina", "Zuki", "Thandi", "Paris"]:
        print("Hi ", name, "  Please come to my party on Saturday!")


Si bien puede parecer que los bucles no son necesarios cuando está iterando sobre algunos elementos, es extremadamente útil cuando
iterando sobre muchos artículos. Imagínese si necesita cambiar lo que sucedió en el bloque de código. A la izquierda, cuando usas
iteración, esto es fácil. A la derecha, cuando ha codificado el proceso, esto es más difícil.
 
.. image:: Figures/iteration_vs_hardcoding.png
   :alt: Demonstration of using iteration over hard coding the iteration.
   :scale: 30%
   :align: center
