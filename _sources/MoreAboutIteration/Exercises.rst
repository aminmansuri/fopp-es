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
   :prefix: moreiter-9-
   :start: 1

Ejercicios
----------


.. question:: moreiter_ex_1
   :number: 1

   .. tabbed:: q1

        .. tab:: Question

           .. actex:: ac14_9_1

              **1.** Usando un ciclo while, cree una lista de ``numbers`` que contenga los números del 0 al 35. Su ciclo while debe inicializar una variable de contador a 0. En cada iteración, el ciclo debe agregar el valor actual del contador a la lista y el contador debe aumentar en 1. El ciclo while debe detenerse cuando el contador es mayor que 35.
              ~~~~


              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                 def testOne(self):
                    self.assertEqual(numbers, [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35], "Testing that numbers is assigned to correct values")

              myTests().main()

        .. tab:: Discussion

            .. disqus::
                :shortname: interactivepython
                :identifier: disqus_5784e08291ba43199d43fdab277849f5


.. question:: moreiter_ex_2

   .. actex:: ac14_9_2

      Usando un ciclo while, cree una lista llamada ``L`` que contenga los números del 0 al 10. (es decir: su ciclo while debe inicializar una variable de contador a 0. En cada iteración, el ciclo debe agregar el valor actual del contador variable a ``L`` y luego aumente el contador en 1. El ciclo while debe detenerse una vez que la variable del contador sea mayor que 10.)
      ~~~~

      =====

      from unittest.gui import TestCaseGui
 
      class myTests(TestCaseGui):
 
         def testOne(self):
            self.assertEqual(L, [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10], "Testing that L was created correctly.")

      myTests().main()

.. question:: moreiter_ex_3

   .. tabbed:: q3

        .. tab:: Question

           .. actex:: ac14_9_3

              Usando un bucle while, cree una lista llamada ``nums`` que contenga los números del 0 al 20. (es decir: su bucle while debe inicializar una variable de contador en 0. Durante cada iteración, el bucle debe agregar el valor actual del contador variable a ``nums`` y luego aumentar el contador en 1. El ciclo while debe detenerse una vez que la variable del contador sea mayor que 20)
              ~~~~

              ====
              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(nums, [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20],"Testing that nums has been assigned the correct elements")

              myTests().main()

.. question:: moreiter_ex_4

    .. actex:: ac14_9_4
       :nocodelens:

       Modifique el programa turtle caminando para que, en lugar de girar 90 grados a la izquierda o derecha,
       el ángulo de giro se determine aleatoriamente en cada paso.
       ~~~~


.. question:: moreiter_ex_5

   .. tabbed:: q5

        .. tab:: Question

           .. actex:: ac14_9_5
              :nocodelens:

              Modifique el programa two turtles each para que tenga dos turtles cada una con un
              ubicación inicial aleatoria. Mantén a las turtles en movimiento hasta que una de ellas salga de la pantalla.
              ~~~~

        .. tab:: Answer

            .. activecode:: q5_answer
                :nocodelens:

                import random
                import turtle

                def moveRandom(wn, t):
                    coin = random.randrange(0,2)
                    if coin == 0:
                        t.left(90)
                    else:
                        t.right(90)

                    t.forward(50)

                def areColliding(t1, t2):
                    if t1.distance(t2) < 2:
                        return True
                    else:
                        return False

                def isInScreen(w, t):
                    leftBound = - w.window_width() / 2
                    rightBound = w.window_width() / 2
                    topBound = w.window_height() / 2
                    bottomBound = -w.window_height() / 2

                    turtleX = t.xcor()
                    turtleY = t.ycor()

                    stillIn = True
                    if turtleX > rightBound or turtleX < leftBound:
                        stillIn = False
                    if turtleY > topBound or turtleY < bottomBound:
                        stillIn = False
                    return stillIn

                t1 = turtle.Turtle()
                t2 = turtle.Turtle()
                wn = turtle.Screen()

                t1.shape('turtle')
                t2.shape('circle')

                leftBound = -wn.window_width() / 2
                rightBound = wn.window_width() / 2
                topBound = wn.window_height() / 2
                bottomBound = -wn.window_height() / 2

                t1.up()
                t1.goto(random.randrange(leftBound, rightBound),
                        random.randrange(bottomBound, topBound))
                t1.setheading(random.randrange(0, 360))
                t1.down()

                t2.up()
                t2.goto(random.randrange(leftBound, rightBound),
                        random.randrange(bottomBound, topBound))
                t2.setheading(random.randrange(0, 360))
                t2.down()


                while isInScreen(wn, t1) and isInScreen(wn, t2):
                    moveRandom(wn, t1)
                    moveRandom(wn, t2)

                wn.exitonclick()

        .. tab:: Discussion

            .. disqus::
                :shortname: interactivepython
                :identifier: disqus_0cd01637a1814f86b11f576c37a46437


.. question:: moreiter_ex_6

   .. actex:: ac14_9_6
      :nocodelens:

      Cree un ciclo while que inicialice un contador en 0 y se ejecutará hasta que el contador alcance 50. Si el valor del contador es divisible por 10, agregue el valor a la lista, ``tens``.
      ~~~~

      =====

      from unittest.gui import TestCaseGui

      class myTests(TestCaseGui):

         def testTwo(self):
            self.assertEqual(tens, [0, 10, 20, 30, 40, 50], "Testing that tens is assigned to correct values.")

      myTests().main()

.. question:: moreiter_ex_7

   .. actex:: ac14_9_7
      :nocodelens:

      Use un bucle while para recorrer los números del 0 al 35. Si un número es divisible por 3, debe agregarse a una lista llamada ``three_nums``.
      ~~~~

      =====

      from unittest.gui import TestCaseGui

      class myTests(TestCaseGui):

         def testOne(self):
            self.assertEqual(three_nums, [0, 3, 6, 9, 12, 15, 18, 21, 24, 27, 30, 33], "Testing that three_nums was created correctly.")

      myTests().main()
