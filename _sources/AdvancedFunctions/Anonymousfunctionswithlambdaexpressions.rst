..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: advfuncs-3-
   :start: 1

Funciones anónimas con expresiones lambda
------------------------------------------

Para dejar bien clara la idea de que estamos pasando un objeto de función como parámetro al objeto ordenado,
veamos una notación alternativa para crear una función, una **expresión lambda**. La sintaxis de una expresión
lambda es la palabra "lambda" seguida de nombres de parámetros, separados por comas pero no adentro (paréntesis),
seguido de dos puntos y luego una expresión. ``argumentos lambda: expresión`` produce un objeto de función. Este
objeto sin nombre se comporta igual que el objeto de función construido a continuación.

.. sourcecode:: python

    def fname(arguments):
        return expression
        
.. image:: Figures/lambda.gif
   :alt: image showing how elements of a lambda expression are like a function definition.

Considere el siguiente código

.. activecode:: ac15_3_1

    def f(x):
        return x - 1
    
    print(f)
    print(type(f))
    print(f(3))
    
    print(lambda x: x-2)
    print(type(lambda x: x-2))
    print((lambda x: x-2)(6))
    
Tenga en cuenta las paralelas entre los dos. En la línea 4, f está vinculada a un objeto de función. Su representación impresa
es "<función f>". En la línea 8, la expresión lambda produce un objeto de función. Como no tiene nombre (anónimo),
su representación impresa no incluye un nombre para ella, "<function <lambda>>". Ambos son de tipo 'función'.

Se puede llamar a una función, ya sea nombrada o anónima, colocando paréntesis () después de ella.
En este caso, debido a que hay un parámetro, hay un valor entre paréntesis. Esta
funciona de la misma manera para la función nombrada y la función anónima producida por lambda
expresión. La expresión lambda tenía que ir entre paréntesis solo para los fines
de agrupar todos sus contenidos juntos. Sin los paréntesis adicionales a su alrededor en la línea 10,
el intérprete agruparía las cosas de manera diferente y haría una función de x que devuelva x - 2(6).

Algunos estudiantes encuentran más natural trabajar con expresiones lambda que referirse a una función
por nombre. Otros encuentran confusa la sintaxis de las expresiones lambda. Depende de usted qué versión desea
use aunque necesitará poder leer y comprender expresiones lambda escritas por otros.
En todos los ejemplos a continuación, se ilustrarán ambas formas de hacerlo.

Digamos que queremos crear una función que tome una cadena y devuelva el último carácter en esa cadena. ¿Qué podría parecer esto?
como con las funciones que has usado antes?

.. activecode:: ac15_3_2

    def last_char(s):
        return s[-1]

Para volver a escribir esto usando la notación lambda, podemos hacer lo siguiente:

.. activecode:: ac15_3_3

    last_char = (lambda s: s[-1])

Tenga en cuenta que ninguna función se invoca realmente. Mira los paralelos entre las dos estructuras. Los parámetros son
definido en ambas funciones con la variable ``s``. En la función típica, tenemos que usar la palabra clave ``return`` retornar
el valor. En una función lambda, eso no es necesario: lo que se coloca después de los dos puntos es lo que se devolverá.

**Revisa tu entendimiento**

.. mchoice:: question15_3_1
   :answer_a: Una cadena con un - delante del número.
   :answer_b: Un número del signo opuesto (el número positivo se vuelve negativo, el negativo se vuelve positivo).
   :answer_c: No se devuelve nada porque no hay una declaración de devolución.
   :correct: b
   :feedback_a: El número se asignaría a la variable x y aquí no se utiliza ninguna conversión de tipo, por lo que el número se mantendría como un número.
   :feedback_b: ¡Correcto!
   :feedback_c: Recuerde, las funciones lambda no usan declaraciones de retorno.
   :practice: T

   Si la entrada a esta función lambda es un número, ¿qué se devuelve?
   
   .. code-block:: python 
     
    (lambda x: -x)
