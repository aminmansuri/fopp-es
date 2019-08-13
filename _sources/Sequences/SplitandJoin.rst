..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: sequences-9-
   :start: 1

División y unión de Cadena de caracteres
========================================

Dos de los métodos más útiles en cadenas incluyen listas de cadenas. El método ``split`` divide una cadena en una lista
de palabras. Por defecto, cualquier número de caracteres de espacio en blanco se considera un límite de palabra.

.. image:: Figures/split_default.gif
   :alt: shows the phrase "leaders and best" being split on spaces

.. activecode:: ac5_9_1
    
    song = "The rain in Spain..."
    wds = song.split()
    print(wds) 

Se puede usar un argumento opcional llamado **delimiter** para especificar qué caracteres usar como límites de palabras.

.. image:: Figures/split_on_e.jpeg
   :alt: shows example of splitting "leaders and best" on "e"

El siguiente ejemplo usa la cadena ``ai`` como delimitador:

.. activecode:: ac5_9_2

    song = "The rain in Spain..."
    wds = song.split('ai')
    print(wds)

Observe que el delimitador no aparece en el resultado.

La inversa del método de ``split`` es ``join``. Tu eliges una
cadena **separator** deseada, (a menudo llamada *glue*)
y únete a la lista con el glue *pegamento* entre cada uno de los elementos.

.. image:: Figures/join.gif
   :alt: shows process of a "/" separating the words "leaders", "and", "best"

.. activecode:: ac5_9_3

    wds = ["red", "blue", "green"]
    glue = ';'
    s = glue.join(wds)
    print(s)
    print(wds)

    print("***".join(wds))
    print("".join(wds))


La lista que pega (``wds`` en este ejemplo) no se modifica. También,
puede usar pegamento vacío o cadenas de caracteres múltiples como pegamento.

**Revisa tu entendimiento**

.. activecode:: ac5_9_4
   :language: python
   :autograde: unittest
   :practice: T

   Cree una nueva lista de los elementos 6º a 13º de ``lst`` (ocho elementos en total) y asígnela a la variable ``output``.
   ~~~~
   lst = ["swimming", 2, "water bottle", 44, "lollipop", "shine", "marsh", "winter", "donkey", "rain", ["Rio", "Beijing", "London"], [1,2,3], "gold", "bronze", "silver", "mathematician", "scientist", "actor", "actress", "win", "cell phone", "leg", "running", "horse", "socket", "plug", ["Phelps", "le Clos", "Lochte"], "drink", 22, "happyfeet", "penguins"]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testFour(self):
         self.assertEqual(output, lst[5:13], "Testing that output value is assigned to correct value.")

   myTests().main()

.. activecode:: ac5_9_5
   :language: python
   :autograde: unittest
   :practice: T

   Cree una variable ``output`` y asígnela a una lista cuyos elementos son las palabras en la cadena ``str1``.
   ~~~~
   str1 = "OH THE PLACES YOU'LL GO"

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testSix(self):
         self.assertEqual(output, ["OH", "THE", "PLACES", "YOU'LL", "GO"], "Testing that output value is assigned to correct value.")

   myTests().main()

