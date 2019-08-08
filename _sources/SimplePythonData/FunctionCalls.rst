..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-4-
   :start: 1

Llamadas a funciones
------------------------

El intérprete de Python puede calcular nuevos valores con llamadas a funciones. Si estás familiarizado con la idea de las funciones del álgebra de la escuela secundaria, allí puedes definir una función ``f`` especificando cómo transforma una entrada en una salida, ``f(x) = 3x + 2``. Luego, puedes escribir ``f(5)`` y esperar obtener el valor 17.

Python adopta una sintaxis similar para invocar funciones. Si hay una función con nombre ``foo`` que toma una sola entrada, podemos invocar foo en el valor 5 escribiendo ``foo(5)``.

Hay muchas funciones integradas disponibles en Python. Verá algunos en este capítulo y en los próximos capítulos.

Las funciones son como las fábricas que toman algo de material, realizan algunas operaciones y luego envían el objeto resultante.

.. image:: Figures/function_object.png
   :alt: Ícono que representa una función. Parece similar a una fábrica con tres lugares en la parte superior para que entre el valor y un lugar en la parte inferior para que salga el valor de salida / retorno.

En este caso, nos referimos a los materiales como argumentos o entradas y el objeto resultante se conoce como salida o valor de retorno. Este proceso de tomar entrada, hacer algo y luego enviar la salida se demuestra en el siguiente gif.

.. image:: Figures/function_calls.gif
   :alt: El Gif animado se muestra utilizando la representación visual de una fábrica como se usó anteriormente. Muestra tres flechas que entran en la función para representar esa entrada o argumentos que una función puede requerir. Luego muestra el temblor del objeto de función, que representa una acción que está completando la función. Luego muestra otra flecha que sale de la imagen de la función, que representa un valor de retorno o salida que viene de fábrica.

.. note::

    No confunda el "valor de salida" de una función con la ventana de salida. La salida de una función es un valor de Python y nunca podemos ver realmente la representación interna de un valor. Pero podemos dibujar imágenes para ayudarnos a imaginar qué son los valores, o podemos imprimirlos para ver una representación externa en la ventana de salida.

    Para confundir aún más las cosas, ``print`` es en realidad una función. Todas las funciones producen valores de salida. Solo la función ``print`` hace que aparezcan cosas en la ventana de salida.

También es posible que los programadores definan nuevas funciones en sus programas. Aprenderá cómo hacerlo más adelante en el curso. Por ahora, solo necesita aprender cómo invocar o llamar a una función y comprender que la ejecución de la función devuelve un valor calculado.

.. activecode:: ac2_4_1
   :nocanvas:
   :hidecode:

   def square(x):
      return x * x

   def sub(x, y):
      return x - y

Hemos definido dos funciones arriba. El código está oculto para no molestarlo (todavía) con la forma en que se definen las funciones.
``square`` toma un solo parámetro de entrada y devuelve esa entrada multiplicada por sí misma. ``sub`` toma dos entradas
(parámetros) y devuelve el resultado de restar el segundo del primero. Obviamente, estas funciones no son
particularmente útiles, ya que tenemos los operadores ``*`` y ``-`` disponibles. Pero ilustran cómo funcionan las funciones.
La siguiente imagen ilustra cómo funciona la función ``square``.

.. image:: Figures/square_function.gif
   :alt: una visual de la función cuadrada. Se proporciona cuatro como entrada, el objeto de función se sacude y luego dieciséis sale de la parte inferior del objeto de función.

.. activecode:: ac2_4_2
   :include: ac2_4_1
   :nocanvas:


   print(square(3))
   square(5)
   print(sub(6, 4))
   print(sub(5, 9))


Observe que cuando una función toma más de un parámetro de entrada, las entradas están separadas por una coma. También
el orden de las entradas importa. El valor antes de la coma se trata como la primera entrada, el valor después de ella
como la segunda entrada.

Nuevamente, recuerde que cuando Python realiza cálculos, los resultados solo se muestran en la ventana de salida si hay una
declaración de impresión que dice hacer eso. En la ventana de activcode arriba, ``square(5)`` produce el valor 25 pero nunca
se ve eso en la ventana de salida, porque no está impreso.

Llamadas a funciones como parte de expresiones complejas
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

En cualquier lugar de una expresión se puede escribir un literal como un número, también puede escribir una invocación de función que
produce un número

Por ejemplo:

.. activecode:: ac2_4_3
   :include: ac2_4_1
   :nocanvas:


   print(square(3) + 2)
   print(sub(square(3), square(1+1)))


Echemos un vistazo a cómo se desarrolla esa última ejecución.

.. showeval:: se_ac2_4_1a
   :trace_mode: true

   Tenga en cuenta que siempre tenemos que resolver primero la expresión dentro de los paréntesis más internos, para determinar qué entrada proporcionar al llamar a las funciones.
   ~~~~
   print(sub({{square(3)}}{{9}}, square(1+1)))
   print(sub(9, square({{1+1}}{{2}})))
   print(sub(9, {{square(2)}}{{4}}))
   print({{sub(9, 4)}}{{5}})


Las funciones son objetos; los paréntesis invocan funciones
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

¿Recuerdas la mención anterior de que algunos tipos de objetos Python no tienen una buena representación impresa? Las funciones son
esos mismos solo objetos. Si le dices a Python que imprima el objeto de función, en lugar de imprimir los resultados de la invocación de
el objeto de función, obtendrá una de esas representaciones impresas no tan bonitas.

Simplemente al escribir el nombre de la función se refiere a la función como un objeto. Escribir el nombre de la función seguido de
el paréntesis ``()`` invoca la función.

.. activecode:: ac2_4_4
   :include: ac2_4_1
   :nocanvas:


   print(square)
   print(square(3))