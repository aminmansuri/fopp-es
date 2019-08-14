..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: sequences-2-
   :start: 1

Strings y Listas
=================

A lo largo de los primeros capítulos de este libro, hemos utilizado cadenas para representar palabras o frases que
queriamos imprimir. Nuestra definición era simple: un string es simplemente algunos caracteres entre comillas.
En este capítulo exploramos los strings *cadenas de caracteres* con mucho más detalle.

Además, exploraremos las listas, que son muy parecidas a strings pero que pueden contener diferentes tiposde datos.

Strings
-------

Los strings se pueden definir como colecciones secuenciales de caracteres. Esto significa que los caracteres
individuales que forman un sting están en un orden particular de izquierda a derecha.

Un string que no contiene caracteres, a menudo denominada **string vacío**, todavía se considera
ser un string. Es simplemente una secuencia de cero caracteres y está representado por '' or "" (dos comillas simples
o dos comillas dobles sin nada en el medio).

Lists
-----

Una **list** es una colección secuencial de valores de datos de Python, donde cada valor se identifica mediante un
índice. Los valores que forman una lista se llaman sus **elementos**. Las listas son similares a las cadenas, que
son colecciones ordenadas de caracteres, excepto que los elementos de una lista pueden tener cualquier tipo y para
cualquier lista, los artículos pueden ser de diferentes tipos.

Hay varias formas de crear una nueva lista. Lo más simple es encerrar el
elementos entre corchetes ( ``[`` y ``]``)..

.. sourcecode:: python
    
    [10, 20, 30, 40]
    ["spam", "bungee", "swallow"]

El primer ejemplo es una lista de cuatro enteros. El segundo es una lista de tres
instrumentos de cuerda. Como dijimos anteriormente, los elementos de una lista no tienen que ser del mismo tipo. El seguimiento
La lista contiene una cadena, un flotador, un entero y
otra lista

.. sourcecode:: python
    
    ["hello", 2.0, 5, [10, 20]]


.. note:: WP: ¡No mezcles tipos!

    Es probable que nos veas hacer esto en el libro de texto para darte combinaciones extrañas, pero cuando creas listas
    en general, no debe mezclar tipos juntos. Una lista de cadenas simples o enteros o flotantes es generalmente
    más fácil de tratar.

Tuples
------

Un **tuple**, es como una lista, es una secuencia de elementos de cualquier tipo. La representación impresa de una tupla es una coma que separa
secuencia de valores, entre paréntesis. En otras palabras, la representación es como listas, excepto con
paréntesis () en lugar de corchetes [].

Una forma de crear una tupla es escribir una expresión, entre paréntesis,
que consiste en varias otras expresiones, separadas por comas.

.. sourcecode:: python

    julia = ("Julia", "Roberts", 1967, "Duplicity", 2009, "Actress", "Atlanta, Georgia")

La diferencia clave entre listas y tuplas es que una tupla es inmutable, lo que significa que su contenido no se puede cambiar después de que la tupla es
creada. Examinaremos la mutabilidad de las listas en detalle en el capítulo sobre:ref:`Mutabilidad <mutabilidad>`.

Para crear una tupla con un solo elemento (pero es probable que no lo hagas con demasiada frecuencia), tenemos que incluir la
coma final, porque sin la coma final, Python trata el ``(5)`` a continuación como un número entero entre paréntesis:

.. activecode:: ac5_2_1

    t = (5,)
    print(type(t))

    x = (5)
    print(type(x))


**Revisa tu entendimiento**

.. mchoice:: question5_2_1 
   :answer_a: Falso
   :answer_b: Verdadero
   :correct: a
   :feedback_a: Sí, a diferencia de los strings, las listas pueden consistir en cualquier tipo de datos en Python.
   :feedback_b: Las listas son heterogéneas, lo que significa que pueden tener diferentes tipos de datos.
   :practice: T

   Una lista solo puede contener elementos enteros.
