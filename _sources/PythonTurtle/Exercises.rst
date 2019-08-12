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
   :prefix: turtle-10-
   :start: 1

Ejercicios
----------

.. question:: turtle_ex_1
   :number: 1

   .. tabbed:: q1

        .. tab:: Question

           .. actex:: ac3_8_1

              Escribe un programa que imprima ``Nos gustan las tortugas de Python's!`` 100 veces.
              ~~~~

        .. tab:: Answer

            .. activecode::  answer3_8_1
                :nocanvas:

                for _ in range(100):
                    print("We like Python's turtles!")

        .. tab:: Discussion

            .. disqus::
                :shortname: interactivepython
                :identifier: f858d02024e54ae1b6b50ed8c65a01e6


.. question:: turtle_ex_2

   .. shortanswer:: turtle_reflect

      Los objetos de tortuga tienen métodos y atributos. Por ejemplo, una tortuga tiene una posición y cuando mueve la tortuga hacia adelante, la posición cambia. Piense en los otros métodos que se muestran en la página Resumen de métodos de tortuga. ¿A qué atributos, si corresponde, se relaciona cada método? ¿El método cambia el atributo?

.. question:: turtle_ex_3

   .. tabbed:: q3

        .. tab:: Question

           .. actex:: ac3_8_3
              :nocodelens:

              Use bucles ``for`` para hacer que una tortuga dibuje estos polígonos regulares
              (regular significa que todos los lados tienen la misma longitud, todos los ángulos iguales):

              * Un triángulo equilatero
              * Un cuadrado
              * Un hexágono (seis lados)
              * Un octágono (ocho lados)
              ~~~~

        .. tab:: Answer

            .. sourcecode:: python

                # draw an equilateral triangle
                import turtle

                wn = turtle.Screen()
                norvig = turtle.Turtle()

                for i in range(3):
                    norvig.forward(100)

                    # el ángulo de cada vértice de un polígono regular
                    # es 360 dividido por el número de lados
                    norvig.left(360/3)

                wn.exitonclick()

            .. sourcecode:: python

                # dibuja un cuadrado
                import turtle

                wn = turtle.Screen()
                kurzweil = turtle.Turtle()

                for i in range(4):
                    kurzweil.forward(100)
                    kurzweil.left(360/4)

                wn.exitonclick()

            .. sourcecode:: python

                # dibuja un hexágono
                import turtle

                wn = turtle.Screen()
                dijkstra = turtle.Turtle()

                for i in range(6):
                    dijkstra.forward(100)
                    dijkstra.left(360/6)

                wn.exitonclick()

            .. sourcecode:: python

                # dibujar un octágono
                import turtle

                wn = turtle.Screen()
                knuth = turtle.Turtle()

                for i in range(8):
                    knuth.forward(75)
                    knuth.left(360/8)

                wn.exitonclick()

        .. tab:: Discussion

            .. disqus::
                :shortname: interactivepython
                :identifier: f36e8bc742b89424e82f111ba2d1dd33f

.. question:: turtle_ex_4

   .. tabbed:: q4

        .. tab:: Question

           .. actex:: ac3_8_4
              :nocodelens:

              Escribe un programa para dibujar una forma como esta:

              .. image:: Figures/star.png
              ~~~~

        .. tab:: Answer

            .. activecode:: answer3_8_4
                :nocodelens:

                import turtle

                turing = turtle.Turtle()

                for i in range(5):
                    turing.forward(110)
                    turing.left(216)

        .. tab:: Discussion

            .. disqus::
                :shortname: interactivepython
                :identifier: c611217310057488aab6a34d4b591e753


.. question:: turtle_ex_5

   .. actex:: ac3_8_5
      :nocodelens:

      Escriba un programa para dibujar la esfera de un reloj que se parece a esto:

      .. image:: Figures/tess_clock1.png
      ~~~~

.. question:: turtle_ex_6

   .. tabbed:: q6

        .. tab:: Question

           .. actex:: ac3_8_6
              :nocodelens:

              Escribe un programa para dibujar algún tipo de imagen. Se creativo y experimenta
              con los métodos de tortuga.
              ~~~~

        .. tab:: Answer

            .. activecode:: answer3_8_6
                :nocodelens:

                import turtle

                tanenbaum = turtle.Turtle()

                tanenbaum.hideturtle()
                tanenbaum.speed(20)

                for i in range(350):
                    tanenbaum.forward(i)
                    tanenbaum.right(98)

        .. tab:: Discussion

            .. disqus::
                :shortname: interactivepython
                :identifier: e928a562a4f5c41f9892c9bfc4a1d5883

.. question:: turtle_ex_7

   .. actex:: ac3_8_7
      :nocodelens:

      Crea una tortuga y asígnela a una variable. Cuando imprime su tipo, ¿qué obtiene?
      ~~~~
