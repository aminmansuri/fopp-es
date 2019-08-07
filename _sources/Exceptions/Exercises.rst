..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

:skipreading:`True`

Ejercicios
==========

#.

    .. tabbed:: q1

        .. tab:: Pregunta

            .. actex:: assess_ac23_5_1
               :practice: T
               :topics: Exceptions/intro-exceptions

               A continuación, hemos proporcionado un código con errores. Agregue una cláusula try / except para que el código se ejecute sin errores. Si una publicación de blog no obtuvo Me gusta, se debe agregar una clave 'Me gusta' a ese diccionario con un valor de 0.

               ~~~~

               blog_posts = [{'Photos': 3, 'Likes': 21, 'Comments': 2}, {'Likes': 13, 'Comments': 2, 'Shares': 1}, {'Photos': 5, 'Likes': 33, 'Comments': 8, 'Shares': 3}, {'Comments': 4, 'Shares': 2}, {'Photos': 8, 'Comments': 1, 'Shares': 1}, {'Photos': 3, 'Likes': 19, 'Comments': 3}]

               total_likes = 0

               for post in blog_posts: 
                   total_likes = total_likes + post['Likes']

               =====

               from unittest.gui import TestCaseGui

               class myTests(TestCaseGui):

                   def testA(self):
                       self.assertEqual(total_likes, 86, "Testing that total_likes has the correct value.")
                   def testB(self):
                        accum = 0
                        for d in blog_posts: 
                            if 'Likes' in d:
                                accum +=1
                        self.assertEqual(accum, 6, "Testing that blog_post dictionaries all have a 'Likes' key.")   

               myTests().main()  

#.

    .. tabbed:: q2

        .. tab:: Pregunta

            .. actex:: assess_ac23_5_2
               :practice: T
               :topics: Exceptions/intro-exceptions

               El siguiente código asigna la quinta letra de cada palabra en ``comida`` a la nueva lista ``quinta``. Sin embargo, el código actualmente produce errores. Inserte una cláusula tryNo entraremos en más detalles sobre el manejo de excepciones en este curso introductorio. Mira el oficial/except que permitirá que el código se ejecute y produzca una lista de la quinta letra en cada palabra. Si la palabra no es lo suficientemente larga, no debe imprimir nada. Nota: La sentencia pass es una operación nula; nada sucederá cuando se ejecute.
               ~~~~

               food = ["chocolate", "chicken", "corn", "sandwich", "soup", "potatoes", "beef", "lox", "lemonade"]
               fifth = []

               for x in food:
      
                   fifth.append(x[4])

               =====

               from unittest.gui import TestCaseGui

               class myTests(TestCaseGui):

                   def testOneA(self):
                       self.assertEqual(fifth, ['o', 'k', 'w', 't', 'n'], "Testing that fifth is assigned to correct values.")
     
                myTests().main()