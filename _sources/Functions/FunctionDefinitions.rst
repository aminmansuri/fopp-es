..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: func-1-
   :start: 1

Definición de función
------------------------

La sintaxis para crear una función con nombre, una **definición de función**, es:

.. code-block:: python

    def name( parameters ):
        statements

Puede inventar los nombres que desee para las funciones que cree, excepto que no puede usar un nombre que sea Python
palabra clave, y los nombres deben seguir las reglas para los identificadores legales que se dieron anteriormente. Los parámetros especifican
qué información, si hay alguna, tiene que proporcionar para usar la nueva función. Otra forma de decir esto es que el
Los parámetros especifican qué necesita la función para hacer su trabajo.

Puede haber cualquier número de declaraciones dentro de la función, pero tienen que estar sangradas de ``def``. En el
ejemplos en este libro, usaremos la sangría estándar de cuatro espacios. Las definiciones de funciones son el tercero de
veremos varias **declaraciones compuestas**, todas las cuales tienen el mismo patrón:

#. Una línea de encabezado que comienza con una palabra clave y termina con dos puntos.
#. Un **cuerpo** que consiste en una o más declaraciones de Python, cada
   sangrado con la misma cantidad -- *4 espacios es el estándar de Python* -- desde
   la línea de encabezado.

Ya hemos visto la declaración ``for`` que tiene la misma estructura, con un bloque de código sangrado, y las
declaraciones ``if``, ``elif`` y ``else`` que también lo hacen.

En una definición de función, la palabra clave en el encabezado es ``def``, que es seguida por el nombre de la función y
algunos *nombres de parámetros* entre paréntesis. La lista de parámetros puede estar vacía o puede contener cualquier número de
parámetros separados entre sí por comas. En cualquier caso, los paréntesis son obligatorios.

Volveremos a los parámetros en un momento, pero primero veamos qué sucede cuando se ejecuta una función,
usando una función sin ningún parámetro para ilustrar.

Aquí está la definición de una función simple, hello.

.. activecode:: ac11_1_1

    def hello():
        """This function says hello and greets you"""
        print("Hello")
        print("Glad to meet you")

.. admonition::  docstrings

    Si lo primero después del encabezado de la función es un string (algunas herramientas insisten en que
    debe ser un string entre comillas triples), se llama **docstring**
    y recibe un tratamiento especial en Python y en algunas de las herramientas de programación.

    Otra forma de recuperar esta información es utilizar el intérprete
    interactivo e ingrese la expresión ``<function_name>.__doc__``, que recuperará el
    docstring para la función. Entonces, el string que escribe como documentación al comienzo de una función es
    recuperable por python tools *en tiempo de ejecución*. Esto es diferente de los comentarios en su código,
    que se eliminan por completo cuando se analiza el programa.

    Por convención, los programadores de Python usan docstrings para la documentación clave de
    sus funciones

También podemos aplicar funciones a los dibujos turtle que hemos hecho en el pasado.

.. activecode:: ac11_1_2
    :nocodelens:

    import turtle

    def drawSquare(t, sz):
        """Make turtle t draw a square of with side sz."""

        for i in range(4):
            t.forward(sz)
            t.left(90)


    wn = turtle.Screen()      # Configurar la ventana y sus atributos.
    wn.bgcolor("lightgreen")

    alex = turtle.Turtle()    # crear alex
    drawSquare(alex, 50)      # llama a la función para dibujar el cuadrado que pasa turtle real y el tamaño del lado real

    wn.exitonclick()

Esta función se llama ``drawSquare``. Tiene dos parámetros: uno para indicarle a la función qué turtle debe moverse
y el otro para decirle el tamaño del cuadrado que queremos dibujar. En la definición de la función se llaman ``t`` y
``sz`` respectivamente. Asegúrese de saber dónde termina el cuerpo de la función --- depende de la sangría y
¡Las líneas en blanco no cuentan para este propósito!
