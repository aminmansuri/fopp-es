..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: func-7-
   :start: 1

.. index:: local variable
   variable; local
   lifetime

Las variables y los parámetros son locales.
-------------------------------------------

Una instrucción de asignación en una función crea una **variable local** para la variable en el lado izquierdo del
operador de asignación. Se llama local porque esta variable solo existe dentro de la función y no puede usarla
fuera de. Por ejemplo, considere nuevamente la función ``square``:

.. activecode:: ac11_7_1

    def square(x):
        y = x * x
        return y

    z = square(10)
    print(y)


Intenta ejecutar esto en Codelens. Cuando se invoca una función en Codelens, el ámbito local se separa del ámbito global por
Una caja azul. Las variables en el ámbito local se colocarán en el cuadro azul, mientras que las variables globales permanecerán en el global
marco. Si presiona el botón 'último >>' verá un mensaje de error. Cuando intentamos usar ``y`` en la línea 6 (fuera de
función) Python busca una variable global llamada ``y`` pero no encuentra una. Esto da como resultado el error:
``Error de nombre: 'y' no está definido``

La variable ``y`` solo existe mientras se ejecuta la función --- llamamos a esto su **duración**. Cuando
la ejecución de la función termina (regresa), las variables locales se destruyen. Codelens te ayuda a visualizar esto
porque las variables locales desaparecen después de que vuelve la función. Regrese y revise los estados de cuenta pagando
especial atención a las variables que se crean cuando se llama a la función. Tenga en cuenta cuando son posteriormente
destruido cuando la función regresa.

Los parámetros formales también son locales y actúan como variables locales. Por ejemplo, la vida útil de ``x`` comienza cuando
se llama ``square`` y su vida útil finaliza cuando la función completa su ejecución.

Por lo tanto, no es posible que una función establezca alguna variable local en un valor, complete su ejecución y luego cuando
se llama nuevamente la próxima vez, recupere la variable local. Cada llamada de la función crea nuevas variables locales, y
sus vidas caducan cuando la función vuelve a la persona que llama.

**Revisa tu entendimiento**

.. mchoice:: question11_7_1
   :answer_a: True
   :answer_b: False
   :correct: b
   :feedback_a: Las variables locales no se pueden referenciar fuera de la función en la que se definieron.
   :feedback_b: Las variables locales no se pueden referenciar fuera de la función en la que se definieron.
   :practice: T

   True o False: Las variables locales se pueden referenciar fuera de la función en la que se definieron.

.. fillintheblank:: question11_7_2

   ¿Cuáles de las siguientes son variables locales? Por favor, escríbalos en orden de línea en el código.

   .. sourcecode:: python

    numbers = [1, 12, 13, 4]
    def foo(bar):
        aug = str(bar) + "street"
        return aug

    addresses = []
    for item in numbers:
        addresses.append(foo(item))


   Las variables locales son

   -  :bar: ¡Buen trabajo!
      :aug: Si bien aug es una variable local, no es la primera en el código.
      :item: item no es una variable local.
      :.*: Incorrecto. Inténtelo de nuevo.
   -  :aug: ¡Buen trabajo!
      :bar: aunque bar es una variable local, no es la primera en el código.
      :item: item no es una variable local.
      :.*: Incorrecto. Inténtelo de nuevo.

.. mchoice:: question11_7_3
   :answer_a: 33
   :answer_b: 12
   :answer_c: Hay un error en el código.
   :correct: c
   :feedback_a: Incorrecto, mira nuevamente lo que está sucediendo.
   :feedback_b: Incorrecto, mira nuevamente lo que está sucediendo.
   :feedback_c: ¡Si! Hay un error porque hacemos referencia a y en la función de producción, pero se define al agregar. Como y es una variable local, no podemos usarla en ambas funciones sin inicializarla en ambas. Sin embargo, si inicializamos y como 3 en ambos, la respuesta sería 33.
   :practice: T

   ¿Cuál es el resultado del siguiente código?

   .. sourcecode:: python

     def adding(x):
         y = 3
         z = y + x + x
         return z

     def producing(x):
         z = x * y 
         return z

     print(producing(adding(4)))
