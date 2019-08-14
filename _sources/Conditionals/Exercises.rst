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
   :prefix: condition-14-
   :start: 1

Ejercicios
----------

#.

    .. tabbed:: q1

        .. tab:: Question

            .. actex:: ac7_14_1

               Escriba un código que le pida al usuario que ingrese una puntuación numérica (0-100). En respuesta, debe imprimir el puntaje y la calificación de letra correspondiente, de acuerdo con la tabla a continuación.
        
               .. table::
        
                  =======   =====
                  Puntaje   Grado
                  =======   =====
                  >= 90     A
                  [80-90)   B
                  [70-80)   C
                  [60-70)   D
                  < 60      F
                  =======   =====
        
               Los corchetes cuadrados y redondos indican intervalos cerrados y abiertos.
               Un intervalo cerrado incluye el número, y el intervalo abierto lo excluye. Entonces 79.99999 obtiene el grado C, pero 80 obtiene el grado B.
               ~~~~
           
        .. tab:: Answer

            .. activecode:: ans7_14_1
            
               sc = input("Ingrese una puntuación de 0 a 100 (se permiten puntos decimales)")
               fl_sc = float(sc)
               
               if fl_sc < 60:
                   gr = "F"
               elif fl_sc <70:
                   gr = "D"
               elif fl_sc < 80:
                   gr = "C"
               elif fl_sc < 90:
                   gr = "B"
               else:
                   gr = "A"
               
               print("Puntaje", fl_sc, "obtiene una calificación de", gr)
                 

#.

    .. tabbed:: q2

        .. tab:: Question

           .. actex:: ac7_14_2

               Un año es un **año bisiesto** si es divisible entre 4. Si el año puede dividirse equitativamente entre 100, NO es un año bisiesto, a menos que el año sea **también** divisible por 400. Es un año bisiesto. Escriba un código que le pida al usuario que ingrese un año y genere True si es un año bisiesto o False de lo contrario. Use las declaraciones if.

               .. table::
    
                  =======  =====
                  Año      Bisiesto?
                  =======  =====
                  1944     True
                  2011     False
                  1986     False
                  1800     False     
                  1900     False
                  2000     True
                  2056     True
                  =======  =====
                
               Arriba hay algunos ejemplos de cuál debería ser la salida para varias entradas.
               ~~~~



#.

    .. tabbed:: q3

        .. tab:: Question

            .. actex:: ac7_14_3

                ¿Qué evalúan estas expresiones?
            
                #.  ``3 == 3``
                #.  ``3 != 3``
                #.  ``3 >= 4``
                #.  ``not (3 < 4)``
                ~~~~        
        

        .. tab:: Answer
            
            #. True
            #. False
            #. False
            #. False



#.
    .. tabbed:: q4

        .. tab:: Question

            .. actex:: ac7_14_4

                Dé los **opuestos lógicos** de estas condiciones, lo que significa una expresión va a
                producir False siempre que esta expresión produzca True, y viceversa. A Usted no
                se le permite usar el operador ``not``.

                #.  ``a > b``
                #.  ``a >= b``
                #.  ``a >= 18  and  day == 3``
                #.  ``a >= 18  or  day != 3``
                ~~~~

#.

    .. tabbed:: q5

        .. tab:: Question

            .. actex:: ac7_14_5
                :nocodelens:

                Se proporcionan las longitudes de dos lados de un triángulo rectángulo. Asigne la longitud de la hipotenusa a la variable ``hypo_len``.  (Sugerencia:  ``x ** 0.5`` devolverá la raíz cuadrada, o usará ``sqrt`` del módulo matemático)
                ~~~~

                side1 = 3
                side2 = 4

                ====

                from unittest.gui import TestCaseGui

                class myTests(TestCaseGui):
                    def testOne(self):
                        self.assertEqual(hypo_len,5,"Testing that hypo_len has been set correctly")

                myTests().main()

#.
   .. tabbed:: q6

        .. tab:: Question

           .. actex:: ac7_14_6
               :practice: T
               :topics: Conditionals/TheAccumulatorPatternwithConditionals
               :nocodelens:

               Se proporciona una lista de números. Para cada uno de los números en la lista, determine si son pares. Si el número es par, agregue ``True``  a una nueva lista llamada ``is_even``. Si el número es impar, entonces agregue ``False``.
               ~~~~
               num_lst = [3, 20, -1, 9, 10]

               ====

               from unittest.gui import TestCaseGui

               class myTests(TestCaseGui):
                    def testOne(self):
                        self.assertEqual(is_even, [False, True, False, False, True],"Testing that is_even is set correctly.")

               myTests().main()


#.
   .. tabbed:: q7

        .. tab:: Question

           .. actex:: ac7_14_7
               :practice: T
               :topics: Conditionals/TheAccumulatorPatternwithConditionals
               :nocodelens:

               Se proporciona una lista de números. Para cada uno de los números en la lista, determine si son impares. Si el número es impar, agregue ``True``  a una nueva lista llamada ``is_odd``. Si el número es par, entonces agregue ``False``.
               ~~~~
               num_lst = [3, 20, -1, 9, 10]


               ====
               from unittest.gui import TestCaseGui

               class myTests(TestCaseGui):
                   def testOne(self):
                       self.assertEqual(is_odd, [True, False, True, True, False],"Testing that is_odd is set correctly.")

               myTests().main()

#.
   .. tabbed:: q8

        .. tab:: Question

           .. actex:: ac7_14_8

               Dadas las longitudes de tres lados de un triángulo, determina si el triángulo está en ángulo recto. Si es así, asigne ``True`` a la variable ``is_rightangled``. Si no es así, entonces asigne ``False`` a la variable ``is_rightangled``.

               Sugerencia: la aritmética de coma flotante no siempre es exactamente precisa,
               por lo tanto, no es seguro probar los números de coma flotante para determinar la igualdad.
               Si un buen programador quiere saber si
               ``x`` es igual o lo suficientemente cerca de ``y``, probablemente lo codificarían como
   
               .. sourcecode:: python
   
                   if  abs(x - y) < 0.001:      # si x es aproximadamente igual a y
                       ...

               ~~~~
               a = 5
               b = 6
               c = 8


               ====
               from unittest.gui import TestCaseGui

               class myTests(TestCaseGui):
                   def testOne(self):
                       self.assertEqual(is_rightangled, False, "Testing whether is_rightangled is set correctly")

               myTests().main()
#.

   .. tabbed:: q9

        .. tab:: Question

            .. actex:: ac7_14_9

               Implemente la calculadora para la fecha de Pascua.

               El siguiente algoritmo calcula la fecha del Domingo de Pascua para cualquier año entre 1900 y 2099.

               Solicite al usuario que ingrese un año.
               Calcule lo siguiente:


   
                   1. a = year % 19
                   #. b = year % 4
                   #. c = year % 7
                   #. d = (19 * a + 24) % 30
                   #. e = (2 * b + 4 * c + 6 * d + 5) % 7
                   #. dateofeaster = 22 + d + e
   
   
               Nota especial: el algoritmo puede dar una fecha en abril. Sabrá que la fecha es en abril si el cálculo le da una respuesta superior a  31.  (Deberá ajustar) Además, si el año es uno de cuatro especiales
               años (1954, 1981, 2049 o 2076) restan 7 de la fecha.

               Su programa debería imprimir un mensaje de error si el usuario proporciona una fecha que está fuera de rango.
               ~~~~

        .. tab:: Answer

            .. activecode:: answer_ex_6_13

                year = int(input("Por favor ingrese un año"))
                if year >= 1900 and year <= 2099:
                    a = year % 19
                    b = year % 4
                    c = year % 7
                    d = (19*a + 24) % 30
                    e = (2*b + 4*c + 6*d + 5) % 7
                    dateofeaster = 22 + d + e

                    if year == 1954 or year == 2981 or year == 2049 or year == 2076:
                        dateofeaster = dateofeaster - 7

                    if dateofeaster > 31:
                        print("Abril", dateofeaster - 31)
                    else:
                        print("Marzo", dateofeaster)
                else:
                    print("ERROR...año fuera de rango")

        .. tab:: Discussion

            .. disqus::
                :shortname: interactivepython
                :identifier: disqus_2dfd6acf1ca849c2853dad606d1ba255

#.

   .. tabbed:: q9

        .. tab:: Question

            .. actex:: ac7_14_10

               Haga que el usuario ingrese texto e imprima True si es un palíndromo, False de lo contrario. (Sugerencia: reutilizar
               parte de su código de la última pregunta. El operador == compara dos valores para ver si son iguales)
               ~~~~

#.

   .. parsonsprob:: pp7_14_11

      Escriba un programa que imprima un saludo a cada estudiante en la lista. Esta lista también debe hacer un seguimiento de cuántos estudiantes han sido recibidos y tener en cuenta que cada vez que un nuevo estudiante ha sido recibido. Cuando solo un estudiante ha ingresado, el programa debe decir "¡El primer estudiante ha ingresado!". Después, el programa debería decir "¡Hay {número aquí} estudiantes en el aula!".
      -----
      students = ["Jay", "Stacy", "Iman", "Trisha", "Ahmed", "Daniel", "Shadae", "Tosin", "Charlotte"]
      =====
      num_students = 0
      =====
      for student in students:
      =====
          print("Bienvenido a clase, " + student)
          num_students += 1
      =====
          if num_students == 1:
              print("El primer alumno ha entrado!")
      =====
          elif num_students > 1:
              print("Existen " + str(num_students) + " estudiantes en el aula!")

#.

   .. parsonsprob:: pp7_14_12

      Arme un programa para que pueda imprimir con éxito una declaración de impresión, dado el valor de x.
      -----
      x = 16
      =====
      if x > 10:
      =====
          if x > 20:
              print("¡Este es un gran número!")
      =====
          else:
              print("Este es un número bastante grande")
