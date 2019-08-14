..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

:skipreading:`True`

.. qnum::
   :prefix: seqmut-13-
   :start: 1

Ejercicios
===========

#.

   .. tabbed:: q1

        .. tab:: Question

           .. actex:: ac8_11_1

              Para cada palabra en la lista ``verbs``, agregue una terminación -ing. Sobrescriba la lista anterior para que ``verbs`` tenga las mismas palabras con ``ing`` al final de cada uno.
              ~~~~
              verbs = ["kayak", "cry", "walk", "eat", "drink", "fly"]

              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testSeven(self):
                      self.assertEqual(verbs, ['kayaking', 'crying', 'walking', 'eating', 'drinking', 'flying'], "Testing that verbs is assigned to correct values.")

              myTests().main()


#.

   .. tabbed:: q2

        .. tab:: Question

           .. actex:: ac8_11_2

              En la Universidad XYZ, las clases de matemáticas de nivel superior están numeradas de 300 en adelante. Las clases de inglés de nivel superior están numeradas de 200 en adelante. Las clases de psicología de nivel superior son 400 y más. Cree dos listas, ``upper`` y ``lower``. Asigne cada curso en ``classes`` a la lista correcta, ``upper`` o ``lower``. SUGERENCIA: recuerde, ¡puede convertir algunas cadenas a diferentes tipos!
              ~~~~
              classes = ["MATH 150", "PSYCH 111", "PSYCH 313", "PSYCH 412", "MATH 300", "MATH 404", "MATH 206", "ENG 100", "ENG 103", "ENG 201", "PSYCH 508", "ENG 220", "ENG 125", "ENG 124"]

              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testEightA(self):
                      self.assertEqual(upper, ['PSYCH 412', 'MATH 300', 'MATH 404', 'ENG 201', 'PSYCH 508', 'ENG 220'], "Testing that the upper list exists and contains the correct elements.")
              def testEightB(self):
                      self.assertEqual(lower, ['MATH 150', 'PSYCH 111', 'PSYCH 313', 'MATH 206', 'ENG 100', 'ENG 103', 'ENG 125', 'ENG 124'], "Testing that the lower list exists and contains the correct elements.")

              myTests().main()

#.

   .. tabbed:: q3

        .. tab:: Question

           .. actex:: ac8_11_3

              Comenzando con la lista myList = [76, 92.3, 'hello', True, 4, 76], escriba sentencias de Python para hacer lo siguiente:
   
              a. Agregue "apple" y 76 a la lista.
              #. Inserte el valor "cat" en la posición 3.
              #. Inserte el valor 99 al inicio de la lista.
              #. Encuentre el índice de "hello".
              #. Cuente el número de 76 que hay en la lista.
              #. Remueva de la lista la primera ocurrencia de 76.
              #. Remueva True de la lista usando ``pop`` and ``index``.
              ~~~~
              myList = [76, 92.3, 'hello', True, 4, 76]

              # Your code here

        .. tab:: Answer

           .. activecode:: answer8_11_3

              myList = [76, 92.3, 'hello', True, 4, 76]

              myList.append("apple")         # a
              myList.append(76)              # a
              myList.insert(3, "cat")        # b
              myList.insert(0, 99)           # c

              print(myList.index("hello"))   # d
              print(myList.count(76))        # e
              myList.remove(76)              # f
              myList.pop(myList.index(True)) # g

              print (myList)

        .. tab:: Discussion

            .. disqus::
                :shortname: interactivepython
                :identifier: disqus_b9034b274ebe4c55a58c44315ee681a4


#.  .. tabbed:: q4

        .. tab:: Question
           
           .. activecode:: ac13_5_3

              El módulo ``keyword`` determina si una cadena es una palabra clave. por ejemplo. ``keyword.iskeyword(s)`` donde ``s`` es una cadena devolverá ``True`` o ``False``, dependiendo de si la cadena es o no una palabra clave de Python. Importe el módulo ``palabra clave`` y pruebe para ver si cada una de las palabras en la lista ``prueba`` son palabras clave. Guarde las respuestas respectivas en una lista, ``keyword_test``.
              ~~~~

              test = ["else", "integer", "except", "elif"]
              keyword_test = []

              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                 def testOneA(self):
                    self.assertEqual(keyword_test, [True, False, True, True], "Testing that keyword_test is correct and p1 assigned to correct values")
      
              myTests().main()



#.  .. tabbed:: q5

        .. tab:: Question
           
           .. activecode:: ac13_5_4

              El módulo ``cadena`` proporciona secuencias de varios tipos de caracteres Python. Tiene un atributo llamado ``dígitos`` que produce la cadena '0123456789'. Importe el módulo y asigne esta cadena a la variable ``nums``. A continuación, proporcionamos una lista de caracteres llamados ``caracteres``. Usando ``nums`` y ``chars``, produzca una lista llamada ``is_num`` que consta de tuplas. El primer elemento de cada tupla debe ser el carácter de ``caracteres``, y el segundo elemento debe ser un booleano que refleje si es o no un dígito de Python.
              ~~~~

              chars = ['h', '1', 'C', 'i', '9', 'True', '3.1', '8', 'F', '4', 'j']

              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                 def testOneA(self):
                    self.assertEqual(is_num, [('h', False), ('1', True), ('C', False), ('i', False), ('9', True), ('True', False), ('3.1', False), ('8', True), ('F', False), ('4', True), ('j', False)], "Testing that is_num was created correctly.")
      
              myTests().main()
