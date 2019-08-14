..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: condition-4-
   :start: 1

Los operadores ``in`` y ``not in``
-----------------------------------

El operador ``in`` prueba si una cadena es una subcadena de otra:

.. activecode:: ac4_3_1
    
    print('p' in 'apple')
    print('i' in 'apple')
    print('ap' in 'apple')
    print('pa' in 'apple')

Tenga en cuenta que un string es un substring de sí mismo, y el string vacío es un
substring de cualquier otro string. (También tenga en cuenta que a los informáticos
nos gusta pensar en estos casos extremos con mucho cuidado)

.. activecode:: ac4_3_2
    
    print('a' in 'a')
    print('apple' in 'apple')
    print('' in 'a')
    print('' in 'apple')
    
El operador ``not in`` devuelve el resultado lógico opuesto de ``in``.

.. activecode:: ac4_3_3

    print('x' not in 'apple')

¡También podemos usar los operadores ``in`` y ``not in`` en las listas!

.. activecode:: ac4_4_4

   print("a" in ["a", "b", "c", "d"])
   print(9 in [3, 2, 9, 10, 9.0])
   print('wow' not in ['gee wiz', 'gosh golly', 'wow', 'amazing'])

Sin embargo, ¿recuerda cómo pudo comprobar si una "a" estaba en "manzana"?
Intentemos eso nuevamente para ver si hay una "a" en algún lugar de la siguiente lista.

.. activecode:: ac4_4_5

    print("a" in ["apple", "absolutely", "application", "nope"])

Claramente, podemos decir que a está en la palabra manzana, y absolutamente, y aplicación. Por alguna razón,
sin embargo, el intérprete de Python devuelve False. ¿Porqué es eso? Cuando usamos ``in`` y ``not in``
operadores en listas, Python verifica si el elemento en el lado izquierdo de la expresión es equivalente
a un elemento en el elemento en el lado derecho de la expresión. En este caso, Python está comprobando
si un elemento de la lista es o no la cadena "a", nada más ni menos que eso.
