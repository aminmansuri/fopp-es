..  Copyright (C)  Brad Miller, Paul Resnick, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, Dario Mitchell, and Jackie Cohen.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-15-
   :start: 1

👩‍💻 Hard-Coding
-----------------

Cuando comience a programar, verá que hay muchas formas de resolver problemas. También encontrará que una de las emociones
de programación es la facilidad con la que puedes hacer cosas correctamente en las que cualquiera podría cometer errores fácilmente. Por ejemplo,
crear un código muy pequeño para encontrar el carácter 1047 en una oración que podría ser miles de
letras, aprenderá cómo hacer exactamente el mismo cálculo con muchos datos diferentes.

A menudo le diremos en este libro de texto *no implemente hard-code* para las respuestas. Qué significa eso?

Algunas cosas en la programación solo se pueden hacer escribiéndolas. Como has visto, cuando tienes que asignar un valor a una
variable, simplemente escribe algo como ``xyz = 6``. Ninguna otra manera.

Pero en la mayoría de los casos, es mejor no hacer cálculos en su cabeza o escribir respuestas completas a los problemas de programación a
mano. Ahí es donde entra **Hard Coding**. "No codificar" básicamente significa que debe confiar en su código, su lógica,
su programa, y usted *no* debería escribir las cosas a mano o hacer cálculos en su cabeza, incluso si puede hacerlo fácilmente.

Cuando esté escribiendo código o trabajando en la respuesta a un ejercicio de programación, debe preguntarse: *¿Mi respuesta sería
correcta incluso si las variables proporcionadas tienen valores diferentes?* Si la respuesta a esa pregunta es no, probablemente sea
Hard Coding, que debe evitar, ¡y probablemente haya al menos una forma un poco más concisa de construir su respuesta!

Por ejemplo, en este código siguiente, si se le pide en un ejercicio que cree una variable ``zx`` y le asigne el valor de
la suma del valor de ``y`` y el valor de ``x``, escribiendo ``zx = 55`` es *hard-coding*.

.. actex:: hard_coding_example
   
   x = 20
   y = 35
   abc = 62

La operación ``20 + 35`` puede ser matemática fácil de hacer en su cabeza o con una calculadora, pero cuando aprende a programar, usted
debe capacitarse para notar patrones útiles de cómo resolver problemas que le facilitarán la vida (quizás
más allá de la programación, incluso).

La forma correcta de responder a ese tipo de ejercicio sería escribir: ``zx = y + x`` (o ``zx = x + y``, ya que simplemente
recordó el orden de las operaciones). Eso no es  hard-coding, y será correcto sin importar que valores de ``x``
e ``y`` sean.

En el código anterior, si el valor de ``x`` fuera ``40``, ``55`` no sería el valor correcto para ``zx``. Pero
``zx = y + x`` aún sería absolutamente correcto.

Intente todo lo que pueda para no confiar en su brillante pero falible cerebro humano para hacer *código* cuando programe -- use
¡su cerebro para determinar cómo escribir el código correcto para resolver el problema por ti! Es por eso que le pedimos que evite
el hard-coding para la mayoría de los ejercicios en este libro.
