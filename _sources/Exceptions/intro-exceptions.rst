..  Copyright (C)  Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: exceptions-
   :start: 1

.. _exceptions_chap:


¿Qué es una excepción?
======================

Una *excepción* es una señal de que ha ocurrido una condición que no puede ser fácilmente
manejada usando el flujo de control normal de un programa en Python. Las *excepciones*
son usualmente definidas como "errores" pero no siempre es el caso. Todos los errores en
Python son tratados usando *excepciones*, pero no todas las *excepciones* son errores.

Manejo de excepciones: Control de flujo
=======================================

Para explicar lo que hace una *excepción*, repasemos el "flujo de control" normal
en un programa en Python. Funcionando normalmente Python ejecuta sentencias secuencialmente,
una tras otra, pero para las tres estructuras: sentencias if, bucles y llamadas a funciones, esta
ejecución secuencial es interrumpida.

* En las *sentencias if*, solo se ejecuta uno de varios bloques de instrucciones
  y luego el flujo de control salta a la primera setencia después de la sentecia if.
* Para los *bucles*, cuando el final de un bucle  es alcanzado, el flujo de control
  vuelve al inicio del bucle y hace una prueba para determinar si el bucle necesita
  ejecutarse de nuevo. Si el ciclo ha finalizado, el flujo de control salta a la
  primera declaración después del bucle.
* Para las *llamadas a funciones*, el flujo de control salta a la primera sentencia
  en la función llamada, la función se ejecuta, y el flujo de control
  salta a la siguiente declaración después de la llamada a la función.

¿Ves el patrón? Si el flujo de control no es puramente secuencial,
siempre ejecuta la primera instrucción inmediatamente después del flujo de
control alterado. Es por eso que podemos decir que el flujo de control de
Python es secuencial. Pero hay casos en los que este flujo de control secuencial
No funciona bien.

Las excepciones nos brindan una manera de tener un punto no secuencial donde podemos manejar algo fuera de lo común (excepcional).

Levantando y atrapando errores
------------------------------

.. index:: try, except, Exception

La estructura de control try/except proporciona una forma de procesar un error en tiempo de ejecución y continuar con la ejecución del programa. Hasta ahora, cualquier error en tiempo de ejecución, como solicitar el octavo elemento de una lista con solo 3 elementos, o dividirlo por 0, ha provocado que la ejecución del programa se detenga. En las ventanas ActiveCode del navegador, aparece un mensaje de error en un cuadro en la parte de abajo. Cuando ejecuta programas de Python desde la línea de comandos, también recibe un mensaje de error que dice algo sobre lo que salió mal y en qué línea se produjo. Después de que se encuentra el error en tiempo de ejecución, el intérprete de Python no intenta ejecutar el resto del código. Debe hacer algún cambio en su código y volver a ejecutar todo el programa.

Con try/except, le dices al intérprete de python :

* Intenta ejecutar un bloque de códgio, sentencia "try".
   * Si todo el bloque de código se ejecuta sin errores de tiempo de ejecución, simplemente continúa con el resto del programa después de la declaración try/except.

* Si un error de tiempo de ejecución ocurre durante la ejecución de un bloque de código:
   * Omita el resto de ese bloque de código (pero no salga de todo el programa)
   * Ejecuta el bloque de código en la sentencia "except"
   * Luego continúe con el resto del programa después de la declaración try/except

.. sourcecode:: python

   try:
      <try clause code block>
   except <ErrorType>:
      <exception handler code block>

La sintaxis es bastante sencilla. La única parte difícil es que después de la palabra, excepto, opcionalmente puede haber una especificación de los tipos de errores que se manejarán. Quien los maneja es la clase Exception. Si escribes ``except Exception:`` se manejarán todos los errores de tiempo de ejecución. Si especifica una clase de errores más restringida, solo se manejarán esos errores; cualquier otro tipo de error hará que el programa deje de ejecutarse y se imprima un mensaje de error.

El código de abajo causa un error del tipo IndexError al intentar acceder al tercer elemento de una lista de dos elementos.

.. activecode:: exceptions_1
   :nocanvas:

   items = ['a', 'b']
   third = items[2]
   
   
El código de abajo causa un error del tipo ZeroDivisionError, o el menos específico ArithmeticError.

.. activecode:: exceptions_2
   :nocanvas:

   x = 5
   y = x/0

Veamos qué pasa si atrapamos algo de este código problemático en una sentencia try/except. Nota que ``this won't print`` no se imprime: cuando se encuentra un error, se omite el resto del bloque try y se ejecuta el bloque de excepción. Cuando ell bloque de excepción termina, continúa con la siguiente línea de código que está identada al mismo nivel que la sentencia try entonces: ``continuing`` es impreso.

.. activecode:: exceptions_3
   :nocanvas:
   
   try:
       items = ['a', 'b']
       third = items[2]
       print("This won't print")
   except Exception:
       print("got an error")
   
   print("continuing")

 
Si solo manejamos IndexEror y tenemos un error de división por cero, El programa detendrá su ejecución.
   
.. activecode:: exceptions_4
   :nocanvas:
   
   try:
       items = ['a', 'b']
       third = items[2]
       print("This won't print")
   except IndexError:
       print("error 1")
      
   print("continuing")
   
   try:
       x = 5
       y = x/0
       print("This won't print, either")
   except IndexError:
       print("error 2")
       
       
   print("continuing again")
   
   
Hay otra característica útil. El código de excepción puede acceder a una variable que contiene información sobre exactamente cuál fue el error. Así, por ejemplo, en la cláusula except podría imprimir la información que normalmente se imprimiría como un mensaje de error pero continuaría con la ejecución del resto del programa. Para hacerlo, especifique un nombre de variable después de la clase de excepción que se está manejando. El código de la cláusula de excepción puede referirse a ese nombre de variable.

.. activecode:: exceptions_5
   :nocanvas:
   
   try:
       items = ['a', 'b']
       third = items[2]
       print("This won't print")
   except Exception, e:
       print("got an error")
       print(e)
   
   print("continuing")


**Check your understanding**

.. mchoice:: exceptions_mc_1
   :answer_a: De  sintaxis
   :answer_b: De tiempo de ejecución
   :answer_c: De semántica
   :feedback_a: Los errores de sintaxis son cosas como dos puntos o cadenas que no están terminados. Try/except no siempre ayudan con esto. El programa seguirá sin funcionar.
   :feedback_b: Los errores de ejecución como index out of bounds pueden ser atrapados y manejados con try/except.
   :feedback_c: Si su programa se ejecuta hasta su finalización pero hace algo incorrecto, try/except no te ayudará.
   :correct: b
   
   ¿Qué tipo de error puede ser advertido y manejado usando try/except?
   
.. mchoice:: exceptions_mc_2
   :answer_a: Verdaddero
   :answer_b: Falso
   :feedback_a: Si su código solo detecta errores de IndexError, la excepción no se manejará y la ejecución finalizará.
   :feedback_b: Si su código solo detecta errores de IndexError, la excepción no se manejará y la ejecución finalizará.
   :correct: a

   Cuando una excepción de tipo de tiempo de ejecución  ZeroDivisionError ocurre y tienes una sentencia ``except IndexError``, el programa dejará de ejecurtarse por completo:

.. mchoice:: exceptions_mc_3
   :answer_a: Verdadero
   :answer_b: Falso
   :feedback_a: Se ejecutará el resto del código después de toda la instrucción try/except, pero no el resto del código en el bloque try.
   :feedback_b: Se ejecutará el resto del código después de toda la instrucción try/except, pero no el resto del código en el bloque try.
   :correct: b

   Después de que una excepción excepto maneje una excepción en tiempo de ejecución, se ejecutará el resto del código en la cláusula try.


.. mchoice:: exceptions_mc_4
   :answer_a: 0
   :answer_b: 1
   :answer_c: 3
   :answer_d: 4
   :answer_e: 5  
   :feedback_a: Try i = 0; Eso debería imprimir .3333
   :feedback_b: Sigue intentando.
   :feedback_c: Cuando i=3, ya no podrá imprimir 1.0/ (3-i), pero seguirá impimiendo una o más líneas en la cláusula except.
   :feedback_d: Imprimirá la fracción para tres valores de i, y luego un mensaje de error.
   :feedback_e: When i=3, dará un error de tiempo de ejecución, y la ejecución se detiene después de eso.
   :correct: d
   :practice: T

   ¿Cuántas líneas se imprimirán cuando se ejecute el siguiente código?
   
   .. sourcecode:: python
   
      try:
          for i in range(5):
              print(1.0 / (3-i))
      except Exception, error_inst:
          print("Got an error", error_inst)

.. activecode:: ee_exceptions_012
   :tags: Exceptions/intro-exceptions.rst
   :practice: T

   5. A continuación, proporcionamos una lista de tuplas que consisten en nombres de estudiantes, puntajes de exámenes finales y si aprobarán o no la clase. Para algunos estudiantes, la tupla no tiene un tercer elemento porque no se sabe si pasarán o no. Actualmente, el bucle for no funciona. Agregue una cláusula try/except para que el código se ejecute sin errores: si no hay un tercer elemento en la tupla, no se deben realizar cambios en el diccionario.
   ~~~~

   students = [('Timmy', 95, 'Will pass'), ('Martha', 70), ('Betty', 82, 'Will pass'), ('Stewart', 50, 'Will not pass'), ('Ashley', 68), ('Natalie', 99, 'Will pass'), ('Archie', 71), ('Carl', 45, 'Will not pass')]

   passing = {'Will pass': 0, 'Will not pass': 0}
   for tup in students:
       if tup[2] == 'Will pass':
           passing['Will pass'] += 1
       elif tup[2] == 'Will not pass':
           passing['Will not pass'] += 1

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(passing, {'Will pass': 3, 'Will not pass': 2}, "Testing that passing is created correctly.")

   myTests().main()

.. activecode:: ee_exceptions_022
   :tags: Exceptions/intro-exceptions.rst
   :practice: T

   6. A continuación, hemos proporcionado un código que no se ejecuta. Agregue una cláusula try/except para que el código se ejecute sin errores. Si un elemento no puede someterse a la operación de adición, la cadena 'Error' debe agregarse a plus_four.
   ~~~~

   nums = [5, 9, '4', 3, 2, 1, 6, 5, '7', 4, 3, 2, 6, 7, 8, '0', 3, 4, 0, 6, 5, '3', 5, 6, 7, 8, '3', '1', 5, 6, 7, 9, 3, 2, 5, 6, '9', 2, 3, 4, 5, 1]

   plus_four = []

   for num in nums: 
       plus_four.append(num+4)


   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(plus_four, [9, 13, 'Error', 7, 6, 5, 10, 9, 'Error', 8, 7, 6, 10, 11, 12, 'Error', 7, 8, 4, 10, 9, 'Error', 9, 10, 11, 12, 'Error', 'Error', 9, 10, 11, 13, 7, 6, 9, 10, 'Error', 6, 7, 8, 9, 5], "Testing that plus_four is created correctly.")

   myTests().main()