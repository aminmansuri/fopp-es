..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: condition-1-
   :start: 1

Introducción: lo que podemos hacer con Turtles y Condicionales
==============================================================

Hasta ahora, nuestros programas han sido una serie de declaraciones que siempre se ejecutan secuencialmente u operaciones que se aplican a cada elemento en un iterable. Sin embargo, los programas con frecuencia deben ser más sutiles con su comportamiento. Por ejemplo, una aplicación de mensajería solo puede establecer el título de un mensaje en negrita si el usuario no lo ha leído. O un videojuego necesita actualizar la posición de todos los personajes que no están dormidos. Esto se hace con algo llamado **selección** o **declaración condicional**.

En el contexto de los dibujos turtle, el uso de este tipo de declaración nos permitirá verificar las condiciones y cambiar el comportamiento del programa en consecuencia

.. activecode:: ac7_1_1

    import turtle
    wn = turtle.Screen()

    amy = turtle.Turtle()
    amy.pencolor("Pink")
    amy.forward(50)
    if amy.pencolor() == "Pink":
        amy.right(60)
        amy.forward(100)
    else:
        amy.left(60)
        amy.forward(100)
        
    kenji = turtle.Turtle()
    kenji.forward(60)
    if kenji.pencolor() == "Pink":
        kenji.right(60)
        kenji.forward(100)
    else:
        kenji.left(60)
        kenji.forward(100)

En el código anterior, primero configuramos el color de la pluma de Amy para que sea "Pink" y luego la movemos hacia adelante. A continuación queremos uno
para que ocurran dos acciones, o bien Amy debe moverse hacia la derecha y luego hacia adelante, o hacia la izquierda y luego hacia adelante. La dirección
que queramos que vaya depende del color de su pluma. Si el color de su bolígrafo está configurado en rosa, que está determinado por
escribir ``amy.pencolor() == "Pink"`` que comprueba si el valor devuelto por ``amy.pencolor()`` es el
equivalente a la cadena "Pink", entonces deberíamos hacer que se mueva hacia la derecha y hacia adelante. De lo contrario (o de otro modo) ella
debe moverse hacia la izquierda y hacia adelante. Sin embargo, ambas cosas no pueden suceder. Ella no puede moverse a la derecha, adelante *e* izquierda,
adelante. Luego hacemos lo mismo para kenji, aunque en este caso, no cambiamos el color de la pluma de kenji.

Puede parecer un poco extraño agregar los condicionales en este ejemplo. ¿No sabríamos ya que creamos Amy?
y los colores de kenji, entonces, ¿por qué necesitaríamos un condicional? Si bien es cierto que este no es el *mejor* lugar para que
use un condicional, ¡podemos combinar enunciados condicionales con bucles for para hacer algo genial!

.. activecode:: ac7_1_2

    import turtle
    wn = turtle.Screen()

    amy = turtle.Turtle()
    amy.pencolor("Pink")
    amy.right(170)

    colors = ["Purple", "Yellow", "Orange", "Pink", "Orange", "Yellow", "Purple", "Orange", "Pink", "Pink", "Orange", "Yellow", "Purple", "Orange", "Purple", "Yellow", "Orange", "Pink", "Orange", "Purple", "Purple", "Yellow", "Orange", "Pink", "Orange", "Yellow", "Purple", "Yellow"]


    for color in colors:
        if amy.pencolor() == "Purple":
            amy.forward(50)
            amy.right(59)
        elif amy.pencolor() == "Yellow":
            amy.forward(65)
            amy.left(98)
        elif amy.pencolor() == "Orange":
            amy.forward(30)
            amy.left(60)
        elif amy.pencolor() == "Pink":
            amy.forward(50)
            amy.right(57)

        amy.pencolor(color)

El ejemplo anterior combina un bucle for con un conjunto de declaraciones condicionales. Aquí, recorremos una lista de
colores y cada iteración comprueba para ver cuál es el color del lápiz de Amy. Dependiendo del color de la pluma, turtle
debe moverse en cierta dirección, por una cierta distancia. Antes de que el ciclo for se repita, el color de la pluma de Amy cambia
a cualquier ``color`` que esté en el bucle for y continúe. Tenga en cuenta que el color no cambia hasta el final,
para que podamos comenzar a usar cualquier color que Amy esté configurado inicialmente. Esto significa que el último color en la lista
no usará los ``colors``, aunque puede ver cómo el icono cambia al color apropiado.

Este capítulo tratará más detalladamente cómo usar declaraciones condicionales.

Metas de aprendizaje
--------------------

* Entender expresiones boolean y operadores lógicos.
* Para entender la ejecución condicional
* Para poder escribir una función boolean
* Saber cuándo usar declaraciones condicionales binarias, unarias, encadenadas y anidadas


Objetivos
----------

* Para evaluar adecuadamente una expresión boolean (compuesta)
* Usar paréntesis para demostrar adecuadamente la precedencia del operador
* Para usar declaraciones condicionales para bifurcar correctamente el código


