..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: moreiter-10-
   :start: 1

Evaluación de capítulos
-----------------------

.. activecode:: ac14_10_1
    :practice: T
    :topics: MoreAboutIteration/listenerLoop
    
    Escriba una función, ``sublist``, que tome una lista de números como parámetro. En la función, use un bucle while para devolver una sublista de la lista de entrada. La sublista debe contener los mismos valores de la lista original hasta que alcance el número 5 (no debe contener el número 5).
    ~~~~

    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

       def testThree(self):
          self.assertEqual(sublist([1, 2, 3, 4, 5, 6, 7, 8]), [1, 2, 3, 4], "Testing that sublist([1, 2, 3, 4, 5, 6, 7, 8]) returns [1, 2, 3, 4]")
          self.assertEqual(sublist([5]), [], "Testing that sublist([5]) returns []")
          self.assertEqual(sublist([8, 6, 5]), [8, 6], "Testing that sublist([8, 6, 5]) returns [8, 6]")
          self.assertEqual(sublist([1, 6, 2, 3, 9]), [1, 6, 2, 3, 9], "Testing that sublist([1, 6, 2, 3, 9]) returns ([1, 6, 2, 3, 9])")

    myTests().main()

.. activecode:: ac14_10_2
    :practice: T
    :topics: MoreAboutIteration/listenerLoop

    Escriba una función llamada ``check_nums`` que tome una lista como parámetro y contenga un ciclo while que solo se detiene una vez que el elemento de la lista es el número 7. Lo que se devuelve es una lista de todos los números hasta llega a 7.
    ~~~~

    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

       def testOne(self):
          self.assertEqual(check_nums([0,2,4,9,2,3,6,8,12,14,7,9,10,8,3]), [0,2,4,9,2,3,6,8,12,14], "Testing that check_nums stops on the correct postion with input [0,2,4,9,2,3,6,8,12,14,7,9,10,8,3]")
          self.assertEqual(check_nums([9,302,4,62,78,97,10,7,8,23,53,1]), [9,302,4,62,78,97,10], "Testing that check_nums stops on the correct position with input [9,302,4,62,78,97,10,7,8,23,53,1]")
          self.assertEqual(check_nums([7,8,3,2,4,51]), [], "Testing that check_nums stops on the correct position with input [7,8,3,2,4,51]")
          self.assertEqual(check_nums([1, 6, 2, 3, 9]), [1, 6, 2, 3, 9], "Testing that check_nums([1, 6, 2, 3, 9]) returns ([1, 6, 2, 3, 9])")

    myTests().main()

.. activecode:: ac14_10_3
    :practice: T
    :topics: MoreAboutIteration/listenerLoop

    Escriba una función, ``sublist``, que tome una lista de strings como parámetro. En la función, use un bucle while para devolver una sublista de la lista de entrada. La sublista debe contener los mismos valores de la lista original hasta que llegue al string "STOP" (no debe contener la cadena "STOP").
    ~~~~

    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

       def testFour(self):
          self.assertEqual(sublist(["bob", "joe", "lucy", "STOP", "carol", "james"]), ["bob", "joe", "lucy"], "Testing that sublist(['bob', 'joe', 'lucy', 'STOP', 'carol', 'james']) returns ['bob', 'joe', 'lucy']")
          self.assertEqual(sublist(["STOP"]), [], "Testing that sublist(['STOP']) returns []")
          self.assertEqual(sublist(["jackie", "paul", "STOP"]), ["jackie", "paul"], "Testing that sublist(['jackie', 'paul', 'STOP']) returns ['jackie', 'paul']")

    myTests().main()

.. activecode:: ac14_10_4
    :practice: T
    :topics: MoreAboutIteration/ThewhileStatement

    Escriba una función llamada ``stop_at_z`` que itera a través de una lista de strings. Usando un ciclo while, agregue cada string a una nueva lista hasta que el string que aparece sea "z". La función debería devolver la nueva lista.
    ~~~~

    def stop_at_z():

    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

       def testOne(self):
          self.assertEqual(stop_at_z(['c', 'b', 'd', 'zebra', 'h', 'r', 'z', 'm', 'a', 'k']), ['c', 'b', 'd', 'zebra', 'h', 'r'], "Testing the function stop_at_z on the input ['c', 'b', 'd', 'zebra', 'h', 'r', 'z', 'm', 'a', 'k'].")
          self.assertEqual(stop_at_z(['zoo', 'zika', 'ozzie', 'pizzazz', 'z', 'pizza', 'zap', 'haze']), ['zoo', 'zika', 'ozzie', 'pizzazz'], "Testing the function stop_at_z on the input ['zoo', 'zika', 'ozzie', 'pizzazz', 'z', 'pizza', 'zap', 'haze'].")
          self.assertEqual(stop_at_z(['z']), [], "Testing the function stop_at_z on the input ['z'].")

    myTests().main()

.. actex:: ac14_10_5
    :practice: T
    :topics: MoreAboutIteration/ThewhileStatement

    A continuación se muestra un bucle for que funciona. Debajo del ciclo for, reescribe el problema para que haga lo mismo, pero usando un ciclo while en lugar de un ciclo for. Asigne el total acumulado en el código del bucle while a la variable ``sum2``. Una vez completado, sum2 debe ser igual a sum1.
    ~~~~

    sum1 = 0

    lst = [65, 78, 21, 33]

    for x in lst:
        sum1 = sum1 + x

    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

       def testFive(self):
          self.assertEqual(sum2, 197, "Testing that sum2 is assigned to correct value.")
          self.assertIn('while', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

    myTests().main()

.. activecode:: ac14_10_6
    :practice: T
    :topics: MoreAboutIteration/listenerLoop

    **Desafío:** Escribe una función llamada ``beginning`` que toma una lista como entrada y contiene un ciclo while que solo se detiene una vez que el elemento de la lista es el string 'bye'. Lo que se devuelve es una lista que contiene hasta los primeros 10 strings, independientemente de dónde se detenga el ciclo. (es decir, si se detiene en el elemento 32, se devuelven los primeros 10. Si "bye" es el quinto elemento, se devuelven los primeros 4). *Si desea que esto sea un desafío aún mayor, hágalo sin slice*
    ~~~~

    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

       def testOne(self):
          self.assertEqual(beginning(['water', 'phone', 'home', 'chapstick', 'market', 'headphones', 'bye', 'stickie notes', 'snapchat', 'facebook', 'social media']), ['water', 'phone', 'home', 'chapstick', 'market', 'headphones'], "Testing that beginning returns the correct list on input ['water', 'phone', 'home', 'chapstick', 'market', 'headphones', 'bye', 'stickie notes', 'snapchat', 'facebook', 'social media']")
          self.assertEqual(beginning(['bye', 'no', 'yes', 'maybe', 'sorta']), [], "Testing that beginning returns the correct list on input ['bye', 'no', 'yes', 'maybe', 'sorta']")
          self.assertEqual(beginning(['hello', 'hi', 'hiyah', 'howdy', 'what up', 'whats good', 'holla', 'good afternoon', 'good morning', 'sup', 'see yah', 'toodel loo', 'night', 'until later', 'peace', 'bye', 'good-bye', 'g night']),['hello', 'hi', 'hiyah', 'howdy', 'what up', 'whats good', 'holla', 'good afternoon', 'good morning', 'sup'] , "Testing that beginning returns the correct list on input ['hello', 'hi', 'hiyah', 'howdy', 'what up', 'whats good', 'holla', 'good afternoon', 'good morning', 'sup', 'see yah', 'toodel loo', 'night', 'until later', 'peace', 'bye', 'good-bye', 'g night']")

    myTests().main()
