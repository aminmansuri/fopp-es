..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: moreiter-4-
   :start: 1

.. _randomly-walking-turtles:

Tortugas deambulando aleatoriamente
---------------------------------------

Supongamos que queremos entretenernos viendo a una tortuga deambular aleatoriamente dentro de la pantalla.
Cuando ejecutamos el programa, queremos que la tortuga y el programa se comporten de la siguiente manera:

#. La tortuga comienza en el centro de la pantalla.
#. Lanza una moneda. Si se trata de cara, gire a la izquierda 90 grados. Si es cruz
   luego gire a la derecha 90 grados.
#. Da 50 pasos hacia adelante.
#. Si la tortuga se ha movido fuera de la pantalla, deténgase, de lo contrario regrese a
   paso 2 y repita.

Tenga en cuenta que no podemos predecir cuántas veces la tortuga necesitará voltear la
moneda antes de que salga de la pantalla, por lo que no podemos usar un bucle for en este
caso. De hecho, aunque es muy poco probable, este programa podría nunca terminar,
por eso llamamos a esta iteración indefinida.

Entonces, según la descripción del problema anterior, podemos describir un programa de la siguiente manera:

.. sourcecode:: python

    create a window and a turtle

    while the turtle is still in the window:
        generate a random number between 0 and 1
        if the number == 0 (heads):
            turn left
        else:
            turn right
        move the turtle forward 50

Ahora, probablemente lo único que te parece un poco confuso es la parte sobre si
la tortuga todavía está en la pantalla. Pero esto es lo bueno de la programación, podemos
retrasar las cosas difíciles y obtener *alg* en nuestro programa trabajando de inmediato. Tal como solemos
hacer esto, es delegar el trabajo de decidir si la tortuga todavía está en la pantalla
o no a una función boolean. Llamemos a esta función boolean  ``isInScreen``. Podemos escribir una
versión simple de esta función boolean al hacer que siempre devuelva ``True``, o al tenerla y
decidir al azar. El punto es hacer que haga algo simple para que podamos centrarnos en las demás partes.
Ya sabemos cómo hacerlo bien y hacer que funcionen. Ya que tenerlo siempre devuelve True no lo haría
una buena idea, escribiremos nuestra versión para decidir al azar. Digamos que hay un 90% de posibilidades de que la
tortuga todavía está en la ventana y el 10% de la tortuga se ha escapado.

.. activecode:: ac14_4_1
    :nocodelens:

    import random
    import turtle


    def isInScreen(w, t):
        if random.random() > 0.1:
            return True
        else:
            return False


    t = turtle.Turtle()
    wn = turtle.Screen()

    t.shape('turtle')
    while isInScreen(wn, t):
        coin = random.randrange(0, 2)
        if coin == 0:              # cara
            t.left(90)
        else:                      # cruz
            t.right(90)

        t.forward(50)

    wn.exitonclick()


Ahora tenemos un programa de trabajo que dibuja una caminata aleatoria de nuestra tortuga que tiene un 90% de posibilidades de
permanecer en la pantalla. Estamos en una buena posición, porque gran parte de nuestro programa está funcionando
y podemos centrarnos en el próximo trabajo: decidir si la tortuga está dentro de la pantalla
límite o no.

Podemos encontrar el ancho y el alto de la pantalla usando el ``window_width`` y
``window_height`` del objeto de pantalla. Sin embargo, recuerde que la tortuga comienza en la
posición 0,0 en el medio de la pantalla. Así que nunca queremos que la tortuga vaya más lejos que
ancho /2 o más a la izquierda que el ancho negativo /2. Nunca queremos que la tortuga suba más que
altura /2 o más abajo que la altura negativa /2. Una vez que sepamos cuáles son los límites, podemos usar
algunos condicionales para verificar la posición de la tortuga contra los límites y devolver ``False`` si
la tortuga está afuera o ``True`` si la tortuga está adentro.

Una vez que hemos calculado nuestros límites, podemos obtener la posición actual de la
tortuga y luego usar condicionales para decidir. Aquí hay una implementación:

.. sourcecode:: python

    def isInScreen(wn,t):
        leftBound = -(wn.window_width() / 2)
        rightBound = wn.window_width() / 2
        topBound = wn.window_height() / 2
        bottomBound = -(wn.window_height() / 2)

        turtleX = t.xcor()
        turtleY = t.ycor()

        stillIn = True
        if turtleX > rightBound or turtleX < leftBound:
            stillIn = False
        if turtleY > topBound or turtleY < bottomBound:
            stillIn = False

        return stillIn

Hay muchas formas en que se puede escribir el condicional. En este caso hemos dado
``stillIn`` el valor predeterminado de ``True`` y use dos declaraciones ``if`` para establecer posiblemente
el valor a ``False``. Puede reescribir esto para usar condicionales anidados o ``elif``
y establezca ``stillIn`` en ``True`` en una cláusula else.

Aquí está la versión completa de nuestro programa de caminata aleatoria.

.. activecode:: ac14_4_2
    :nocodelens:

    import random
    import turtle

    def isInScreen(w,t):
        leftBound = - w.window_width() / 2
        rightBound = w.window_width() / 2
        topBound = w.window_height() / 2
        bottomBound = -w.window_height() / 2

        turtleX = t.xcor()
        turtleY = t.ycor()

        stillIn = True
        if turtleX > rightBound or turtleX < leftBound:
            stillIn = False
        if turtleY > topBound or turtleY < bottomBound:
            stillIn = False

        return stillIn

    t = turtle.Turtle()
    wn = turtle.Screen()

    t.shape('turtle')
    while isInScreen(wn,t):
        coin = random.randrange(0, 2)
        if coin == 0:
            t.left(90)
        else:
            t.right(90)

        t.forward(50)

    wn.exitonclick()

Podríamos haber escrito este programa sin usar una función boolean. Tu podrías querer que
intente reescribirlo utilizando una condición compleja en la instrucción while. Sin embargo, usando un boolean
la función hace que el programa sea mucho más legible y fácil de entender. También nos da
otra herramienta para usar si este era un programa más grande y necesitábamos verificar si
la tortuga todavía estaba en la pantalla en otra parte del programa. Otra ventaja es que
si alguna vez necesita escribir un programa similar, puede reutilizar esta función con confianza
la próxima vez que lo necesites. Romper este programa en un par de partes es otro ejemplo de
descomposición funcional.

.. index:: 3n + 1 sequence

**Revisa tu entendimiento**

.. mchoice:: question14_4_1
   :answer_a: Devuelve Verdadero si la tortuga todavía está en la pantalla y Falso si ya no está en la pantalla.
   :answer_b: Utiliza un ciclo while para mover la tortuga al azar hasta que salga de la pantalla.
   :answer_c: Gira la tortuga hacia la derecha o hacia la izquierda al azar y la mueve hacia adelante 50.
   :answer_d: Calcula y devuelve la posición de la tortuga en la ventana.
   :correct: a
   :feedback_a: La función isInScreen calcula la prueba booleana de si la tortuga todavía está en la ventana. Simplifica la condición del bucle while en la parte principal del código.
   :feedback_b: La función isInScreen no contiene un ciclo while. Ese bucle está fuera de la función isInScreen.
   :feedback_c: La función isInScreen no mueve la tortuga.
   :feedback_d: Si bien la función isInScreen utiliza el tamaño de la ventana y la posición de la tortuga, no devuelve la posición de la tortuga.

   En el programa de caminata aleatoria en esta sección, ¿qué hace la función isInScreen?
