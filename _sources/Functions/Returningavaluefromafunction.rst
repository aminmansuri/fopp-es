..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: func-4-
   :start: 1

Devolver un valor de una función
---------------------------------

.. image:: Figures/function_call.gif
   :alt: gif of a box labeled function with three spaces on the top for input and a space on the bottom for output. Three arrows enter the top and are labeled as input or arguments. The function box shakes, and then one arrow leaves the bottom of the function box.

No solo puede pasar un valor de parámetro a una función, una función también puede producir un valor. Ya lo tienes
visto esto en algunas funciones anteriores que ha utilizado. Por ejemplo, ``len`` toma una lista o string como parámetro
valor y devuelve un número, la longitud de esa lista o string. ``range`` toma un entero como valor de parámetro y
devuelve una lista que contiene todos los números desde 0 hasta ese valor de parámetro.

Las funciones que devuelven valores a veces se denominan **funciones fructíferas**. En muchos otros idiomas, una función que
no devuelve un valor se llama un **procedimiento**, pero nos quedaremos aquí con la forma de Python de llamarlo también una
función, o si queremos enfatizarlo, una función *no fructífera*.

.. image:: Figures/blackboxfun.png

¿Cómo escribimos nuestra propia función fructífera? Comencemos creando una función matemática muy simple que haremos
llamar ``square``. La función square tomará un número como parámetro y devolverá el resultado de la cuadratura del
número. Aquí está el diagrama de caja negra con el siguiente código de Python.

.. image:: Figures/squarefun.png

.. activecode:: ac11_4_1

    def square(x):
        y = x * x
        return y

    toSquare = 10
    result = square(toSquare)
    print("El resultado de {} square es {}.".format(toSquare, result))

La declaración **return** es seguida por una expresión que se evalúa. Su resultado se devuelve a la persona que llama como
"fruto" de llamar a esta función. Debido a que la declaración de retorno puede contener cualquier expresión de Python que podamos tener,
evitó crear la **variable temporal** ``y`` y simplemente usó ``return x*x``. Intenta modificar la función square
arriba para ver que esto funciona igual. Por otro lado, usando **variables temporales** como ``y`` en el programa
arriba facilita la depuración. Estas variables temporales se denominan **variables locales**.

Note algo importante aquí. El nombre de la variable que pasamos como argumento --- ``toSquare`` --- no tiene nada que
hacer con el nombre del parámetro formal  --- ``x``. Es como si se ejecuta ``x = toSquare`` cuando ``square`` es
llamado. No importa cómo se llamó el valor en la persona que llama (el lugar donde se invocó la función). Dentro
``square``, su nombre es ``x``. Puede ver esto muy claramente en codelens, donde están las variables globales y las locales
para la función cuadrada están en cuadros separados.

.. codelens:: clens11_4_1
    :python: py3

    def square(x):
        y = x * x
        return y

    toSquare = 10
    squareResult = square(toSquare)

Hay un aspecto más de los valores de retorno de la función que debe tenerse en cuenta. Todas las funciones de Python devuelven el valor especial
``None`` a menos que haya una declaración de retorno explícita con un valor diferente a ``None``. Considere lo siguiente un común
error cometido por los programadores principiantes de Python. A medida que avance en este ejemplo, preste mucha atención al retorno
valor en el listado de variables locales. Luego mire lo que se imprime cuando finaliza la función.

.. codelens:: clens11_4_2
    :python: py3

    def square(x):
        y = x * x
        print(y)   # ¡Malo! ¡Esto es confuso! ¡Debería usar return en su lugar!

    toSquare = 10
    squareResult = square(toSquare)
    print("The result of {} squared is {}.".format(toSquare, squareResult))

El problema con esta función es que, aunque imprima el valor de la entrada al cuadrado, ese valor no será
regresó al lugar donde se realizó la llamada. En cambio, se devolverá el valor ``None``. Como la línea 6 usa el
valor de retorno como el lado derecho de una instrucción de asignación, ``squareResult`` tendrá ``None`` como su valor y
El resultado impreso en la línea 7 es incorrecto. Normalmente, las funciones devolverán valores que se pueden imprimir o procesar
de otra manera por la persona que llama.

Una declaración de retorno, una vez ejecutada, finaliza inmediatamente la ejecución de una función, incluso si no es la última.
declaración en la función. En el siguiente código, cuando se ejecuta la línea 3, el valor 5 se devuelve y se asigna a
variable x, luego impresa. Las líneas 4 y 5 nunca se ejecutan. Ejecute el siguiente código e intente hacer algunas modificaciones de
para asegurarse de que entiende por qué "allí" y 10 nunca se imprimen.

.. activecode:: ac11_4_2

  def weird():
      print("here")
      return 5
      print("there")
      return 10
      
  x = weird()
  print(x)

El hecho de que una declaración de devolución finalice inmediatamente la ejecución del bloque de código dentro de una función es importante para
entender para escribir programas complejos, y también puede ser muy útil. El siguiente ejemplo es una situación donde
puede usar esto para su ventaja, y comprender esto lo ayudará a comprender mejor el código de otras personas, y
ser capaz de recorrer el código con más confianza.

Considere una situación en la que desea escribir una función para averiguar, de una lista de asistencia a clase, si alguien
El primer nombre es más largo que cinco letras, llamado ``longer_than_five``. Si hay alguien en clase cuyo primer nombre es
con más de 5 letras, la función debe devolver ``True``. De lo contrario, debería devolver ``False``.

En este caso, usará sentencias condicionales en el código que existe en el **cuerpo de la función**, el bloque de código
sangrado debajo de la declaración de definición de función (al igual que el código que comienza con la línea ``print("here")``
en el ejemplo anterior, ese es el cuerpo de la función ``extraño``, arriba).

**Desafío adicional para estudiar:** Después de mirar la explicación a continuación, deja de mirar el código, solo el
descripción de la función que se encuentra arriba e intente escribir el código usted mismo. Luego pruébelo en diferentes listas y haga
Seguro que funciona. Pero lea primero la explicación, para asegurarse de tener una sólida comprensión de estas funciones.
mecánica.

Primero, un plan en español para definir esta nueva función llamado ``longer_than_five``:

* Querrá pasar una lista de cadenas (que representan los nombres de las personas) a la función.
* Querrá iterar sobre todos los elementos de la lista, cada una de las cadenas.
* Tan pronto como llegue a un nombre que tenga más de cinco letras, sabrá que la función debe devolver `` Verdadero ''. ¡Sí, hay al menos un nombre con más de cinco letras!
* Y si revisa toda la lista y no había un nombre de más de cinco letras, entonces la función debería devolver `` False``.

Ahora, el código:

.. activecode:: ac11_4_3

  def longer_than_five(list_of_names):
      for name in list_of_names: # iterar sobre la lista para ver cada nombre
          if len(name) > 5: # tan pronto como vea un nombre de más de 5 letras,
              return True # luego retorna True!
              # Si Python ejecuta esa declaración de retorno, la función ha terminado y el resto del código no se ejecutará, ¡ya tiene su respuesta!
      return False # Solo llegarás a esta línea si
      # iterado en toda la lista y no obtuvo un nombre donde
      # la expresión if se evaluó como True, por lo que en este punto, ¡es correcto devolver False!

  # Aquí hay un par de llamadas de muestra a la función con diferentes listas de nombres. Intente ejecutar este código en Codelens varias veces y asegúrese de comprender exactamente lo que está sucediendo.

  list1 = ["Sam","Tera","Sal","Amita"]
  list2 = ["Rey","Ayo","Lauren","Natalie"]

  print(longer_than_five(list1))
  print(longer_than_five(list2))


Hasta ahora, acabamos de ver valores de retorno asignados a variables. Por ejemplo, tuvimos la línea
``squareResult = square(toSquare)``. Como con todas las declaraciones de asignación, el lado derecho se ejecuta primero. Eso
invoca la función `` cuadrado '', pasando un valor de parámetro 10 (el valor actual de ``toSquare``). Eso devuelve un
valor 100, que completa la evaluación del lado derecho de la tarea. 100 se asigna a la
variable ``squareResult``. En este caso, la invocación de la función fue la expresión completa que se evaluó.

Sin embargo, las invocaciones de funciones también se pueden usar como parte de expresiones más complicadas. Por ejemplo,
``squareResult = 2 * square(toSquare)``. En este caso, se devuelve el valor 100 y luego se multiplica por 2 para
producir el valor 200. Cuando python evalúa una expresión como ``x * 3``, sustituye el valor actual de x en
la expresión y luego hace la multiplicación. Cuando python evalúa una expresión como ``2 * square(toSquare)``,
sustituye el valor de retorno 100 por la invocación de la función completa y luego realiza la multiplicación.

Para reiterar, al ejecutar una línea de código ``squareResult = 2 * square(toSquare)``,
el intérprete hace estos pasos:

#. Es una declaración de asignación, así que evalúa la expresión del lado derecho ``2 * square(toSquare)``.
#. Busque los valores de las variables square y toSquare: square es un objeto de función y toSquare es 10
#. Pase 10 como valor de parámetro a la función, recupere el valor de retorno 100
#. Sustituya el cuadrado por 100 (toSquare), de modo que la expresión ahora lea ``2 * 100``
#. Asigne 200 a la variable ``squareResult``

**Revise su Entendimiento**

.. mchoice:: question11_4_1
   :answer_a: Nunca debe usar una declaración de impresión en una definición de función.
   :answer_b: No debería tener ninguna declaración en una función después de la declaración de devolución. Una vez que la función llega a la declaración de retorno, inmediatamente dejará de ejecutarla.
   :answer_c: Debe calcular el valor de x+y+z antes de devolverlo.
   :answer_d: Una función no puede devolver un número.
   :correct: b
   :feedback_a: Aunque no debe confundir la impresión con la devolución, puede incluir declaraciones de impresión dentro de sus funciones.
   :feedback_b: Este es un error muy común, ¡así que asegúrese de tenerlo en cuenta cuando escriba su código!
   :feedback_c: Python calculará automáticamente el valor x+y+z y luego lo devolverá en la declaración tal como está escrito
   :feedback_d: Las funciones pueden devolver cualquier información legal, incluidos (entre otros) números, strings, listas, diccionarios, etc.
   :practice: T

   Lo que está mal con la siguiente definición de función:

   .. code-block:: python

     def addEm(x, y, z):
         return x+y+z
         print('the answer is', x+y+z)

.. mchoice:: question11_4_2
   :answer_a: El valor None
   :answer_b: El valor de x+y+z
   :answer_c: El string 'x+y+z'
   :correct: a
   :feedback_a: Hemos usado accidentalmente print donde queremos decir retorno. Por lo tanto, la función devolverá el valor Ninguno de forma predeterminada. Este es un error MUY COMÚN, ¡así que ten cuidado! Este error también es particularmente difícil de encontrar porque cuando ejecuta la función la salida se ve igual. No es hasta que intenta asignar su valor a una variable que puede notar una diferencia.
   :feedback_b: ¡Cuidado! Este es un error muy común. Aquí hemos impreso el valor x+y+z pero no lo hemos devuelto. Para devolver un valor DEBEMOS utilizar la palabra clave return.
   :feedback_c: x+y+z calcula un número (suponiendo que x+y+z son números) que representa la suma de los valores x, y and z.
   :practice: T

   ¿Qué devolverá la siguiente función?

   .. code-block:: python

    def addEm(x, y, z):
        print(x+y+z)

.. mchoice:: question11_4_3
   :answer_a: 25
   :answer_b: 50
   :answer_c: 25 + 25
   :correct: b
   :feedback_a: Eleva al cuadrado 5 dos veces y los suma.
   :feedback_b: los dos valores de retorno se suman.
   :feedback_c: Los dos resultados se sustituyen en la expresión y luego se evalúa. Los valores devueltos son enteros en este caso, no cadenas.
   :practice: T

   What will the following code output?
   
   .. code-block:: python

       def square(x):
           y = x * x
           return y
           
       print(square(5) + square(5))

.. mchoice:: question11_4_4
   :answer_a: 8
   :answer_b: 16
   :answer_c: Error: no se puede poner una invocación de función entre paréntesis
   :correct: b
   :feedback_a: Eleva al cuadrado 2, produciendo el valor 4. Pero eso no significa que el siguiente valor multiplique 2 y 4.
   :feedback_b: Eleva al cuadrado 2, produciendo el valor 4. 4 luego se pasa como un valor al cuadrado nuevamente, obteniendo 16.
   :feedback_c: Esta es una expresión más complicada, pero aún válida. Se evalúa la expresión cuadrado (2) y el valor de retorno 4 sustituye al cuadrado (2) en la expresión.

   ¿Cuál será el siguiente código de salida?
   
   .. code-block:: python 

       def square(x):
           y = x * x
           return y
           
       print(square(square(2)))

.. mchoice:: question11_4_5
   :answer_a: 1
   :answer_b: Sí
   :answer_c: El primero fue más largo
   :answer_d: El segundo fue al menos tan largo
   :answer_e: Error
   :correct: c
   :feedback_a: cyu2 devuelve el valor 1, pero eso no es lo que se imprime.
   :feedback_b: "Sí" es más largo, pero eso no es lo que se imprime.
   :feedback_c: cyu2 devuelve el valor 1, que se asigna a z.
   :feedback_d: cyu2 devuelve el valor 1, que se asigna a z.
   :feedback_e: ¿qué crees que causará un error?
   :practice: T

   ¿Cuál será el siguiente código de salida?
   
   .. code-block:: python 

       def cyu2(s1, s2):
           x = len(s1)
           y = len(s2)
           return x-y
           
       z = cyu2("Si", "No")
       if z > 0:
           print("El primero fue más largo")
       else:
           print("El segundo fue al menos tan largo")
 
.. mchoice:: question11_4_6
   :answer_a: square
   :answer_b: g
   :answer_c: a number
   :correct: b
   :feedback_a: Antes de ejecutar el cuadrado, tiene que averiguar qué valor pasar, por lo que g se ejecuta primero
   :feedback_b: g debe ejecutarse y devolver un valor para saber qué valor de parámetro proporcionar a x.
   :feedback_c: square y g deben ejecutarse antes de imprimir el número.
   :practice: T

   ¿Cuál imprimirá primero, square, g o un número?
   
   .. code-block:: python 

       def square(x):
           print("square")
           return x*x
           
       def g(y):
           print("g")
           return y + 3
           
       print(square(g(2)))

.. mchoice:: question11_4_7
   :answer_a: 3
   :answer_b: 2
   :answer_c: None
   :correct: b
   :feedback_a: La función llega a una declaración de retorno después de imprimir 2 líneas, por lo que la tercera declaración de impresión no se ejecutará.
   :feedback_b: ¡Sí! Dos líneas impresas, y luego la ejecución del cuerpo de la función alcanza una declaración de retorno.
   :feedback_c: ¡La función devuelve un valor entero! Sin embargo, este código no imprime el resultado de la invocación de la función, por lo que no puede verlo (la impresión es para personas). Las únicas líneas que ve impresas son las que aparecen en las declaraciones de impresión antes de la declaración de devolución.
   :practice: T

   ¿Cuántas líneas imprimirá el siguiente código?
   
   .. code-block:: python

       def show_me_numbers(list_of_ints):
           print(10)
           print("Luego acumularemos la suma")
           accum = 0
           for num in list_of_ints:
               accum = accum + num
           return accum
           print("Todo hecho con acumulación!")

       show_me_numbers([4,2,3])

.. activecode:: ac11_4_4
   :language: python
   :autograde: unittest
   :practice: T

   **8.** Escriba una función llamada ``same`` que tome un string como entrada y simplemente devuelva ese string.
   ~~~~
   
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(same('hello'), 'hello', "Testing the same function on input 'hello'.")

   myTests().main()


.. activecode:: ac11_4_5
   :language: python
   :autograde: unittest
   :practice: T

   **9.** Escriba una función llamada ``same_thing`` que devuelva el parámetro, sin cambios.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(same_thing(5), 5,"Testing the function same_thing with input 5")
         self.assertEqual(same_thing("Welcome"), "Welcome", "Testing the function same_thing with input 'Welcome'")

   myTests().main()

.. activecode:: ac11_4_6
   :language: python
   :autograde: unittest
   :practice: T

   **10.** Escriba una función llamada ``subtract_three`` que tome un número entero o cualquier número como entrada, y devuelva ese número menos tres.
   ~~~~
   
   ===== 

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(subtract_three(9), 6, "Testing the subtract_three function on input 9.")
         self.assertEqual(subtract_three(-5), -8, "Testing the subtract_three function on input -5.")

   myTests().main()


.. activecode:: ac11_4_7
   :language: python
   :autograde: unittest
   :practice: T

   **11.** Escriba una función llamada ``change`` que tome un número como entrada y devuelva ese número, más 7.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(change(5), 12,"Testing the function change with input 5")
         self.assertEqual(change(-10), -3, "Testing the function change with input -10")

   myTests().main()

.. activecode:: ac11_4_8
   :language: python
   :autograde: unittest
   :practice: T

   **12.** Escriba una función llamada ``intro`` que tome un string como entrada. Dado el string "Becky" como entrada, la función debería devolver: "Hello, my name is Becky and I love SI 106."
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(intro("Mike"), "Hello, my name is Mike and I love SI 106.", "Testing the intro function on input 'Mike'.")

   myTests().main()


.. activecode:: ac11_4_9
   :language: python
   :autograde: unittest
   :practice: T

   **13.** Escriba una función llamada ``s_change`` que tome un string como entrada y devuelva ese string, concatenado con el string " for fun.".
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(s_change("Coding"), "Coding for fun." ,"Testing the function s_change with input coding")
         self.assertEqual(s_change("We go to the beach"), "We go to the beach for fun." , "Testing the function s_change with input We go to the beach")

   myTests().main()

.. activecode:: ac11_4_10
   :language: python
   :autograde: unittest
   :practice: T

   **14.** Escriba una función llamada ``decision`` que tome un string como entrada y luego verifique el número de caracteres. Si tiene más de 17 caracteres, devuelva "This is a long string", si es más corta o tiene 17 caracteres, devuelva "This is a short string".
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(decision("Well hello dolly"), "This is a short string", "Testing the function decision with input 'Well hello dolly'")
         self.assertEqual(decision("In olden days a glimps of stocking was looked on a something shocking but heaven knows, anything goes"), "This is a long string", "Testing the function decision with input 'In olden days a glimps of stocking was looked on a something shocking but heaven knows, anything goes'")
         self.assertEqual(decision("how do you do sir"), "This is a short string", "Testing the function decision with input 'how do you do sir'")

   myTests().main()
