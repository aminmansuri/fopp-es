..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-18-
   :start: 1

Ejercicios
-------------
.. question:: spd_ex_1
   :number: 1

   .. tabbed:: q1

        .. tab:: Pregunta

            .. activecode:: ch02_ex1

               Evalúa las siguientes expresiones numéricas en tu cabeza, luego usa
               la ventana de código activo para verificar sus resultados:

               #. ``5 ** 2``
               #. ``9 * 5``
               #. ``15 / 12``
               #. ``12 / 15``
               #. ``15 // 12``
               #. ``12 // 15``
               #. ``5 % 2``
               #. ``9 % 5``
               #. ``15 % 12``
               #. ``12 % 15``
               #. ``6 % 6``
               #. ``0 % 7``
               ~~~~

               print(5**2)
        
        .. tab:: Respuesta

            #. ``5 ** 2  = 25``
            #. ``9 * 5 = 45``
            #. ``15 / 12 = 1.25``
            #. ``12 / 15 = 0.8``
            #. ``15 // 12 = 1``
            #. ``12 // 15 = 0``
            #. ``5 % 2 = 1``
            #. ``9 % 5 = 4``
            #. ``15 % 12 = 3``
            #. ``12 % 15 = 12``
            #. ``6 % 6 = 0``
            #. ``0 % 7 = 0``

        .. tab:: Debate

            .. disqus::
                :shortname: interactivepython
                :identifier: c0a62044cac248859ce3695b46697ecc

.. question:: spd_ex_2

   .. actex:: ex_2_2

      ¿Cuál es el orden de las operaciones aritméticas en la siguiente expresión? Evalúa la expresión a mano y luego verifica tu trabajo.
      ~~~~
      2 + (3 - 1) * 10 / 5 * (2 + 3)

.. question:: spd_ex_5

    .. tabbed:: q5

        .. tab:: Pregunta

            .. actex:: ex_2_5
        
               Opcional. Muchas personas pasan la hora usando un reloj de 24 horas (11 son las 11 a.m. y 23 son las 11 p.m., 0 es medianoche).
               Si actualmente son las 13 y configuras la alarma para que suene en 50 horas, serán las 15 (3pm).
               Escriba un programa de Python para resolver la versión general del problema anterior.
               Solicite al usuario el tiempo ahora (en horas) y luego solicite la cantidad de horas que esperará la alarma.
               Su programa debería mostrar la hora del reloj cuando suena la alarma.
               ~~~~

        .. tab:: Respuesta
            
            .. activecode:: spd_q5_answer
                :nocanvas:
                
                ## question 5 solution ##

                current_time_string = input("What is the current time (in hours)? ")
                waiting_time_string = input("How many hours do you have to wait? ")

                current_time_int = int(current_time_string)
                waiting_time_int = int(waiting_time_string)

                hours = current_time_int + waiting_time_int

                timeofday = hours % 24

                print(timeofday)

.. question:: spd_ex_6

   .. actex:: ex_2_6

       Es posible nombrar los días 0 a 6, donde el día 0 es domingo y el día 6 es sábado.
       Si te vas de maravillosas vacaciones saliendo el día número 3 (un miércoles) y regresas
       después de 10 noches en casa, regresarías a casa un sábado (día 6). Escriba un versión
       general del programa que solicita el número del día de inicio y la duración de su
       estadía y le indicará la cantidad de días de la semana en que volverá.
       ~~~~


.. question:: spd_ex_7

    .. tabbed:: q7

        .. tab:: Pregunta

            Opcional. Tome la oración: *Todo el trabajo y nada de juego hacen que Jack sea un niño aburrido.*
            Almacene cada palabra en una variable separada, luego imprima la oración en
            una línea usando ``print``.

            .. actex:: ex_2_7

        .. tab:: Respuesta

            .. activecode:: spd_q7_answer    
                :nocanvas:

                ## Solución a la pregunta 7 ##

                word1 = "Todo"
                word2 = "el"
                word3 = "trabajo"
                word4 = "y"
                word5 = "nada"
                word6 = "de"
                word7 = "juegos"
                word8 = "hacen"
                word9 = "que"
                word10 = "Jack"
                word11 = "sea"
                word12 = "un"
                word13 = "niño"
                word14 = "aburrido"

                print(word1 + ' ' +  word2 + ' ' + word3 + ' ' +  word4 + ' ' +  word5 + ' ' +  word6 + ' ' +  word7 + ' ' +  word8 + ' ' +  word9 + ' ' +  word10+ ' ' +  word11 + ' ' +  word12+ ' ' +  word13 + ' ' +  word14)


.. question:: spd_ex_8

   .. actex:: ex_2_8

      Agregue paréntesis a la expresión ``6 * 1 - 2`` para cambiar su valor de 4 a -6.
      ~~~~

      print(6 * 1 -2)

  
.. question:: spd_ex_9

    .. tabbed:: q9

        .. tab:: Pregunta

            .. actex:: ex_2_9

                Opcional. La fórmula para calcular la cantidad final si se gana
                el interés compuesto se da en Wikipedia como

                .. image:: Figures/compoundInterest.png
                   :alt: formula for compound interest

                Escriba un programa de Python que asigne la cantidad principal de 10000 a
                variable ``P``, asigne a ``n`` el valor 12 y asigne a ``r`` el interés
                tasa del 8% (0.08). Luego haga que el programa solicite al usuario la cantidad de años,
                ``t``, que el dinero se agravará. Calcule e imprima el final
                cantidad después de ``t`` años.
                ~~~~
            
                P = 10000
                n = 12
                r = 0.08

                t = ??
                
        .. tab:: Respuesta

            .. activecode:: spd_q9_answer
                :nocanvas:

                ## solución a la pregunta 9 ##

                P = 10000
                n = 12
                r = 0.08

                t = int(input("Por cuántos años está compuesto? "))

                final = P * ( ((1 + (r/n)) ** (n * t)) )

                print("La cantidad final después de ", t, " años es", final)

    
.. question:: spd_ex_10

   .. actex:: ex_2_10

      Escribe un programa que calcule el área de un círculo. Solicite al usuario que ingrese el radio e imprima un mensaje agradable al usuario con la respuesta.
      ~~~~

  
.. question:: spd_ex_11

    .. tabbed:: q11

        .. tab:: Pregunta

            .. actex:: ex_2_11

               Opcional. Escribe un programa que calcule el área de un rectángulo. Solicite al usuario que ingrese el ancho y la altura del rectángulo.
               Imprime un bonito mensaje con la respuesta.
               ~~~~
        
        .. tab:: Respuesta

            .. activecode:: spd_q11_answer
                :nocanvas:        

                ## Solución el ejercicio 9

                width = int(input("Ancho? "))
                height = int(input("Altot? "))

                area = width * height

                print("El área del rectángulo es", area)


.. question:: spd_ex_12

   .. actex:: ex_2_12

      Escriba un programa que calcule MPG para un automóvil. Solicitar al usuario que ingrese el número de
      millas recorridas y la cantidad de galones utilizados. Imprime un bonito mensaje con la respuesta.
      ~~~~

  
.. question:: spd_ex_13

    .. tabbed:: q13

        .. tab:: Pregunta

            .. actex:: ex_2_13

               Opcional. Escriba un programa que convierta grados centígrados a grados fahrenheit.
               ~~~~
        
        .. tab:: Respuesta

            .. activecode:: spd_q13_answer
                :nocanvas:

                ## solución al ejercicio 13 ##

                deg_c = int(input("¿Cuál es la temperatura en grados Celsius? "))

                # formula to convert C to F is: (degrees Celcius) times (9/5) plus (32)
                deg_f = deg_c * (9 / 5) + 32

                print(deg_c, " en grados Celsius es ", deg_f, ", grados Fahrenheit.")

        .. tab:: Proceso

            .. disqus::
                :shortname: interactivepython
                :identifier: c4a929d598ab4c46b484f6abbcec2655

.. question:: spd_ex_14

   .. actex:: ex_2_14

      Opcional. Escriba un programa que convierta grados Fahrenheit a grados Celsius.
      ~~~~

.. question:: spd_ex_15

   .. parsonsprob:: pp_2_15
      :noindent:

      Reúna el código para que se le pidan dos números a un usuario, y luego se imprima la suma de esos dos números.
      -----
      num_one = input("Por favor ingrese su primer número: ")
      =====
      num_two = input("Por favor ingrese su segundo número: ")
      =====
      sum_of_input = int(num_one) + int(num_two)
      =====
      print(sum_of_input)

.. question:: spd_ex_16

   .. parsonsprob:: pp_2_16
      :noindent:

      Escriba un programa que convierta galones a litros. Este programa también necesitará recibir información de un usuario para ver cuántos galones se deben convertir y el resultado se debe imprimir al usuario.
      -----
      user_gallons = input("¿Cuántos galones se deben convertir ?: ")
      =====
      num_gallons = int(user_gallons)
      =====
      liters = num_gallons * 3.785
      =====
      print("Numero de litros: " + str(liters))


.. question:: spd_ex_17

   .. parsonsprob:: pp_2_17
      :noindent:

      Escriba un programa que convierta las cucharadas de mesa en cucharaditas. Este programa también necesitará la entrada de un usuario para ver cuántas cucharadas se deben convertir y el resultado se debe imprimir al usuario.
      -----
      user_tablespoons = float(input("¿Cuántas cucharadas se deben convertir?: "))
      =====
      teaspoons = user_tablespoons * 3
      =====
      print("Número de cucharaditas: " + str(teaspoons))
