..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: seqmut-10-
   :start: 1

Patrón de acumulación con Strings
----------------------------------

También podemos acumular cadenas en lugar de acumular números, como has visto antes. El siguiente programa no es
particularmente útil para el procesamiento de datos, pero más adelante veremos cosas más útiles que acumulan cadenas.

.. activecode:: ac8_10_1
    
   s = input("Enter some text")
   ac = ""
   for c in s:
       ac = ac + c + "-" + c + "-"
       
   print(ac)
 
Mire cuidadosamente la línea 4 en el programa anterior (``ac = ac + c + "-" + c + "-"``). En palabras, dice que el
El nuevo valor de ``ac`` será el valor anterior de ``ac`` concatenado con el carácter actual, un guión, luego el
personaje actual y una carrera de nuevo. Estamos construyendo la cadena de resultados carácter por carácter.

Observe de cerca también la inicialización de ``ac``. Comenzamos con una cadena vacía y luego comenzamos a agregar
nuevos personajes hasta el final. También tenga en cuenta que esta vez le he dado un nombre diferente, ``ac`` en lugar de
``acumular``. No hay nada mágico en estos nombres. Podrías usar cualquier variable válida y funcionaría
mismo (intente sustituir x por ac en todas partes en el código anterior).

**Revisa tu entendimiento**

.. mchoice:: question8_10_1
   :answer_a: Ball
   :answer_b: BALL
   :answer_c: LLAB
   :correct: c
   :feedback_a: Cada elemento se convierte a mayúsculas antes de la concatenación.
   :feedback_b: Cada carácter se convierte a mayúsculas pero el orden es incorrecto.
   :feedback_c: Sí, el orden se invierte debido al orden de la concatenación.
   :practice: T

   Lo que se imprime en las siguientes declaraciones:
   
   .. code-block:: python

      s = "ball"
      r = ""
      for item in s:
         r = item.upper() + r
      print(r)

.. activecode:: ac8_10_2
   :language: python
   :autograde: unittest
   :practice: T

   1. Para cada carácter de la cadena ya guardado en la variable ``str1``, agregue cada carácter a una lista llamada ``caracteres``.
   ~~~~
   str1 = "I love python"
   # SUGERENCIA: ¿cuál es el acumulador? Eso debería ir aquí.
      
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testTwo(self):
         self.assertEqual(chars, ['I', ' ', 'l', 'o', 'v', 'e', ' ', 'p', 'y', 't', 'h', 'o', 'n'], "Testing that chars is assigned to correct values.")
         self.assertIn('append', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

   myTests().main()

.. activecode:: ac6_6_6
   :language: python
   :autograde: unittest
   :practice: T

   Asigne una cadena vacía a la variable ``output``. Usando la función ``range``, escriba el código para que la variable ``output`` tenga 35 ``a`` dentro (como ``"aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"``). Pista: ¡usa accumulation pattern!
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testThree(self):
         self.assertEqual(output, "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa", "Testing that output has the correct value.")
         self.assertNotIn("aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa", self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

   myTests().main()
   
