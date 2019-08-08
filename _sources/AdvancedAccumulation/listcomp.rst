..  Copyright (C)  Paul Resnick Brad.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: AdAccum-4-
   :start: 1 

List Comprehensions
-------------------

Python proporciona una forma alternativa de hacer operaciones de ``mapa`` y ``filtro``, llamada **list comprehension**.
Muchos programadores los encuentran más fáciles de entender y escribir. Son formas concisas para crear listas de otras
listas. La sintaxis general es::

   [<transformer_expression> for <loop_var> in <sequence> if <filtration_expression>]

Donde el if es opcional.  For example,

.. activecode:: ac20_4_1

    things = [2, 5, 9]

    yourlist = [value * 2 for value in things]

    print(yourlist)

En el ejemplo, transformer expression es ``value * 2``. La variable del elemento es ``valor`` y la secuencia es ``things``. Esta es una forma alternativa
para realizar una operación de mapeo *mapping*. Al igual que con ``map``, cada elemento de la secuencia se transforma en un elemento en la nueva lista.
Sin embargo, en lugar de que la iteración ocurra automáticamente, hemos adoptado la sintaxis del bucle for que puede hacerlo más fácil de entender.

Al igual que en un bucle for regular, la parte de la declaración ``for value in things`` dice que se ejecute un código una vez para cada
artículo en things. Cada vez que se ejecuta ese código, ``value`` está vinculado a un elemento de ``things``. El código que se ejecuta
cada vez es la expresión del transformador ``valor * 2``, en lugar de un bloque de código identado debajo de la declaración del for.
La otra diferencia de un ciclo for regular es que cada vez que se evalúa la expresión, el valor resultante se adjunta a una lista.
Eso sucede automáticamente, sin que el programador inicialice explícitamente una lista vacía o agregue cada artículo.

La cláusula ``if`` de una list comprehension se puede usar para hacer una operación de filtrado. Para realizar una operación de filtrado puro la
expresión puede ser simplemente la variable que está vinculada a cada elemento. Por ejemplo, la siguiente list comprehension mantendrá
solo los números pares de la lista original.

.. activecode:: ac20_4_2

   def keep_evens(nums):
       new_list = [num for num in nums if num % 2 == 0]
       return new_list
      
   print(keep_evens([3, 4, 6, 7, 0, 1]))

También puedes combinar las operaciones ``map`` y ``filter`` encadenándolas, o con un list comprehension.

.. activecode:: ac20_4_3

   things = [3, 4, 6, 7, 0, 1]
   #Encadenando filter y map:
   #primero, filter para mantener solo los números pares
   #duplica cada uno de ellos
   print(map(lambda x: x*2, filter(lambda y: y % 2 == 0, things)))
   
   #versión equivalente usando list comprehension
   print([x*2 for x in things if x % 2 == 0])


**Revisa yu entendimiento**

.. mchoice:: question21_4_1
   :practice: T
   :answer_a: [4,2,8,6,5]
   :answer_b: [8,4,16,12,10]
   :answer_c: 10
   :answer_d: [10]
   :correct: d
   :feedback_a: Los elementos de alist se duplican antes de agregarse a blist.
   :feedback_b: No todos los artículos en alist serán incluidos en blist. Mira la cláusula if.
   :feedback_c: El resultado debe ser una lista.
   :feedback_d: Sí, 5 es el único número impar en alist. Se duplica antes de ser colocado en blist.
   
   ¿Qué se imprime en las siguientes declaraciones?
   
   .. code-block:: python

     alist = [4,2,8,6,5]
     blist = [num*2 for num in alist if num%2==1]
     print(blist)

.. activecode:: ac21_4_4
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T

   **2.** El siguiente ciclo for produce una lista de números mayores que 10. Debajo del código dado, use list comprehension para lograr lo mismo. Asigne en la variable ``lst2``. Solo se necesita una línea de código.
   ~~~~

   L = [12, 34, 21, 4, 6, 9, 42]
   lst = []
   for x in L:
       if x > 10:
           lst.append(x)
   print(lst)

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testFourA(self):
         self.assertEqual(lst2, [12, 34, 21, 42], "Testing that lst2 is assigned to correct values")
         self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('sum(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('zip(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

   myTests().main()

.. activecode:: ac21_4_5
   :language: python
   :autograde: unittest
   :chatcodes:
   :practice: T

   **3.** Escriba el código para asignar a la variable ``compri`` todos los valores de la clave ``name`` en cualquiera de los sub-diccionarios del diccionario ``tester``. Haga esto usando list comprehension.
   ~~~~

   tester = {'info': [{"name": "Lauren", 'class standing': 'Junior', 'major': "Information Science"},{'name': 'Ayo', 'class standing': "Bachelor's", 'major': 'Information Science'}, {'name': 'Kathryn', 'class standing': 'Senior', 'major': 'Sociology'}, {'name': 'Nick', 'class standing': 'Junior', 'major': 'Computer Science'}, {'name': 'Gladys', 'class standing': 'Sophomore', 'major': 'History'}, {'name': 'Adam', 'major': 'Violin Performance', 'class standing': 'Senior'}]}


   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(sorted(compri), sorted(['Lauren', 'Ayo', 'Kathryn', 'Nick', 'Gladys', 'Adam']), "Testing that compri has the correct values.")
         self.assertNotIn('map(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('filter(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('sum(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")
         self.assertNotIn('zip(', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

   myTests().main()
