..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. _mutability:

.. qnum::
   :prefix: seqmut-1-
   :start: 1

.. index:: mutable, immutable
   runtime error; string item assignment
   string; immutable

Mutabilidad
============

Algunos tipos de colección de Python -cadenas y listas hasta ahora- pueden cambiar y otros no. Si
un tipo puede cambiar, se dice que es mutable. Si el tipo no puede cambiar, entonces
se dice que es inmutable. Esto se ampliará a continuación.

Las Listas son Mutables
------------------------

A diferencia de las cadenas, las listas son **mutables**. Esto significa que podemos cambiar un elemento en una lista accediendo
directamente como parte de la declaración de asignación. Usando el operador de indexación (corchetes) en
En el lado izquierdo de una tarea, podemos actualizar uno de los elementos de la lista.

.. activecode:: ac8_1_4

    fruit = ["banana", "apple", "cherry"]
    print(fruit)

    fruit[0] = "pear"
    fruit[-1] = "orange"
    print(fruit)


Una asignación a un elemento de una lista se llama **asignación de elemento**. La asignación de elementos no funciona
para Strings Recordemos que los Strings son inmutables.

Aquí está el mismo ejemplo en codelens para que pueda recorrer las declaraciones y ver los
cambios en los elementos de la lista.

.. codelens:: clens8_1_1
    :python: py3

    fruit = ["banana", "apple", "cherry"]

    fruit[0] = "pear"
    fruit[-1] = "orange"

Al combinar la asignación con el operador slice podemos actualizar varios elementos a la vez.

.. activecode:: ac8_1_5

    alist = ['a', 'b', 'c', 'd', 'e', 'f']
    alist[1:3] = ['x', 'y']
    print(alist)

También podemos eliminar elementos de una lista asignándoles la lista vacía.

.. activecode:: ac8_1_6

    alist = ['a', 'b', 'c', 'd', 'e', 'f']
    alist[1:3] = []
    print(alist)

Incluso podemos insertar elementos en una lista comprimiéndolos en un segmento vacío en la
ubicación deseada.

.. activecode:: ac8_1_7

    alist = ['a', 'd', 'f']
    alist[1:1] = ['b', 'c']
    print(alist)
    alist[4:4] = ['e']
    print(alist)

Los Strings son Immutables
---------------------------

Una última cosa que hace que los Strings sean diferentes de otros tipos de colección de Python es que
no puede modificar los caracteres individuales de la colección. Es tentador usar
el operador ``[]`` en el lado izquierdo de una asignación, con la intención de cambiar un caracter
en un String, por ejemplo en el siguiente código, nos gustaría cambiar la primera letra de ``saludo``.

.. activecode:: ac8_1_1
    
    greeting = "Hello, world!"
    greeting[0] = 'J'            # ERROR!
    print(greeting)

En lugar de producir la salida ``¡Jello, mundo!``, Este código produce el error de tiempo de ejecución
``TypeError: 'str' el objeto no admite la asignación de elementos``.

Las Sttrings son **inmutables**, lo que significa que no puede cambiar una cadena existente.
Lo mejor que puede hacer es crear una nueva cadena que sea una variación de la original.

.. activecode:: ac8_1_2
    
    greeting = "Hello, world!"
    newGreeting = 'J' + greeting[1:]
    print(newGreeting)
    print(greeting)          # same as it was

La solución aquí es concatenar una nueva primera letra a un slice de ``greeting``.
Esta operación no tiene efecto en la cadena original.

Si bien es posible inventar nuevos nombres de variables cada vez que hacemos cambios a los existentes
valores, podría ser difícil hacer un seguimiento de todos ellos.

.. activecode:: ac8_1_3

    phrase = "many moons"
    phrase_expanded = phrase + " and many stars"
    phrase_larger = phrase_expanded + " litter"
    phrase_complete = "M" + phrase_larger[1:] + " the night sky."
    excited_phrase_complete = phrase_complete[:-1] + "!"

Cuanto más cambie la cadena, más difícil será crear una nueva variable para usar. Es perfectamente aceptable reasignar el valor al mismo nombre de variable en este caso.

Las Tuplas son Immutables
--------------------------

Al igual que con los Strings, si intentamos usar la asignación de elementos para modificar uno de los elementos de una tupla, obtenemos un error. De hecho, esa es la diferencia clave entre listas y tuplas: las tuplas son como listas inmutables. Ninguna de las operaciones en las listas que las mutan están disponibles para las tuplas. Una vez que se crea una tupla, no se puede cambiar.

.. sourcecode:: python

    julia[0] = 'X'  # TypeError: 'tuple' object does not support item assignment




**Revisa tu entendimiento**

.. mchoice:: question8_1_1
   :answer_a: [4,2,True,8,6,5]
   :answer_b: [4,2,True,6,5]
   :answer_c: Error, es una asignación incorrecta
   :correct: b
   :feedback_a: La asignación de elementos no inserta el nuevo elemento en la lista.
   :feedback_b: Sí, el valor True se coloca en la lista en el índice 2. Reemplaza 8.
   :feedback_c: La asignación de artículos está permitida con listas. Las listas son mutables.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?
   
   .. code-block:: python

     alist = [4,2,8,6,5]
     alist[2] = True
     print(alist)

.. mchoice:: question8_1_2
   :answer_a: Ball
   :answer_b: Call
   :answer_c: Error
   :correct: c
   :feedback_a: La asignación no está permitida con Strings.
   :feedback_b: La asignación no está permitida con Strings.
   :feedback_c: Sí, los Strings son inmutables.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?
   
   .. code-block:: python

      s = "Ball"
      s[0] = "C"
      print(s)

