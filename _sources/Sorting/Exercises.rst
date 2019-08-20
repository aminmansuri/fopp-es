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
   :prefix: sort-8-
   :start: 1

Ejercicios
-----------

.. tabbed:: q1

    .. tab:: Question

        .. actex:: ac18_8_1

            Va a escribir una función que tome un string como parámetro y devuelva una lista de los cinco caracteres más frecuentes en el string. Eventualmente, podrá hacer este tipo de problema sin mucho entrenamiento. Pero vamos a guiarlo a través de una serie de ejercicios.

            Primero, la función contará las frecuencias de todos los caracteres, como lo hemos hecho antes, usando un diccionario y el patrón acumulador. Luego, ordenará los pares (clave, valor). Finalmente, tomará una porción de la lista ordenada para obtener solo los cinco primeros. Esa rebanada será devuelta.

            Paso 1. Supongamos que tiene esta lista, [8, 7, 6, 6, 4, 4, 3, 1, 0], ya ordenada, ¿cómo haría una lista de los 5 mejores? (Sugerencia: toma un slice).
            ~~~~
            
            L = [8, 7, 6, 6, 4, 4, 3, 1, 0]
    
    .. tab:: Answer
    
        .. actex:: answer16_8_1
        
             L = [8, 7, 6, 6, 4, 4, 3, 1, 0]
             L[:5]

.. tabbed:: q2

    .. tab:: Question

        .. actex:: ac18_8_2

            Ahora supongamos que la lista aún no está ordenada. ¿Cómo obtendría esos mismos cinco elementos de esta lista?
            ~~~~

            L = [0, 1, 6, 7, 3, 6, 8, 4, 4]
            
    .. tab:: Answer
 
         .. actex:: answer16_8_2

            L = [0, 1, 6, 7, 3, 6, 8, 4, 4]
            L2 = sorted(L, reverse=True)
            L2[:5]
    

.. tabbed:: q3

    .. tab:: Question

        .. actex:: ac18_8_3

            Ahora tome una lista L y haga un diccionario de recuentos de la frecuencia con la que aparecen estos números en la lista.
            ~~~~
    
            L = [0, 1, 6, 7, 3, 6, 8, 4, 4, 6, 1, 6, 6, 5, 4, 4, 3, 35, 4, 11]
        

    .. tab:: Answer
    
        .. actex:: answer16_8_3

            L = [0, 1, 6, 7, 3, 6, 8, 4, 4, 6, 1, 6, 6, 5, 4, 4, 3, 35, 4, 11]
            d = {}
            for x in L:
                if x in d:
                    d[x] = d[x] + 1
                else:
                    d[x] = 1


.. tabbed:: q4

    .. tab:: Question
    
        .. actex:: ac18_8_4

            Ahora ordene las teclas (números) según sus frecuencias. Revise *Sorting a Dictionary* si no está seguro de cómo hacerlo. Mantenga solo las cinco llaves principales.
            ~~~~

            L = [0, 1, 6, 7, 3, 6, 8, 4, 4, 6, 1, 6, 6, 5, 4, 4, 3, 35, 4, 11]
    
    .. tab:: Answer
    
        .. actex:: answer16_8_4
        
            L = [0, 1, 6, 7, 3, 6, 8, 4, 4, 6, 1, 6, 6, 5, 4, 4, 3, 35, 4, 11]
        
            d = {}
            for x in L:
                if x in d:
                    d[x] = d[x] + 1
                else:
                    d[x] = 1

            s = sorted(d, key=lambda x: d[x], reverse=True)
            
            print(s[:5])
            

.. tabbed:: q5

    .. tab:: Question

        .. actex:: ac18_8_5

           Finalmente, generaliza lo que ha hecho. Escriba una función que tome un string en lugar de una lista como parámetro y devuelva una lista de los cinco caracteres más frecuentes en el string.
           ~~~~


    .. tab:: Answer
    
        .. actex:: answer16_8_5
        
            def five_most_frequent(s):
                d = {}
                for x in s:
                    if x in d:
                        d[x] = d[x] + 1
                    else:
                        d[x] = 1
                
                s = sorted(d, key=lambda x: d[x], reverse=True)
            
                return s[:5]
                
            =====

            from unittest.gui import TestCaseGui

            class myTests(TestCaseGui):

               def testOne(self):
                  self.assertEqual(five_most_frequent("aaaaaabbbbbccccdefggghijkk"), ['a', 'b', 'c', 'g', 'k'], "Checking the value returned from using five_most_frequent.")

            myTests().main()
