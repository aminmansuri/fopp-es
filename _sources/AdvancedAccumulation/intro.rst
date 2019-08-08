..  Copyright (C)  Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".


.. qnum::
   :prefix: AdAccum-1-
   :start: 1

.. _list_comp_chap:

Introducción: Map, Filter, List Comprehensions y Zip
====================================================

Revisemos el :ref:`accumulator pattern <accum_pattern>`. Con frecuencia tomamos una lista y producimos otra lista
a partir de ella que contiene un subconjunto de los elementos o una versión transformada de cada elemento. Cuando cada elemento se transforma, nosotros
decimos que la operación es un **mapping** *mapeo*, o **map** *mapa* de la lista original. Cuando se omiten algunos elementos, lo llamamos **filter** *filtrar*.

Python proporciona funciones integradas ``map`` y ``filter``. Python también proporciona una nueva sintaxis, llamada
**list comprehensions**, que le permite expresar una operación de mapeo y/o filtrado. Al igual que con las funciones con nombre y
expresiones lambda, a algunos estudiantes les parece más fácil pensar en términos de las funciones de map y filter, mientras que otros
estudiantes les resulta más fácil leer y escribir list comprehensions. Aprenderás ambas formas; uno puede incluso ayudarte a entender
el otro. La mayoría de los programadores de Python usan list comprehensions, así que asegúrese de aprender a leerlas. En este curso, puedes
elegir aprender a escribir list comprehensions o usar map y filter, lo que prefieras  pero deberías aprender a leer ambos
list comprehensions y map/filter.

Otros patrones de acumuladores comunes en las listas agregan todos los valores en un solo valor.

Map y filter son comandos que usaría en la informática de alto rendimiento en grandes conjuntos de datos.
Consulte `MapReduce en Wikipedia <http://en.wikipedia.org/wiki/MapReduce>`_.
