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
   :prefix: func-14-
   :start: 1

Ejercicios
=============
#.

    .. tabbed:: q1

        .. tab:: Question

           .. actex:: ac11_14_1

              Escriba una función llamada ``num_test`` que tome un número como entrada. Si el número es mayor que 10, la función debería devolver "Greater than 10". Si el número es menor que 10, la función debería devolver "Less than 10.". Si el número es igual a 10, la función debería devolver "Equal to 10."
              ~~~~
              

              ====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                def testOne(self):
                    self.assertEqual(num_test(5), "Less than 10.", "Testing the num_test function on input 5.")
                    self.assertEqual(num_test(0), "Less than 10.", "Testing the num_test function on input 0.")
                    self.assertEqual(num_test(12.99), "Greater than 10.", "Testing the num_test function on input 12.99.")
                    self.assertEqual(num_test(10.00), "Equal to 10.", "Testing the num_test function on input 10.00.")



              myTests().main()

#.

    .. tabbed:: q2

        .. tab:: Question

           .. actex:: ac11_14_2

              Escriba una función que devolverá el número de dígitos en un entero.
              ~~~~
              def numDigits(n):
                  # su código aquí

              ====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                def testOne(self):
                    self.assertEqual(numDigits(2),1,"Tested numDigits on input of 2")
                    self.assertEqual(numDigits(55),2,"Tested numDigits on input of 55")
                    self.assertEqual(numDigits(1352),4,"Tested numDigits on input of 1352")
                    self.assertEqual(numDigits(444),3,"Tested numDigits on input of 444")



              myTests().main()


        .. tab:: Answer

            .. activecode:: answer11_14_2

                def numDigits(n):
                    n_str = str(n)
                    return len(n_str)


                print(numDigits(50))
                print(numDigits(20000))
                print(numDigits(1))

        .. tab:: Discussion

            .. disqus::
                :shortname: interactivepython
                :identifier: disqus_bfd6f74a183c4682b29c72c4411200fb


#.

    .. tabbed:: q3

        .. tab:: Question 

           .. actex:: ac11_14_3
      
              Escriba una función que invierta el argumento de un string.
              ~~~~
              def reverse(astring):
                  # your code here

              ====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(reverse("happy"),"yppah","Tested reverse on input of 'happy'")
                      self.assertEqual(reverse("Python"),"nohtyP","Tested reverse on input of 'Python'")
                      self.assertEqual(reverse(""),"","Tested reverse on input of ''")




              myTests().main()

#.

    .. tabbed:: q4

        .. tab:: Question

           .. actex:: ac11_14_4
              :nocodelens:

              Escriba una función que refleje su argumento de string para
              generar un string que contiene el string original y el string anterior hacia atrás.
              ~~~~

              def mirror(mystr):
                  # su código aquí

              ====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(mirror("good"),"gooddoog","Tested mirror on input of 'good'")
                      self.assertEqual(mirror("Python"),"PythonnohtyP","Tested mirror on input of 'Python'")
                      self.assertEqual(mirror(""),"","Tested mirror on input of ''")
                      self.assertEqual(mirror("a"),"aa","Tested mirror on input of 'a'")


              myTests().main()



        .. tab:: Answer

            .. activecode:: answer11_14_4
                :nocodelens:

                from test import testEqual

                def reverse(mystr):
                    reversed = ''
                    for char in mystr:
                        reversed = char + reversed
                    return reversed

                def mirror(mystr):
                    return mystr + reverse(mystr)

                testEqual(mirror('good'), 'gooddoog')
                testEqual(mirror('Python'), 'PythonnohtyP')
                testEqual(mirror(''), '')
                testEqual(mirror('a'), 'aa')

        .. tab:: Discussion

            .. disqus::
                :shortname: interactivepython
                :identifier: disqus_70b7ac515456497c952a2de5caa27ab9

#.

    .. tabbed:: q5

        .. tab:: Question 

           .. actex:: ac11_14_5
              :nocodelens:

              Escriba una función que elimine todas las apariciones de una letra dada de una cadena.
              ~~~~
              def remove_letter(theLetter, theString):
                  # su código aquí

              ====


              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(remove_letter("a","apple"),"pple","Tested remove_letter on inputs of 'a' and 'apple'")
                      self.assertEqual(remove_letter("a","banana"),"bnn","Tested remove_letter on inputs of 'a' and 'banana'")
                      self.assertEqual(remove_letter("z","banana"),"banana","Tested remove_letter on inputs of 'z' and 'banana'")



              myTests().main()


#.

   .. tabbed:: q6

        .. tab:: Question

           .. actex:: ac11_14_6

              Aunque Python nos proporciona muchos métodos de lista, es una buena práctica y muy instructivo pensar cómo se implementan. Implemente una función de Python que funcione de la siguiente manera:
   
              a. count
              #. in
              #. reverse
              #. index
              #. insert
              ~~~~ 

        .. tab:: Answer

            .. activecode:: answer11_14_6

                def count(obj, lst):
                    count = 0
                    for e in lst:
                        if e == obj:
                            count = count + 1
                    return count

                def is_in(obj, lst):  # cannot be called in() because in is a reserved keyword
                    for e in lst:
                        if e == obj:
                            return True
                    return False

                def reverse(lst):
                    reversed = []
                    for i in range(len(lst)-1, -1, -1): # step through the original list backwards
                        reversed.append(lst[i])
                    return reversed

                def index(obj, lst):
                    for i in range(len(lst)):
                        if lst[i] == obj:
                            return i
                    return -1

                def insert(obj, index, lst):
                    newlst = []
                    for i in range(len(lst)):
                        if i == index:
                            newlst.append(obj)
                        newlst.append(lst[i])
                    return newlst

                lst = [0, 1, 1, 2, 2, 3, 4, 5, 6, 7, 8, 9]
                print(count(1, lst))
                print(is_in(4, lst))
                print(reverse(lst))
                print(index(2, lst))
                print(insert('cat', 4, lst))

        .. tab:: Discussion

            .. disqus::
                :shortname: interactivepython
                :identifier: disqus_39ee0274e51d4c888cc20b6fefa4069c

#.

    .. tabbed:: q7

        .. tab:: Question 

           .. actex:: ac11_14_7

              Escriba una función ``replace(s, old, new)`` que reemplaza todas las ocurrencias de
              ``old`` con ``new`` en un string ``s``::
   
                 test(replace('Mississippi', 'i', 'I'), 'MIssIssIppI')
   
                 s = 'I love spom!  Spom is my favorite food.  Spom, spom, spom, yum!'
                 test(replace(s, 'om', 'am'), 
                        'I love spam!  Spam is my favorite food.  Spam, spam, spam, yum!')
   
                 test(replace(s, 'o', 'a'), 
                        'I lave spam!  Spam is my favarite faad.  Spam, spam, spam, yum!')
   
              *Hint*: use los métodos de ``split`` y ``join``.
              ~~~~
              def replace(s, old, new):
                  # su código aquí

              ====
              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(replace('Mississippi','i','I'),'MIssIssIppI',"Tested replace on input 'Mississippi','i','I'")
                      self.assertEqual(replace('Bookkeeper','e','A'),'BookkAApAr',"Tested failed on input 'Bookkeeper','e','A'")
                      self.assertEqual(replace('Deeded','e','q'),'Dqqdqd',"Tested failed on input 'Deeded','e','q'")

              myTests().main()

#.

   .. tabbed:: q8

        .. tab:: Question

           .. actex:: ac11_14_8

              Escriba una función de Python que tomará una lista de 100 enteros aleatorios entre 0 y 1000 y devolverá el valor máximo. (Nota: hay una función incorporada llamada ``max`` pero finge que no puedes usarla)
              ~~~~


        .. tab:: Answer

            .. activecode:: answer11_14_8

                import random

                def max(lst):
                    max = 0
                    for e in lst:
                        if e > max:
                            max = e
                    return max

                lst = []
                for i in range(100):
                    lst.append(random.randint(0, 1000))

                print(max(lst))

        .. tab:: Discussion

            .. disqus::
                :shortname: interactivepython
                :identifier: disqus_714fd5537ebf41189ce5fb6fb16d1d26

#.

   .. tabbed:: q9

        .. tab:: Question

           .. actex:: ac11_14_9

              Escriba una función ``sum_of_squares(xs)`` que calcule la suma
              de los cuadrados de los números en la lista ``xs``. Por ejemplo,
              ``sum_of_squares([2, 3, 4])`` debería devolver 4+9+16, que es 29:
              ~~~~   
              def sum_of_squares(xs):
                  # su código aquí

              ====
              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(sum_of_squares([2,3,4]),29,"Tested sum_of_squares on input [2,3,4]")
                      self.assertEqual(sum_of_squares([0,1,-1]),2,"Tested sum_of_squares on input [0,1,-1]")
                      self.assertEqual(sum_of_squares([5,12,14]),365,"Tested sum_of_squares on input [5,12,14]")

              myTests().main()

#.

   .. tabbed:: q10

        .. tab:: Question

           .. actex:: ac11_14_10

              Escriba una función para contar cuántos números impares hay en una lista.
              ~~~~
              def countOdd(lst):
                  # su código aquí

              ====
              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(countOdd([1,3,5,7,9]),5,"Tested countOdd on input [1,3,5,7,9]")
                      self.assertEqual(countOdd([1,2,3,4,5]),3,"Tested countOdd on input [-1,-2,-3,-4,-5]")
                      self.assertEqual(countOdd([2,4,6,8,10]),0,"Tested countOdd on input [2,4,6,8,10]")
                      self.assertEqual(countOdd([0,-1,12,-33]),2,"Tested countOdd on input [0,-1,12,-33]")

              myTests().main()



        .. tab:: Answer

            .. activecode:: answer11_14_10

                import random

                def countOdd(lst):
                    odd = 0
                    for e in lst:
                        if e % 2 != 0:
                            odd = odd + 1
                    return odd

                # hacer una lista aleatoria para probar la función
                lst = []
                for i in range(100):
                    lst.append(random.randint(0, 1000))

                print(countOdd(lst))

        .. tab:: Discussion

            .. disqus::
                :shortname: interactivepython
                :identifier: disqus_fdd366b1b4c8494082a385e1e1197844


#.

   .. tabbed:: q11

        .. tab:: Question

           .. actex:: ac11_14_11

              Resume todos los números pares en una lista.
              ~~~~
              def sumEven(lst):
                  # su código aquí

              ====
              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

              def testOne(self):
                  self.assertEqual(sumEven([1,3,5,7,9]),0,"Tested sumEven on input [1,3,5,7,9]")
                  self.assertEqual(sumEven([-1,-2,-3,-4,-5]),-6,"Tested sumEven on input [-1,-2,-3,-4,-5]")
                  self.assertEqual(sumEven([2,4,6,7,9]),12,"Tested sumEven on input [2,4,6,7,9]")
                  self.assertEqual(sumEven([0,1,12,33]),12,"Tested sumEven on input [0,1,12,33]")

              myTests().main()

#.

   .. tabbed:: q12

        .. tab:: Question

           .. actex:: ac11_14_12

              Resume todos los números negativos en una lista.
              ~~~~
              def sumNegatives(lst):
                  # su código aquí

              ====
              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(sumNegatives([-1,-2,-3,-4,-5]),-15,"Tested sumNegatives on input [-1,-2,-3,-4,-5]")
                      self.assertEqual(sumNegatives([1,-3,5,-7,9]),-10,"Tested sumNegatives on input [1,-3,5,-7,9]")
                      self.assertEqual(sumNegatives([-2,-4,6,-7,9]),-13,"Tested sumNegatives on input [-2,-4,6,-7,9]")
                      self.assertEqual(sumNegatives([0,1,2,3,4]),0,"Tested sumNegatives on input [0,1,2,3,4]")

              myTests().main()



        .. tab:: Answer

            .. activecode:: answer11_14_12

                import random

                def sumNegative(lst):
                    sum = 0
                    for e in lst:
                        if e < 0:
                            sum = sum + e
                    return sum

                lst = []
                for i in range(100):
                    lst.append(random.randrange(-1000, 1000))

                print(sumNegative(lst))

        .. tab:: Discussion

            .. disqus::
                :shortname: interactivepython
                :identifier: disqus_bfe671ac1e0942f2be4de7179921f83f

#.

    .. tabbed:: q13

        .. tab:: Question

            .. actex:: ac11_14_13
                :nocodelens:

                Escribe una función ``findHypot``. La función tendrá la longitud de dos lados de un triángulo rectángulo y debe devolver la longitud de la hipotenusa. (Sugerencia:  ``x ** 0.5`` devolverá la raíz cuadrada, o usará ``sqrt`` del módulo matemático)
                ~~~~

                def findHypot(a,b):
                    # su código aquí

                ====

                from unittest.gui import TestCaseGui

                class myTests(TestCaseGui):
                    def testOne(self):
                        self.assertEqual(findHypot(12.0,5.0),13.0,"Tested findHypot on inputs of 12.0 and 5.0")
                        self.assertEqual(findHypot(14.0,48.0),50.0,"Tested findHypot on inputs of 14.0 and 48.0")
                        self.assertEqual(findHypot(21.0,72.0),75.0,"Tested findHypot on inputs of 21.0 and 72.0")
                        self.assertAlmostEqual(findHypot(1,1.73205),1.999999,2,"Tested findHypot on inputs of 1 and 1.73205")

                myTests().main()

#.
   .. tabbed:: q14

        .. tab:: Question

           .. actex:: ac11_14_14
               :nocodelens:

               Escriba una función llamada ``is_even(n)`` que toma un número entero como argumento y devuelve ``True`` si el argumento es un **número par** y ``False`` si es **impar**.
               ~~~~
               def is_even(n):
                   # su código aquí

               ====

               from unittest.gui import TestCaseGui

               class myTests(TestCaseGui):
                    def testOne(self):
                        self.assertEqual(is_even(10),True,"Tested is_even on input of 10")
                        self.assertEqual(is_even(5),False,"Tested is_even on input of 5")
                        self.assertEqual(is_even(1),False,"Tested is_even on input of 1")
                        self.assertEqual(is_even(0),True,"Tested is_even on input of 0")

               myTests().main()

#.
   .. tabbed:: q15

        .. tab:: Question

           .. actex:: ac11_14_15
               :nocodelens:

               Ahora escriba la función ``is_odd(n)`` que devuelve ``True`` cuando ``n`` es impar y ``False`` de lo contrario.
               ~~~~

               def is_odd(n):
                   # su código aquí


               ====
               from unittest.gui import TestCaseGui

               class myTests(TestCaseGui):
                   def testOne(self):
                       self.assertEqual(is_odd(10),False,"Tested is_odd on input of 10")
                       self.assertEqual(is_odd(5),True,"Tested is_odd on input of 5")
                       self.assertEqual(is_odd(1),True,"Tested is_odd on input of 1")
                       self.assertEqual(is_odd(0),False,"Tested is_odd on input of 0")

               myTests().main()



#.
   .. tabbed:: q16

        .. tab:: Question

           .. actex:: ac11_14_16

               Escriba una función ``is_rightangled`` que, dada la longitud de tres lados de un triángulo, determinará si el triángulo está en ángulo recto. Suponga que el tercer argumento de la función es siempre el lado más largo. Devolverá ``True`` si el triángulo está en ángulo recto, o ``False`` de lo contrario.

               Sugerencia: la aritmética de coma flotante no siempre es exactamente precisa,
               por lo tanto, no es seguro probar los números de coma flotante para determinar la igualdad.
               Si un buen programador quiere saber si
               ``x`` es igual o lo suficientemente cerca de ``y``, probablemente lo codificarían como:
   
               .. sourcecode:: python
   
                   if  abs(x - y) < 0.001:      # si x es aproximadamente igual a y
                       ...

               ~~~~
               def is_rightangled(a, b, c):
                   # su código aquí


               ====
               from unittest.gui import TestCaseGui

               class myTests(TestCaseGui):
                   def testOne(self):
                       self.assertEqual(is_rightangled(1.5,2.0,2.5),True,"Tested is_rightangled on inputs of 1.5, 2.0 and 2.5")
                       self.assertEqual(is_rightangled(4.0,8.0,16.0),False,"Tested is_rightangled on inputs of 4.0, 8.0 and 16.0")
                       self.assertEqual(is_rightangled(4.1,8.2,9.1678787077),True,"Tested is_rightangled on inputs of 4.1, 8.2 and 9.1678787077")
                       self.assertEqual(is_rightangled(4.1,8.2,9.16787),True,"Tested is_rightangled on inputs of 4.1, 8.2, and 9.16787")
                       self.assertEqual(is_rightangled(4.1,8.2,9.168),False,"Tested is_rightangled on inputs of 4.1, 8.2 and 9.168")
                       self.assertEqual(is_rightangled(0.5,0.4,0.64031),True,"Tested is_rightangled on inputs of 0.5, 0.4 and 0.64031")

               myTests().main()
