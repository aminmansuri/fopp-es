..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-14-
   :start: 1

Actualización de variables
--------------------------

.. video:: updatevid
    :controls:
    :thumb: ../_static/updatethumb.png

    http://media.interactivepython.org/thinkcsVideos/update.mov
    http://media.interactivepython.org/thinkcsVideos/update.webm


Una de las formas más comunes de reasignación es una **actualización** donde el nuevo
valor de la variable depende de la antigua. Por ejemplo

.. sourcecode:: python

    x = x + 1

Esto significa obtener el valor actual de x, agregar uno y luego actualizar x con el nuevo
valor. El nuevo valor de x es el antiguo valor de x más 1. Aunque esta declaración de asignación puede
parecer un poco extraña, recuerda que ejecutar la asignación es un proceso de dos pasos. Primero, evalúe la
expresión del lado derecho Segundo, deje que el nombre de la variable en el lado izquierdo se refiera a este nuevo
objeto resultante. El hecho de que aparezca ``x`` en ambos lados no importa. La semántica de la tarea de
declaración asegura que no hay confusión en cuanto al resultado. El visualizador lo deja muy claro.

.. showeval:: se_ac2_14_1
   :trace_mode: true

   x = 6
   x = x + 1
   ~~~~
   x = {{x}}{{6}} + 1
   x = {{6 + 1}}{{7}}




.. activecode:: ac2_14_1

    x = 6        # inicializa x
    print(x)
    x = x + 1    # actualiza x
    print(x)


Si intenta actualizar una variable que no existe, recibirá un error porque
Python evalúa la expresión en el lado derecho del operador de asignación
antes de asignar el valor resultante al nombre de la izquierda.
Antes de poder actualizar una variable, debe **inicializarla**, generalmente con una
asignación simple. En el ejemplo anterior, ``x`` se inicializó a 6.

La actualización de una variable añadiéndole algo se llama **incremento**; restando es
un **decremento**. A veces, los programadores hablan de aumentar o disminuir sin especificar cuánto; cuando lo hacen, generalmente quieren decir con 1. A veces, los programadores también hablan sobre **golpear** una variable, lo que significa lo mismo que incrementarla en 1.

El aumento y la disminución son operaciones tan comunes que los lenguajes de programación a menudo incluyen una sintaxis especial para ello. En Python, ``+ =`` se usa para incrementar, y ``- =`` para disminuir. En algunos otros idiomas, incluso hay una sintaxis especial ``++`` y ``--`` para aumentar o disminuir en 1. Python no tiene una sintaxis tan especial. Para incrementar x en 1, debe escribir ``x += 1`` o ``x = x + 1``.

.. activecode:: ac2_14_2

    x = 6        # inicializa x
    print(x)
    x += 3       # incrementa x en 3; igual que x = x + 3
    print(x)
    x -= 1       # decrementa x en 1
    print(x)

Imagine que no quisiéramos aumentar en uno cada vez, sino que sumar
números del uno al diez, pero solo uno a la vez.

.. activecode:: ac2_14_3
  
  s = 1
  print(s)
  s = s + 2
  print(s)
  s = s + 3
  print(s)
  s = s + 4
  print(s)
  s = s + 5
  print(s)
  s = s + 6
  print(s)
  s = s + 7
  print(s)
  s = s + 8
  print(s)
  s = s + 9
  print(s)
  s = s + 10
  print(s)

Después de la declaración inicial, donde asignamos ``s`` a 1, podemos agregar el valor actual de
``s`` y el siguiente número que queremos agregar (2 hasta el 10) y finalmente
reasigne ese valor a ``s`` para que la variable se actualice después de cada línea en el
código.

Esto será tedioso cuando tengamos muchas cosas que agregar. Más tarde leerás sobre una
forma más fácil de hacer este tipo de tarea.


**Verifica tu entendimiento**

.. mchoice:: question2_14_1
   :answer_a: 12
   :answer_b: -1
   :answer_c: 11
   :answer_d: Nada. Se produce un error porque x nunca puede ser igual a x - 1.
   :correct: c
   :feedback_a: El valor de x cambia en la segunda declaración.
   :feedback_b: En la segunda declaración, sustituya el valor actual de x antes de restar 1.
   :feedback_c: Sí, esta declaración establece el valor de x igual al valor actual menos 1.
   :feedback_d: Recuerde que las variables en Python son diferentes de las variables en matemáticas en que (temporalmente) tienen valores, pero pueden reasignarse.
   :practice: T

   ¿Qué se imprime cuando se ejecutan las siguientes declaraciones?

   .. code-block:: python

     x = 12
     x = x - 1
     print(x)

.. mchoice:: question2_14_2
   :answer_a: 12
   :answer_b: 9
   :answer_c: 15
   :answer_d: Nada. Se produce un error porque x no se puede usar tantas veces en las instrucciones de asignación.
   :correct: c
   :feedback_a: El valor de x cambia en la segunda declaración.
   :feedback_b: Cada declaración cambia el valor de x, entonces 9 no es el resultado final.
   :feedback_c: Sí, comenzando con 12, resta 3, luego suma 5, y finalmente suma 1.
   :feedback_d: Recuerde que las variables en Python son diferentes de las variables en matemáticas en que (temporalmente) tienen valores, pero pueden reasignarse.
   :practice: T

   ¿Qué se imprime cuando se ejecutan las siguientes declaraciones?

   .. code-block:: python

     x = 12
     x = x - 3
     x = x + 5
     x = x + 1
     print(x)

.. parsonsprob:: pp2_14_1

   Construya el código que dará como resultado que se imprima el valor 134.
   -----
   mybankbalance = 100
   mybankbalance = mybankbalance + 34
   print(mybankbalance)

.. mchoice:: question2_14_3
   :multiple_answers:
   :answer_a: x = x + y
   :answer_b: y += x
   :answer_c: x += x + y
   :answer_d: x += y
   :answer_e: x++ y
   :correct: a,d
   :feedback_a: x se actualiza para que sea el valor anterior de x más el valor de y.
   :feedback_b: y se actualiza para que sea el valor anterior de y más el valor de x.
   :feedback_c: Esto actualiza x para que sea su valor anterior (debido a +=) más su valor anterior nuevamente (debido a la x en el lado derecho) más el valor de y, por lo que es equivalente a x = x + x + y
   :feedback_d: x se actualiza para que sea el valor anterior de x más el valor de y.
   :feedback_e: ++ no es una sintaxis que significa algo en Python.
   :practice: T

   ¿Cuál de las siguientes afirmaciones son equivalentes?
 