..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: sort-3-
   :start: 1

Parámetro clave opcional
-------------------------

Si desea ordenar las cosas en un orden distinto al "natural" o al revés, puede proporcionar un
parámetro adicional, el parámetro clave. Por ejemplo, suponga que desea ordenar una lista de números según
su valor absoluto, de modo que -4 viene después de 3? O suponga que tiene un diccionario con strings como teclas
y números como los valores. En lugar de ordenarlos en orden alfabético según las teclas, es posible que desee
ordenarlos en orden según sus valores.

Primero, veamos un ejemplo, y luego profundizaremos en cómo funciona.

Primero, definamos una función absoluta que tome un número y devuelva su valor absoluto.
(En realidad, python proporciona una función incorporada ``abs`` que hace esto, pero vamos a
definir el nuestro, por razones que se explicarán en un minuto).

.. activecode:: ac18_3_1

    L1 = [1, 7, 4, -2, 3]

    def absolute(x):
        if x >= 0:
            return x
        else:
            return -x

    print(absolute(3))
    print(absolute(-119))

    for y in L1:
        print(absolute(y))


Ahora, podemos pasar la función absoluta a L1 para especificar que queremos los elementos
ordenados por su valor absoluto, en lugar de por su valor real.

.. activecode:: ac18_3_2

    L1 = [1, 7, 4, -2, 3]

    def absolute(x):
        if x >= 0:
            return x
        else:
            return -x

    L2 = sorted(L1, key=absolute)
    print(L2)

    #or in reverse order
    print(sorted(L1, reverse=True, key=absolute))

¿Qué está pasando realmente allí? Hemos hecho algo bastante extraño. Antes todos los valores que tenemos
pasados como parámetros han sido bastante fáciles de entender: números, strings, lists, Booleans, diccionarios.
Aquí hemos pasado un objeto de función: absoluto es un nombre de variable cuyo valor es la función. Cuando nosotros
pasar ese objeto de función, *no* se invoca automáticamente. En cambio, solo está vinculado a lo formal
clave de parámetro de la función ordenada.

No vamos a ver el código fuente de la función incorporada ordenada. Pero si lo hiciéramos, encontraríamos
en algún lugar de su código, un parámetro llamado clave con un valor predeterminado de Ninguno. Cuando se proporciona un valor para ese
parámetro en una invocación de la función ordenada, tiene que ser una función. Lo que hace la función ordenada se
llame a esa función clave una vez para cada elemento de la lista que se está ordenando. Asocia el resultado devuelto
por esa función (la función absoluta en nuestro caso) con el valor original. Piensa en esos valores asociados
como pequeñas notas post-it que decoran los valores originales. El valor 4 tiene una nota post-it que dice 4
en él, pero el valor -2 tiene una nota post-it que dice 2 en él. Luego, la función ordenada reorganiza el original
elementos en el orden de los valores escritos en sus notas post-it asociadas.

Para ilustrar que la función absoluta se invoca una vez en cada elemento, durante la ejecución de ordenado,se
agregó algunas declaraciones de impresión en el código.

.. activecode:: ac18_3_3

    L1 = [1, 7, 4, -2, 3]

    def absolute(x):
        print("--- averiguar qué escribir en la nota post-it para" + str(x))
        if x >= 0:
            return x
        else:
            return -x

    print("A punto de llamar a sorted")
    L2 = sorted(L1, key=absolute)
    print("Ejecución terminada de sorted")
    print(L2)

Tenga en cuenta que este código nunca llama explícitamente a la función absoluta. Pasa la función absoluta como parámetro
valor a la función ordenada. Dentro de la función ordenada, cuyo código no hemos visto, se invoca esa función.

.. note::

   Es un poco confuso que estemos reutilizando la palabra *key* tantas veces. El nombre del parámetro opcional es
   ``key``. Por lo general, pasaremos un valor de parámetro utilizando el mecanismo de paso de parámetro de palabra clave. Cuando escribimos
   ``key=some_function`` en la invocación de la función, la palabra clave está ahí porque es el nombre del parámetro,
   especificado en la definición de la función de ordenamiento, no porque estemos usando el paso de parámetros basado en palabras clave.

**Revisa tu entendimiento**

.. activecode:: ac18_3_4
   :language: python
   :autograde: unittest
   :practice: T

   **1.** Ordenar la siguiente lista por la segunda letra de la A a la Z de cada elemento. Cree una función para usar al ordenar, llamada ``second_let``. Tomará un string como entrada y devolverá la segunda letra de ese string. Luego ordene la lista, cree una variable llamada ``sorted_by_second_let`` y asígnele la lista ordenada. No use lambda.
   ~~~~

   ex_lst = ['hi', 'how are you', 'bye', 'apple', 'zebra', 'dance']

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(sorted_by_second_let, sorted(ex_lst, key = second_let), "Testing that func_sort has the correct value.")
         self.assertEqual(second_let('0123456789'), '1', "Testing that the second_let function returns the second letter in a string.")
         self.assertNotIn("lambda", self.getEditorText(), "Checking that you did *not* use a lambda (Don't worry about actual and expected values).")

   myTests().main()

.. activecode:: ac18_3_5
   :language: python
   :autograde: unittest
   :practice: T

   **2.** A continuación, proporcionamos una lista de strings llamada ``nums``. Escriba una función llamada ``last_char`` que tome un string como entrada y solo devuelva su último carácter. Use esta función para ordenar la lista ``nums`` por el último dígito de cada número, de mayor a menor, y guárdela como una nueva lista llamada ``nums_sorted``.
   ~~~~

   nums = ['1450', '33', '871', '19', '14378', '32', '1005', '44', '8907', '16']

   def last_char():

   nums_sorted =

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testA(self):
         self.assertEqual(nums_sorted, ['19', '14378', '8907', '16', '1005', '44', '33', '32', '871', '1450'], "Testing that nums_sorted was created correctly.")
      def testB(self):
         self.assertEqual(last_char('pants'), 's', "Testing the function last_char on input 'pants'.")


   myTests().main()

.. activecode:: ac18_3_6
   :language: python
   :autograde: unittest
   :practice: T

   **3.** Una vez más, ordene la lista ``nums`` según el último dígito de cada número de mayor a menor. Sin embargo, ahora debe hacerlo escribiendo una función lambda. Guarde la nueva lista como ``nums_sorted_lambda``.
   ~~~~

   nums = ['1450', '33', '871', '19', '14378', '32', '1005', '44', '8907', '16']

   nums_sorted_lambda =

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testA(self):
         self.assertEqual(nums_sorted_lambda, ['19', '14378', '8907', '16', '1005', '44', '33', '32', '871', '1450'], "Testing that nums_sorted_lambda was created correctly.")
         self.assertIn("lambda", self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")


   myTests().main()
