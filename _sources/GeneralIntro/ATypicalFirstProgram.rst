..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: intro-7-
   :start: 1

.. index:: depuración, error

Un primer programa típico
-------------------------

Tradicionalmente, el primer programa escrito en un nuevo idioma se llama *Hola,
Mundo!* Porque todo lo que hace es mostrar las palabras ¡Hola Mundo! en Python, el código fuente
se ve como esto.

.. sourcecode:: python

    print("¡Hola, mundo!")

Este es un ejemplo del uso de la **función print**, que en realidad no
imprime cualquier cosa en papel. Muestra un valor en la pantalla. En este caso, el resultado es la frase:

::

    ¡Hola Mundo!

Aquí está el ejemplo en una ventana de activecode, donde puede ejecutarlo y modificarlo.

.. activecode:: ac1_7_1

    print("¡Hola, mundo!")

Las comillas en el programa marcan el principio y el final del valor.
No aparecen en el resultado. Aprenderá más sobre por qué en el próximo capítulo.

Algunas personas juzgan la calidad de un lenguaje de programación por la simplicidad de
el programa hola mundo!. Según este estándar, Python funciona tan bien como es
posible.

**Chequea tu entendimiento**

.. mchoice:: question1_7_1
   :answer_a: Envía información a la impresora para que se imprima en papel.
   :answer_b: Muestra un valor en la pantalla.
   :answer_c: Le dice a la computadora que ponga la información en formato impreso, en lugar de cursiva.
   :answer_d: Le dice a la computadora que diga la información.
   :correct: b
   :feedback_a: Dentro del lenguaje de programación Python, la declaración de impresión no tiene nada que ver con la impresora.
   :feedback_b: Sí, la declaración de impresión se usa para mostrar el valor de la cosa que se está imprimiendo.
   :feedback_c: El formato de la información se llama su fuente y no tiene nada que ver con la declaración de impresión.
   :feedback_d: ¡Eso sería bueno! Pero no...

    La función print:
