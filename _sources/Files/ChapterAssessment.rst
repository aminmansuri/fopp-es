..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: files-10-
   :start: 1

Evaluación de capítulos
=======================

.. datafile:: travel_plans.txt
   :fromfile: travel_plans.txt
   :hide:

.. datafile:: school_prompt.txt
   :fromfile: school_prompt.txt
   :hide:

.. datafile:: emotion_words.txt
   :fromfile: emotion_words.txt
   :hide:

.. activecode:: ac9_10_1
   :language: python
   :autograde: unittest
   :practice: T
   :available_files: travel_plans.txt

   El archivo de texto, ``travel_plans.txt``, contiene los planes de viaje de verano para alguien con algún comentario. Encuentre el número total de caracteres en el archivo y guárdelo en la variable ``num``.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(num, 316, "Testing that num value is assigned to correct value.")

   myTests().main()

.. activecode:: ac9_10_2
   :language: python
   :autograde: unittest
   :practice: T
   :available_files: emotion_words.txt
   
   Hemos proporcionado un archivo llamado ``emotion_words.txt`` que contiene líneas de palabras que describen emociones. Encuentre el número total de palabras en el archivo y asigne este valor a la variable ``num_words``.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(num_words, 48, "Testing that num_words was assigned to the correct value.")

   myTests().main()


.. activecode:: ac9_10_3
   :language: python
   :autograde: unittest
   :practice: T
   :available_files: school_prompt.txt

   Asigne a la variable ``num_lines`` el número de líneas en el archivo ``school_prompt.txt``.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(num_lines, 10, "Testing that num_lines has the correct value.")

   myTests().main()


.. activecode:: ac9_10_4
   :language: python
   :autograde: unittest
   :practice: T
   :available_files: school_prompt.txt

   Asigne los primeros 30 caracteres de ``school_prompt.txt`` como una cadena a la variable ``beginning_chars``.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(len(beginning_chars), 30, "Testing that beginning_chars has the correct length.")
         self.assertEqual(beginning_chars, "Writing essays for school can ", "Testing that beginning_chars has the correct string.")

   myTests().main()   


.. activecode:: ac9_10_5
   :language: python
   :autograde: unittest
   :practice: T
   :available_files: school_prompt.txt

   **Desafío:** Usando el archivo ``school_prompt.txt``, asigne la tercera palabra de cada línea a una lista llamada ``three``.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(three, ['for', 'find', 'to', 'many', 'they', 'solid', 'for', 'have', 'some', 'ups,'], "Testing that three has the correct value.")

   myTests().main()
 

.. activecode:: ac9_10_6
   :language: python
   :autograde: unittest
   :practice: T
   :available_files: emotion_words.txt

   **Desafío:** Cree una lista llamada ``emotions`` que contenga la primera palabra de cada línea en ``emotion_words.txt``.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(emotions, ['Sad', 'Angry', 'Happy', 'Confused', 'Excited', 'Scared', 'Nervous'], "Testing that emotions was created correctly.")

   myTests().main() 


.. activecode:: ac9_10_7
   :language: python
   :autograde: unittest
   :practice: T
   :available_files: travel_plans.txt

   Asigne los primeros 33 caracteres del archivo de texto, ``travel_plans.txt`` a la variable ``first_chars``.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testFive(self):
         self.assertEqual(first_chars, "This summer I will be travelling.", "Testing that first_chars is assigned to correct value.")

   myTests().main()


.. activecode:: ac9_10_8
   :language: python
   :autograde: unittest
   :practice: T
   :available_files: school_prompt.txt

   **Desafío:** Usando el archivo ``school_prompt.txt``, si el carácter 'p' está en una palabra, entonces agregue la palabra a una lista llamada ``p_words``.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(p_words, ['topic', 'point', 'papers,', 'ups,', 'scripts.'], "Testing that p_words has the correct list.")

   myTests().main()
