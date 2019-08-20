..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: moreiter-2-
   :start: 1

La declaración ``while``
-------------------------

.. video:: whileloop
   :controls:
   :thumb: ../_static/whileloop.png

   http://media.interactivepython.org/thinkcsVideos/whileloop.mov
   http://media.interactivepython.org/thinkcsVideos/whileloop.webm

Hay otra declaración de Python que también se puede usar para construir una iteración. Se llama la declaración ``while``.
La declaración ``while`` proporciona un mecanismo mucho más general para iterar. Similar a la declaración ``if``, usa
una expresión booleana para controlar el flujo de ejecución. El cuerpo de while se repetirá mientras el control de
la expresión boolean se evalúa como ``True``.

Las siguientes dos figuras muestran el flujo de control. El primero se centra en el flujo dentro del bucle while y el segundo
muestra el ciclo while en contexto.

.. image:: Figures/while_flow.png
   :alt: un diamante en la parte superior tiene la frase "Is the condition True?". Dos flechas salen con la frase sí o no en las flechas. La flecha de sí apunta a un cuadro que dice "evaluate the statemenets in the body of the loop". Luego tiene una flecha que señala incondicionalmente a "Is the condition True?" diamante. La flecha de no escapa del bucle y apunta hacia abajo más allá del square "evaluate".

.. image:: Figures/while_loop.png
   :alt: imagen que muestra un rectángulo con "bloque de código" escrito en la parte superior. Luego, el texto que dice "while {condition}": seguido de un bloque sangrado con "run if {condition} is True" escrito en él. Una flecha apunta desde la parte inferior del bloque sangrado a la parte superior del ciclo while y dice "ejecutar ciclo nuevamente". En la parte inferior de la imagen hay un bloque sin sangría que dice la frase "bloque de código."

Podemos usar el bucle ``while`` para crear cualquier tipo de iteración que deseemos, incluido todo lo que tenemos previamente
hecho con un bucle ``for``. Por ejemplo, el programa en la sección anterior podría reescribirse usando ``while``.
En lugar de confiar en la función ``range`` para producir los números para nuestra suma, necesitaremos producirlos
nosotros mismos. Para hacer esto, crearemos una variable llamada ``aNumber`` y la inicializaremos a 1, el primer número en la
suma. Cada iteración agregará ``aNumber`` al total acumulado hasta que se hayan utilizado todos los valores. A fin de que
Para controlar la iteración, debemos crear una expresión booleana que se evalúe como ``True`` siempre que queramos mantener
agregando valores a nuestro total acumulado. En este caso, siempre que ``aNumber`` sea menor o igual que el límite,
debería seguir adelante.

Aquí hay una nueva versión del programa de suma que utiliza una instrucción while.

.. activecode:: ac14_2_1

    def sumTo(aBound):
        """ Return the sum of 1+2+3 ... n """

        theSum  = 0
        aNumber = 1
        while aNumber <= aBound:
            theSum = theSum + aNumber
            aNumber = aNumber + 1
        return theSum

    print(sumTo(4))

    print(sumTo(1000))

Casi puede leer la declaración ``while`` como si estuviera en lenguaje natural. Significa que mientras ``aNumber`` es menor
que o igual a ``aBound``, continúe ejecutando el cuerpo del bucle. Dentro del cuerpo, cada vez, actualice ``theSum``
utilizando el patrón del acumulador e incremente ``aNumber``. Después del cuerpo del bucle, volvemos a la condición
del ``while`` y reevaluarlo. Cuando ``aNumber`` se vuelve mayor que ``aBound``, la condición falla y fluye
de control continúa a la declaración de ``return``.

El mismo programa en codelens le permitirá observar el flujo de ejecución.

.. codelens:: clens14_2_1
    :python: py3

    def sumTo(aBound):
        """ Return the sum of 1+2+3 ... n """

        theSum  = 0
        aNumber = 1
        while aNumber <= aBound:
            theSum = theSum + aNumber
            aNumber = aNumber + 1
        return theSum

    print(sumTo(4))

.. note:: Los nombres de las variables se han elegido para ayudar a la legibilidad.

Más formalmente, aquí está el flujo de ejecución para una declaración ``while``:

#. Evalúe la condición, produciendo ``False`` o ``True``.
#. Si la condición es ``False``, salga de la instrucción ``while`` y continúe la
   ejecución en la siguiente declaración.
#. Si la condición es ``True``, ejecute cada una de las declaraciones en el cuerpo y
   luego regrese al paso 1.

El cuerpo consta de todas las declaraciones debajo del encabezado con la misma sangría.

Este tipo de flujo se denomina **bucle** porque el tercer paso se repite hacia la parte superior. Tenga en cuenta que si
la condición es ``False`` la primera vez a través del ciclo, las declaraciones dentro del ciclo nunca se ejecutan.

El cuerpo del bucle debe cambiar el valor de una o más variables para que eventualmente la condición se vuelva
``False`` y el ciclo termina. De lo contrario, el bucle se repetirá para siempre. Esto se llama un **bucle infinito**.
Una fuente interminable de diversión para los informáticos es la observación de que las instrucciones escritas en la parte posterior de
la botella de champú (espuma, enjuague, repita) crea un bucle infinito.

En el caso que se muestra arriba, podemos probar que el ciclo termina porque sabemos que el valor de ``aBound`` es
finito, y podemos ver que el valor de ``aNumber`` aumenta cada vez a través del ciclo, por lo que eventualmente lo hará
tiene que exceder ``aBound``. En otros casos, no es tan fácil saberlo.

.. note::

    La introducción de la instrucción while nos hace pensar en los tipos de iteración que hemos visto. El ``for``
    la declaración siempre iterará a través de una secuencia de valores como la lista de nombres para la parte o la lista de
    números creados por ``range``. Como sabemos que iterará una vez para cada valor de la colección, es
    A menudo se dice que un bucle ``for`` crea una **iteración definida** porque definitivamente sabemos cuántas veces estamos
    va a iterar Por otro lado, la declaración ``while`` depende de una condición que necesita evaluar
    a  ``False`` para que el ciclo finalice. Como no necesariamente sabemos cuándo ocurrirá esto,
    crea lo que llamamos **iteración indefinida**. La iteración indefinida simplemente significa que no sabemos cuántos
    repetiremos, pero eventualmente la condición que controla la iteración fallará y la iteración fallará
    detener. (A menos que tengamos un bucle infinito que, por supuesto, es un problema)

Lo que notará aquí es que el ciclo ``while`` es más trabajo para usted --- el programador --- que el equivalente
bucle ``for``. Cuando se usa un ciclo ``while``, debe controlar la variable del ciclo usted mismo. Le das una inicial
valor, prueba de finalización y luego asegúrese de cambiar algo en el cuerpo para que el ciclo finalice. Ese
también hace que un bucle while sea más difícil de leer y comprender que el bucle equivalente. Entonces, mientras que *puedes* implementar
iteración definida con un ciclo while, no es una buena idea hacer eso. Use un bucle for siempre que se conozca
el comienzo del proceso de iteración cuántas veces se debe ejecutar el bloque de código.

**Revisa tu entendimiento**

.. mchoice:: question14_2_1
   :answer_a: True
   :answer_b: False
   :correct: a
   :feedback_a: Aunque el ciclo while usa una sintaxis diferente, es tan poderoso como un ciclo for y a menudo más flexible.
   :feedback_b: A menudo, un ciclo for es más natural y conveniente para una tarea, pero esa misma tarea siempre se puede expresar usando un ciclo while.

   True o False: Puede reescribir cualquier bucle for como un bucle while.

.. mchoice:: question14_2_2
   :answer_a: n comienza en 10 y se incrementa en 1 cada vez a través del ciclo, por lo que siempre será positivo
   :answer_b: La respuesta comienza en 1 y se incrementa en n cada vez, por lo que siempre será positiva
   :answer_c: No puede comparar n con 0 en el ciclo while. Debes compararlo con otra variable.
   :answer_d: En el cuerpo del bucle while, debemos establecer n en False, y este código no hace eso.
   :correct: a
   :feedback_a: El ciclo se ejecutará mientras n sea positivo. En este caso, podemos ver que n nunca será no positiva.
   :feedback_b: Si bien es cierto que la respuesta siempre será positiva, la respuesta no se considera en la condición de bucle.
   :feedback_c: Es perfectamente válido comparar n a 0. Aunque indirectamente, esto es lo que causa el bucle infinito.
   :feedback_d: La condición del bucle debe volverse False para que el bucle termine, pero n por sí sola no es la condición en este caso.
   :practice: T

   El siguiente código contiene un bucle infinito. ¿Cuál es la mejor explicación de por qué el ciclo no termina?

   .. code-block:: python

     n = 10
     answer = 1
     while ( n > 0 ):
       answer = answer + n
       n = n + 1
     print(answer)

.. mchoice:: question14_2_3
   :answer_a: un bucle for o un bucle while
   :answer_b: solo un ciclo for
   :answer_c: solo un ciclo while
   :correct: a
   :feedback_a: Aunque no sabe cuántas iteraciones ejecutará el bucle antes de que el programa comience a ejecutarse, una vez que haya elegido su entero aleatorio, Python sabe exactamente cuántas iteraciones ejecutará el bucle, por lo que funcionará un bucle for o un bucle while.
   :feedback_b: Como aprendió en la sección 7.2, un ciclo while siempre se puede usar para cualquier cosa para la que se pueda usar un ciclo for.
   :feedback_c: Aunque no sabe cuántas iteraciones ejecutará el ciclo antes de que el programa comience a ejecutarse, una vez que haya elegido su entero aleatorio, Python sabe exactamente cuántas iteraciones ejecutará el ciclo, por lo que este es un ejemplo de iteración definitiva.
   :practice: T

   Qué tipo de bucle se puede usar para realizar la siguiente iteración: elige un entero positivo al azar y luego imprime los números desde 1 hasta el entero seleccionado.


.. activecode:: ac14_2_2
   :practice: T

   Escriba un ciclo while que se inicialice en 0 y se detenga en 15. Si el contador es un número par, añádalo a una lista llamada ``eve_nums``.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

     def testOne(self):
        self.assertEqual(eve_nums, [0,2,4,6,8,10,12,14], "Testing that eve_nums has been assigned the correct elements")

   myTests().main()

.. activecode:: ac14_2_3
    :practice: T

    A continuación, proporcionamos un bucle for que resume todos los elementos de ``list1``. Escriba el código que realiza la misma tarea, pero en su lugar utiliza un ciclo while. Asigne la variable acumuladora al nombre ``accum``.
    ~~~~

    list1 = [8, 3, 4, 5, 6, 7, 9]

    tot = 0
    for elem in list1: 
        tot = tot + elem

    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

       def testOne(self):
          self.assertEqual(accum, 42, "Testing that accum has the correct value.")
          self.assertIn('while', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")


    myTests().main()

.. activecode:: ac14_2_4
    :practice: T

    Escriba una función llamada ``stop_at_four`` que itera a través de una lista de números. Usando un ciclo while, agregue cada número a una nueva lista hasta que aparezca el número 4. La función debería devolver la nueva lista.
    ~~~~

    def stop_at_four():



    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

       def testOne(self):
          self.assertEqual(stop_at_four([0, 9, 4.5, 1, 7, 4, 8, 9, 3]), [0, 9, 4.5, 1, 7], "Testing the function stop_at_four on the input [0, 9, 4.5, 1, 7, 4, 8, 9, 3].")
          self.assertEqual(stop_at_four([4, 1, 2, 8]), [], "Testing the function stop_at_four on the input [4, 1, 2, 8].")
          self.assertEqual(stop_at_four([4]), [], "Testing the function stop_at_four on the input [4].")
          self.assertEqual(stop_at_four([1, 6, 2, 3, 9]), [1, 6, 2, 3, 9], "Testing that stop_at_four([1, 6, 2, 3, 9]) returns ([1, 6, 2, 3, 9])")

    myTests().main()