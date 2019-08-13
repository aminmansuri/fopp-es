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
   :prefix: iter-11-
   :start: 1

Ejercicios
==========


.. question:: q6_11_1

    .. actex:: ex6_11_1

        En el libro de Robert McCloskey's *Abran paso a los patitos*, los nombres de los patitos
        son Jack, Kack, Lack, Mack, Nack, Ouack, Pack y Quack. Este bucle intenta generar estos nombres en orden.

        Por supuesto, eso no está del todo bien porque Ouack y Quack están mal escritos.
        ¿Puedes arreglarlo?
        ~~~~

        prefixes = "JKLMNOPQ"
        suffix = "ack"

        for p in prefixes:
            print(p + suffix)


.. question:: q6_11_2

    .. actex:: ex6_11_2

        Haga que el usuario ingrese texto e imprímalo en orden inverso.
        ~~~~

.. question:: iter_ex_3

    .. tabbed:: q3

        .. tab:: Question


           .. actex:: ex_3_3

              Escriba un programa que use un bucle for para imprimir
                 |  ``Uno de los meses del año es Enero``
                 |  ``Uno de los meses del año es Febrero``
                 |  ``Uno de los meses del año es Marzo``
                 |  etc ...
              ~~~~

        .. tab:: Answer

            .. activecode:: q3_answer


                for amonth in ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'November', 'December']:
                    print("One of the months of the year is", amonth)

        .. tab:: Discussion

            .. disqus::
                :shortname: interactivepython
                :identifier: b271442ee0864973a023c19f27aeb401


.. question:: iter_ex_4


   .. actex:: ex_3_4

      Suponga que tiene una lista de números ``12, 10, 32, 3, 66, 17, 42, 99, 20``

      a. Escriba un bucle que imprima cada uno de los números en una nueva línea.
      b. Escriba un bucle que imprima cada número y su cuadrado en una nueva línea.
      ~~~~

.. question:: iter_ex_6

   .. actex:: ex_3_6
      :nocodelens:

      Escriba un programa que le solicite al usuario la cantidad de lados, la longitud del lado, el color y el color de relleno de un
      polígono regular. El programa debe dibujar el polígono y luego completarlo.
      ~~~~


.. question:: iter_ex_7

   .. tabbed:: q7

       .. tab:: Question

            .. actex:: ex_3_7
               :nocodelens:

               Un pirata borracho hace un giro al azar y luego da 100 pasos hacia adelante, da otro giro al azar, da otros 100 pasos, da otro giro al azar, etc. Un estudiante de ciencias sociales registra el ángulo de cada turno antes de dar los siguientes 100 pasos. Sus datos experimentales son ``160, -43, 270, -97, -43, 200, -940, 17, -86``. (Los ángulos positivos son en sentido antihorario). Usa una tortuga para dibujar el camino tomado por nuestro amigo borracho. Después de que el pirata termine de caminar, imprima el encabezado actual. Suponga que la tortuga originalmente tiene un encabezado de 0 y acumule los cambios en el encabezado para imprimir el final. Su solución debería funcionar para cualquier secuencia de datos experimentales.
               ~~~~

       .. tab:: Answer

           .. activecode:: iter_q7_answer
               :nocodelens:

               import turtle

               wn = turtle.Screen()
               lovelace = turtle.Turtle()

               # move the turtle forward a little so that the whole path fits on the screen
               lovelace.penup()
               lovelace.forward(60)

               # now draw the drunk pirate's path
               lovelace.pendown()
               current_heading = 0
               for angle in [160, -43, 270, -97, -43, 200, -940, 17, -86]:

                   # we use .left() so that positive angles are counter-clockwise
                   # and negative angles are clockwise
                   current_heading = (current_heading + angle) % 360
                   lovelace.left(angle)
                   lovelace.forward(100)

               # the .heading() method gives us the turtle's current heading in degrees
               print("The pirate's final heading was", current_heading)

               wn.exitonclick()

       .. tab:: Discussion

           .. disqus::
                :shortname: interactivepython
                :identifier: a7e34946f59f348f2bfeb3f918eb57b7a

.. question:: iter_ex_8

   .. parsonsprob:: pp_3_8

      Escriba un programa que revise una lista de temperaturas e imprímalas al usuario.
      -----
      temperatures = [-3, 78, 95, 28, 56, 42, 56, 81, -10, -]
      =====
      for temp in temperatures:
      =====
          print("The weather outside is: " + str(temp))

.. question:: iter_ex_9

   .. parsonsprob:: pp_3_9

      Escriba un programa que imprima un saludo a cada estudiante en la lista. Esta lista también debe hacer un seguimiento de cuántos estudiantes han sido recibidos y tener en cuenta que cada vez que un nuevo estudiante ha sido recibido.
      -----
      students = ["Jay", "Stacy", "Iman", "Trisha", "Ahmed", "Daniel", "Shadae", "Tosin", "Charlotte"]
      =====
      num_students = 0
      =====
      for student in students:
      =====
          print("Welcome to class, " + student)
      =====
          num_students += 1
          print(str(num_students) + "student(s) have entered the classroom")


