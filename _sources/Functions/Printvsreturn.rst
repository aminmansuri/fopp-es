..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: func-11-
   :start: 1

👩‍💻 Print vs. return
----------------------

Muchos programadores principiantes encuentran la distinción entre impresión y devolución muy confusa, especialmente porque la mayoría de
las ilustraciones de valores de retorno en textos introductorios como este muestran el valor devuelto de una llamada a función print
it, como en ``print(square(g(2)))``.

La declaración impresa es bastante fácil de entender. Toma un objeto python y genera una representación impresa del mismo
en la ventana de salida. Puede pensar en la declaración impresa como algo que toma un objeto de la tierra del
programa y lo hace visible a la tierra del observador humano.

.. note::

   **La impresión es solo para las personas**. Recuerda ese eslogan. La impresión no tiene ningún efecto en la ejecución en curso de un programa. No asigna un valor a una variable. No devuelve un valor de una llamada de función.

Si está confundido, es probable que la fuente de su confusión sea realmente acerca de los valores devueltos y la evaluación de
expresiones complejas. Una función que devuelve un valor está produciendo un valor para usar *por el programa*, en particular para
usar en la parte del código donde se invocó la función. Recuerde que cuando se invoca una función, la función
se ejecuta el bloque de código: todo ese código sangrado bajo la instrucción ``def`` se ejecuta, siguiendo las reglas de el
Lenguaje formal de Python para lo que debe y no debe ejecutarse a medida que avanza. Pero cuando la función regresa, el control se va
a volver a la ubicación de la llamada, y un valor de retorno puede volver con él.

Ya ha visto algunas llamadas a funciones en el Capítulo 1. Cuando te contamos sobre la función ``square`` que definimos,
viste que la expresión ``square(2)`` evalúa el valor entero ``4``.

Esto se debe a que la función ``square`` *devuelve* un valor: el cuadrado de cualquier entrada que se le pase.

Si un valor devuelto es para uso *por el programa*, ¿por qué hizo esa invocación de función para devolver un valor? Qué hacer si se
utiliza el resultado de la llamada a la función? Hay tres posibilidades

#. Guárdalo para después.
    El valor devuelto puede ser:

    * Asignado a una variable. Por ejemplo, ``w = cuadrado (3)``
    * Poner en una lista. Por ejemplo, ``L.append(cuadrado (3))``
    * Poner en un diccionario. Por ejemplo, ``d[3] = cuadrado (3)``

#. Úselo en una expresión más compleja.
    En ese caso, piense en el valor de retorno como
    reemplazando todo el texto de la invocación de la función. Por ejemplo, si hay una línea
    del código ``w = cuadrado (cuadrado (3) + 7) - 5``, piense en el valor de retorno 9 que reemplaza el
    texto cuadrado (3) en esa invocación, por lo que se convierte en ``square(9 + 7) -5``.

#. Imprimirlo para consumo humano.
    Por ejemplo, ``print(square(3))`` da salida a 9.
    Tenga en cuenta que, a menos que el valor de retorno se guarde primero como en la posibilidad 1, estará disponible
    solo a los humanos que miran el área de salida, no al programa mientras continúa ejecutándose.

Si su único propósito al ejecutar una función es hacer que una salida sea visible para el consumo humano, hay dos formas de
hacerlo. Puede poner una o más declaraciones de impresión dentro de la definición de la función y no molestarse en devolver nada de
la función (se devolverá el valor Ninguno). En ese caso, invoque la función sin una declaración de impresión. Por
ejemplo, puede tener una línea completa de código que lea ``f(3)``. Eso ejecutará la función f y tirará el
valor de retorno. Por supuesto, si el cuadrado no imprime nada o tiene efectos secundarios, es inútil llamarlo y hacer
nada con el valor de retorno. Pero con una función que tiene declaraciones de impresión dentro, puede ser bastante útil.

La otra posibilidad es devolver un valor de la función e imprimirlo, como en ``print(f(3))``. Cuando empiezas a
escriba programas más grandes y complejos, esto será más típico. De hecho, la declaración impresa generalmente solo será una
medida temporal mientras desarrolla el programa. Eventualmente, terminará llamando f y guardando el valor de retorno
o usándolo como parte de una expresión más compleja.

Sabrá que realmente ha internalizado la idea de las funciones cuando ya no esté confundido acerca de la diferencia
entre impresión y devolución. ¡Sigue trabajando hasta que tenga sentido para ti!

**Revisa tu entendimiento**

.. mchoice:: question11_11_1
   :answer_a: 2
   :answer_b: 5
   :answer_c: 7
   :answer_d: 25
   :answer_e: Error: y tiene un valor pero x es una variable independiente dentro de la función square
   :correct: c
   :feedback_a: 2 es la entrada; El valor devuelto por h es el que se imprimirá.
   :feedback_b: No olvides que 2 se eleva al cuadrado.
   :feedback_c: primer cuadrado 2, luego agregue 3.
   :feedback_d: 3 se agrega al resultado de la cuadratura 2
   :feedback_e: cuando se llama al cuadrado, x está vinculado al valor del parámetro que se pasa, 2.
   :practice: T

   ¿Cuál será el siguiente código de salida?

   .. code-block:: python

       def square(x):
           return x*x

       def g(y):
           return y + 3

       def h(y):
           return square(y) + 3

       print(h(2))

.. mchoice:: question11_11_2
   :answer_a: 2
   :answer_b: 5
   :answer_c: 7
   :answer_d: 10
   :answer_e: Error: no puede anidar llamadas de función
   :correct: d
   :feedback_a: Mejor lea la sección anterior una vez más.
   :feedback_b: Mejor lea la sección anterior una vez más.
   :feedback_c: Eso es h(2), pero se pasa a g.
   :feedback_d: h(2) devuelve 7, por lo que y está vinculado a 7 cuando se invoca g.
   :feedback_e: Ah, pero puede anidar llamadas de función.
   :practice: T

   ¿Cuál será el siguiente código de salida?
   
   .. code-block:: python 

       def square(x):
           return x*x
           
       def g(y):
           return y + 3
           
       def h(y):
           return square(y) + 3
           
       print((g(h(2)))
