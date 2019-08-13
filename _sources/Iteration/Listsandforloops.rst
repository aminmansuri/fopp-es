..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: iter-5-
   :start: 1

Listas y bucles ``for``
=======================

También es posible realizar **recorrer una lista** usando la iteración por elemento. Una lista es una secuencia de elementos, por lo que el ciclo ``for`` itera sobre cada elemento de la lista automáticamente.

.. activecode:: ac6_5_1

    fruits = ["apple", "orange", "banana", "cherry"]

    for afruit in fruits:     # by item
        print(afruit)

Casi se lee como lenguaje natural: para (cada) fruta en (la lista de) frutas,
imprimir (el nombre de la) fruta.

¿Recuerdas los dibujos de tortugas que hicimos antes? ¡Para bucles y listas se pueden aplicar allí también!

La iteración simplifica nuestro programa en Turtle
---------------------------------------------------

Para dibujar un cuadrado, nos gustaría hacer lo mismo cuatro veces: mover la tortuga hacia adelante
distancia y girar 90 grados. Anteriormente utilizamos 8 líneas de código Python para que alex dibujara los cuatro
lados de un cuadrado. El siguiente programa hace exactamente lo mismo pero, con la ayuda de un bucle for,
usa solo tres líneas (sin incluir el código de configuración). Recuerde que la declaración for
repetirá `adelante` e `izquierda` cuatro veces, una vez para cada valor en la lista.

.. activecode:: ac6_5_2
   :nocodelens:

   import turtle            # preparar a alex
   wn = turtle.Screen()
   alex = turtle.Turtle()

   for i in [0, 1, 2, 3]:      # repetir cuatro veces
       alex.forward(50)
       alex.left(90)

   wn.exitonclick()



Si bien "guardar algunas líneas de código" podría ser conveniente, no es la gran cosa aquí.
Lo que es mucho más importante es que hemos encontrado un "patrón repetitivo" de declaraciones,
y reorganizamos nuestro programa para repetir el patrón.

Los valores [0,1,2,3] se proporcionaron para hacer que el cuerpo del bucle se ejecute 4 veces.
Podríamos haber usado cuatro valores cualquiera. Por ejemplo, considere el siguiente programa.


.. activecode:: ac6_5_3
   :nocodelens:

   import turtle            # preparar a alex
   wn = turtle.Screen()
   alex = turtle.Turtle()

   for aColor in ["yellow", "red", "purple", "blue"]:      # repetir cuatro veces
       alex.forward(50)
       alex.left(90)

   wn.exitonclick()

En el ejemplo anterior, había cuatro enteros en la lista. Esta vez hay cuatro Strings.
Como hay cuatro elementos en la lista, la iteración seguirá ocurriendo cuatro veces.
``aColor`` va a tomar cada color en la lista. Incluso podemos ir un paso más allá y usar el valor de
``aColor`` como parte del cálculo.

.. activecode:: ac6_5_4
    :nocodelens:

    import turtle            # preparar a alex
    wn = turtle.Screen()
    alex = turtle.Turtle()

    for aColor in ["yellow", "red", "purple", "blue"]:
        alex.color(aColor)
        alex.forward(50)
        alex.left(90)

    wn.exitonclick()

En este caso, el valor de ``aColor`` se usa para cambiar el atributo de color de ``alex``. Cada
la iteración hace que ``aColor`` cambie al siguiente valor en la lista.

El ciclo for es nuestro primer ejemplo de una **declaración compuesta**. Sintácticamente una declaración compuesta
Es una declaración. El nivel de tabulación de una declaración compuesta (completa) es la sangría de su título.
En el ejemplo anterior hay cinco declaraciones con la misma sangría, ejecutadas secuencialmente: la importación,
2 tareas, el *for* loop completo y ``wn.exitonclick()``. los la declaración compuesta for-loop se ejecuta
completamente antes de pasar a la siguiente secuencial declaración, ``wn.exitonclick()``.

**Revisa tu entendimiento**

.. mchoice:: question6_5_1
   :answer_a: 8
   :answer_b: 9
   :answer_c: 15
   :answer_d: Error, la sentencia for necesita usar la función range.
   :correct: b
   :feedback_a: La iteración por elemento se procesará una vez para cada elemento de la secuencia, incluso la lista vacía.
   :feedback_b: Sí, hay nueve elementos en la lista, por lo que el bucle for iterará nueve veces.
   :feedback_c: La iteración por elemento se procesará una vez para cada elemento de la secuencia. Cada cadena se ve como un solo elemento, incluso si puede iterar sobre una cadena.
   :feedback_d: La instrucción for puede iterar sobre una secuencia elemento por elemento.
   :practice: T

   ¿Cuántas veces iterará el ciclo for en las siguientes afirmaciones?
   
   .. code-block:: python

      p = [3, 4, "Me", 3, [], "Why", 0, "Tell", 9.3]
      for ch in p:
         print(ch)

.. mchoice:: question6_5_2
   :answer_a: Están sangrados en el mismo grado desde el encabezado del bucle.
   :answer_b: Siempre hay exactamente una línea en el cuerpo del bucle.
   :answer_c: El cuerpo del bucle termina con un punto y coma (;) que no se muestra en el código anterior.
   :correct: a
   :feedback_a: El cuerpo del bucle puede tener cualquier número de líneas, todas sangradas desde el encabezado del bucle.
   :feedback_b: El cuerpo del bucle puede tener más de una línea.
   :feedback_c: Python no necesita punto y coma en su sintaxis, se basa principalmente en la sangría.

   ¿Cómo sabe Python qué declaraciones están contenidas en el cuerpo del bucle?

.. mchoice:: question6_5_3
      :answer_a: Dibuja un cuadrado usando el mismo color para cada lado.
      :answer_b: Dibuja un cuadrado usando diferentes colores para cada lado.
      :answer_c: Dibuja un lado de un cuadrado.
      :correct: c
      :feedback_a: La pregunta no es pedirle que describa el resultado del ciclo completo, la pregunta es preguntarle sobre el resultado de una **iteración única** del ciclo.
      :feedback_b: Tenga en cuenta que aColor nunca se usa realmente dentro del bucle.
      :feedback_c: El cuerpo del bucle solo dibuja un lado del cuadrado. Se repetirá una vez para cada elemento de la lista. Sin embargo, el color de la tortuga nunca cambia.

      Considera el siguiente code:

      .. code-block:: python

        for aColor in ["yellow", "red", "green", "blue"]:
           alex.forward(50)
           alex.left(90)

      ¿Qué hace cada iteración a través del bucle?
