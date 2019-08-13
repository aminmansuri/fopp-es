..  Copyright (C) Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. _iter_iterators:

.. qnum::
   :prefix: iter-9-
   :start: 1

Los detalles sangrientos: Iterables
-----------------------------------

La sintasix general de un bucle es:



.. code-block:: python

    for iter_var_name in some_seq:
        # code block line 1
        # code block line 2
        # ...

Después de la palabra ``in``, puede haber cualquier expresión de Python que se evalúe como una secuencia. Ya has visto iteración
sobre cadenas y listas. Una cadena es una secuencia cuyos elementos son caracteres individuales. Una lista es una secuencia cuyos
elementos pueden ser cualquier tipo de objeto Python.

En realidad, el bucle for es un poco más general. Puede iterar no solo sobre cadenas y listas, sino sobre cualquier tipo de
objeto en Python que actúa como una secuencia. Hasta ahora, las cadenas y las listas son todo lo que hemos visto. Pero un
poco más tarde en el curso lo haremos ver tuplas, que son otro tipo de secuencia.

También veremos algunos objetos de Python que actúan como secuencias con el propósito de iterar con un bucle for.
Éstos incluyen objetos de archivo, vistas e iteradores.

De hecho, ya hemos visto uno de estos sin darnos cuenta, porque casi no importa. Técnicamente, el
La función ``rango`` en realidad no devuelve una lista. Es decir, ``rango (3)`` en realidad no crea la lista
``[0, 1, 2]``. Devuelve un objeto que actúa igual que la lista ``[0, 1, 2]``, cuando se usa en un bucle for.
La diferencia es que los números 0, 1 y 2 se producen cuando se necesitan en lugar de todos creados de antemano.
Esto apenas importa cuando hay Solo tres artículos. Para ``rango (10000000)``, hace una pequeña diferencia en la velocidad
de ejecución del programa y la cantidad de memoria se utiliza es por eso que los artículos se producen según sea necesario
en lugar de todos producidos por adelantado.

Para los propósitos de este libro, sin embargo, la diferencia no importa. Podrá pensar en la función de rango como
si devuelve un objeto de lista. De hecho, el intérprete de Python que está integrado en el libro de texto engaña un poco y
hace la función de rango en realidad produce una lista. Cuando ejecuta un intérprete de Python nativo en su computadora,
no engañará de esa manera. Aún así, cuando ejecutas el código de la forma, ``para x en el rango (y)`` harás bien en pensar
en el rango (y) que regresa una lista.

No se preocupe por comprender estos detalles ahora mismo. El punto importante es que en la ventana de código activo anterior,
en lugar de ``some_seq`` puede tener cualquier expresión de Python que se evalúe como una cadena, una lista u otro objeto de Python
determinada objetos que actúan como secuencias con el propósito de usar en bucles for. Es algo a tener en cuenta para más
adelante, cuando vemos algunos de esos otros objetos de Python que actúan como secuencias pero no del todo.

.. todo:  Add some questions to check understanding of the type of the loop variable given an iteration over a -- string, a list, a range