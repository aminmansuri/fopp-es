..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: tuples-4-
   :start: 1

.. index::
    single: assignment; tuple 
    single: tuple; assignment 

Asignación de tuplas con desempaquetado
-----------------------------------------

Python tiene una característica **tuple assignment** muy poderosa que permite una tupla de nombres de variables a la izquierda de un
declaración de asignación para asignar valores de una tupla a la derecha de la asignación. Otra forma de pensar en esto
es que la tupla de valores está **desempaquetada** en los nombres de las variables.

.. activecode:: ac12_4_1

    julia = "Julia", "Roberts", 1967, "Duplicity", 2009, "Actress", "Atlanta, Georgia"

    name, surname, birth_year, movie, movie_year, profession, birth_place = julia

Esto equivale a siete declaraciones de asignación, todas en una sola línea fácil. Un requisito es que el número de
variables de la izquierda deben coincidir con el número de elementos en la tupla.

De vez en cuando, es útil intercambiar los valores de dos variables. Con las declaraciones de asignación convencionales, tenemos que
usa una variable temporal. Por ejemplo, para intercambiar ``a`` y ``b``:

.. activecode:: ac12_4_2

    a = 1
    b = 2
    temp = a
    a = b
    b = temp
    print(a, b, temp)

La asignación de tuplas resuelve este problema perfectamente:

.. activecode:: ac12_4_3

    a = 1
    b = 2
    (a, b) = (b, a)
    print(a, b)

El lado izquierdo es una tupla de variables; el lado derecho es una tupla de valores. Cada valor se asigna a sus respectivos
variable. Todas las expresiones en el lado derecho se evalúan antes de cualquiera de las asignaciones. Esta característica hace
Asignación de tuplas bastante versátil.

Naturalmente, el número de variables a la izquierda y el número de valores a la derecha tienen que ser los mismos.

.. activecode:: ac12_4_4

    (a, b, c, d) = (1, 2, 3) # ValueError: need more than 3 values to unpack 

Anteriormente estábamos demostrando cómo usar las tuplas como valores de retorno al calcular el área y la circunferencia de un
círculo. Aquí podemos desempaquetar los valores de retorno después de llamar a la función.

.. activecode:: ac12_4_5
    
    def circleInfo(r):
        """ Return (circumference, area) of a circle of radius r """
        c = 2 * 3.14159 * r
        a = 3.14159 * r * r
        return c, a

    print(circleInfo(10))
    
    circumference, area = circleInfo(10)
    print(circumference)
    print(area)

    circumference_two, area_two = circleInfo(45)
    print(circumference_two)
    print(area_two)

Python incluso proporciona una manera de pasar una sola tupla a una función y hacer que se desempaquete para asignarla a la persona nombrada
parámetros

.. activecode:: ac12_4_6

    def add(x, y):
        return x + y
        
    print(add(3, 4))
    z = (5, 4)
    print(add(*z)) # this line will cause the values to be unpacked
    print(add(z)) # this line causes an error

Si ejecuta esto, recibirá un error causado por la línea 7, donde dice que la función add espera dos
parámetros, pero solo está pasando un parámetro (una tupla). En la línea 6 verá que la tupla está desempaquetada y 5 es
obligado a x, 4 a y.

No te preocupes por dominar esta idea todavía. Pero más adelante en el curso, si encuentras algún código que alguien más tiene
escrito que usa la notación * dentro de una lista de parámetros, regrese y mire esto nuevamente.

.. note::

    Desempaquetar en múltiples nombres de variables también funciona con listas, o cualquier otro tipo de secuencia, siempre que haya exactamente un valor para cada variable. Por ejemplo, puede escribir ``x, y = [3, 4]``.

Desempaquetado en Variables de Iterador
-----------------------------------------

La asignación múltiple con desempaquetado es particularmente útil cuando recorre una lista de tuplas o listas.

Por ejemplo, un diccionario consta de pares clave-valor. Cuando llama al método items() en un diccionario, obtiene una secuencia de
pares clave-valor. Cada uno de esos pares es una tupla de dos elementos. (Más generalmente, nos referimos a cualquier tupla de dos elementos como
**par**). Puede iterar sobre los pares clave-valor.

.. activecode:: ac12_4_7

    d = {"k1": 3, "k2": 7, "k3": "some other value"}

    for p in d.items():
        print("key: {}, value: {}".format(p[0], p[1]))

Cada vez que se ejecuta la línea 4, p se referirá a un par clave-valor de d. Un par es solo una tupla, por lo que p[0] se refiere a
clave y p[1] se refiere al valor.

Ese código es más fácil de leer si desempaquetamos los pares clave-valor en dos nombres de variables.

.. activecode:: ac12_4_8

    d = {"k1": 3, "k2": 7, "k3": "some other value"}

    for k, v in d.items():
        print("key: {}, value: {}".format(k, v))

En términos más generales, si tiene una lista de tuplas que tienen más de dos elementos y las repite con un
bucle sacando información de las tuplas, el código será mucho más legible si los desempaqueta en
nombres de variables justo después de la palabra ``for``.

**Revisa tu Entendimiento**

.. mchoice:: question12_4_1
   :practice: T
   :multiple_answers:
   :answer_a: Haga que las dos últimas líneas de la función sean "return x" y "return y"
   :answer_b: Incluya la declaración "return [x, y]"
   :answer_c: Incluya la declaración "return (x, y)"
   :answer_d: Incluya la declaración "return x, y"
   :answer_e: No es posible devolver dos valores; hacer dos funciones que cada una calcule un valor.
   :feedback_a: Tan pronto como se ejecuta la primera declaración de retorno, la función se cierra, por lo que la segunda nunca se ejecutará; solo se devolverá x
   :feedback_b: return [x,y] no es el método preferido porque devuelve xey en una lista y tendría que desempaquetar manualmente los valores. Pero es viable.
   :feedback_c: return (x, y) retorna una tupla.
   :feedback_d: return x, y hace que los dos valores se empaqueten en una tupla.
   :feedback_e: Es posible, y con frecuencia útil, tener una función que calcule múltiples valores.
   :correct: b,c,d

   Si desea que una función devuelva dos valores, contenidos en las variables x e y, ¿cuál de los siguientes métodos funcionará?

.. mchoice:: question12_4_2
   :practice: T
   :answer_a: No puede usar diferentes nombres de variables en el lado izquierdo y derecho de una declaración de asignación.
   :answer_b: Al final, x todavía tiene su valor original en lugar del valor original de y.
   :answer_c: En realidad, ¡funciona bien!
   :feedback_a: Seguro que puede; puede usar cualquier variable en el lado derecho que ya tenga un valor.
   :feedback_b: Una vez que asigna el valor de x a y, el valor original de y desaparece.
   :feedback_c: Una vez que asigna el valor de x a y, el valor original de y desaparece.
   :correct: b

   Considere la siguiente forma alternativa de intercambiar los valores de las variables x e y. ¿Qué tiene de malo?
   
   .. code-block:: python 
        
        # assume x and y already have values assigned to them
        y = x
        x = y   

.. activecode:: ac12_4_9
   :language: python
   :autograde: unittest
   :practice: T
   :chatcodes:

   **3.** Con solo una línea de código, asigne las variables agua, fuego, electricidad y pasto a los valores "Squirtle", "Charmander", "Pikachu" y "Bulbasaur"
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(water, "Squirtle", "Testing that water is assigned to the correct value.")
         self.assertEqual(fire, "Charmander", "Testing that fire is assigned to the correct value.")
         self.assertEqual(electric, "Pikachu", "Testing that electric is assigned to the correct value.")
         self.assertEqual(grass, "Bulbasaur", "Testing that grass is assigned to the correct value.")

   myTests().main()
   
.. activecode:: ac12_4_10
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T

   **4.** Con solo una línea de código, asigne cuatro variables, ``v1``, ``v2``, ``v3`` y ``v4``, a los siguientes cuatro valores: 1, 2, 3, 4.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(v1, 1, "Testing that v1 was assigned correctly.")
         self.assertEqual(v2, 2, "Testing that v2 was assigned correctly.")
         self.assertEqual(v3, 3, "Testing that v3 was assigned correctly.")
         self.assertEqual(v4, 4, "Testing that v4 was assigned correctly.")

   myTests().main()


.. activecode:: ac12_4_11
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T

   **1.** Si recuerdas, el método de diccionario .items() produce una secuencia de tuplas. Teniendo esto en cuenta, le proporcionamos un diccionario llamado ``pokemon``. Para cada par de valores clave, agregue la clave a la lista ``p_names``, y agregue el valor a la lista ``p_number``. No utilice los métodos .keys() o .values().
   ~~~~

   pokemon = {'Rattata': 19, 'Machop': 66, 'Seel': 86, 'Volbeat': 86, 'Solrock': 126}

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(sorted(p_names), sorted(['Rattata', 'Machop', 'Seel', 'Volbeat', 'Solrock']), "Testing that p_name has the correct values")
      def testTwo(self):
         self.assertEqual(sorted(p_number), sorted([19,66,86,86,126]), "Testing that p_number hsa the correct values")
         self.assertNotIn('.keys()', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertIn('.items()', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('.values()', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

   myTests().main()

.. activecode:: ac12_4_12
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T

   **2.** El método .items() produce una secuencia de tuplas de pares clave-valor. Con esto en mente, escriba el código para crear una lista de claves del diccionario ``track_medal_counts`` y asigne la lista al nombre de la variable ``track_events``. **NO** use el método .keys().
   ~~~~

   track_medal_counts = {'shot put': 1, 'long jump': 3, '100 meters': 2, '400 meters': 2, '100 meter hurdles': 3, 'triple jump': 3, 'steeplechase': 2, '1500 meters': 1, '5K': 0, '10K': 0, 'marathon': 0, '200 meters': 0, '400 meter hurdles': 0, 'high jump': 1}

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(sorted(track_events), sorted(['shot put', 'long jump', '100 meters', '400 meters', '100 meter hurdles', 'triple jump', 'steeplechase', '1500 meters', '5K', '10K', 'marathon', '200 meters', '400 meter hurdles', 'high jump']) , "Testing that track_events was created correctly.")
         self.assertNotIn('.keys()', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertIn('.items()', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('in track_medal_counts:', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

   myTests().main()
