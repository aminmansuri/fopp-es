..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: files-4-
   :start: 1

Métodos alternativos de lectura de archivos
-------------------------------------------

Una vez que tiene un "objeto" de archivo, lo que devuelve la función abierta, Python proporciona tres métodos para leer datos
de ese objeto El método ``read()`` devuelve todo el contenido del archivo como un solo string (o solo algunos
caracteres si proporciona un número como parámetro de entrada). El método ``readlines`` devuelve todo el contenido de
todo el archivo como una lista de strings, donde cada elemento de la lista es una línea del archivo. El método ``readline``
lee una línea del archivo y la devuelve como un string. Los strings devueltos por ``readlines`` o
``readline`` contendrán el carácter de nueva línea al final.  :ref:`Table 2 <filemethods2a>` resume estos
métodos y la siguiente sesión los muestra en acción.

.. _filemethods2a:

======================== =========================== =====================================
**Nombre del método**           **Uso**                     **Explicación**
======================== =========================== =====================================
``write``                 ``filevar.write(astring)``  Agrega una cadena al final del archivo,
                                                      filevar debe referirse a un archivo que
                                                      debe haber sido abierto para escribir.
``read(n)``               ``filevar.read()``          Lee y devuelve una cadena de ``n``
                                                      caracteres, o todo el archivo como
                                                      string único si no se proporciona n.
``readline(n)``           ``filevar.readline()``      Devuelve la siguiente línea del archivo
                                                      con todo el texto hasta e incluyendo el
                                                      caracter de nueva línea. Si n se proporciona
                                                      como un parámetro que solo n caracteres
                                                      será devuelto si la línea es más larga
                                                      que ``n``.
``readlines(n)``          ``filevar.readlines()``     Devuelve una lista de cadenas, cada una
                                                      representando una sola línea del archivo.
                                                      Si no se proporciona n, entonces todas las líneas
                                                      devuelven el archivo. Si se proporciona n
                                                      entonces se leen n caracteres pero n es
                                                      redondeado hacia arriba para que una línea
                                                      entera sea devuelta
======================== =========================== =====================================


En este curso, generalmente iteraremos a través de las líneas devueltas por ``readlines()`` con un bucle for,
o usando ``read()`` para obtener todos los contenidos como un solo string.

En otros lenguajes de programación, donde no tienen el método conveniente para recorrer las líneas
del archivo, uno por uno, usan un patrón diferente que requiere un tipo diferente de bucle, el bucle ``while``.
Afortunadamente, no necesita aprender este otro patrón, y pospondremos la consideración de los bucles  ``while``
hasta más tarde en este curso. No los necesitamos para manejar datos de archivos.

.. note::

   Un error común que hacen los programadores novatos es no darse cuenta de que todas estas formas de leer el contenido del archivo,
   **usan el archivo**. Después de llamar a readlines(), si lo vuelve a llamar obtendrá una lista vacía.

**Revisa tu entendimiento**

.. raw:: html

    <pre id="school_prompt.txt">
    Writing essays for school can be difficult but
    many students find that by researching their topic that they
    have more to say and are better informed. Here are the university
    we require many undergraduate students to take a first year writing requirement
    so that they can
    have a solid foundation for their writing skills. This comes
    in handy for many students.
    Different schools have different requirements, but everyone uses
    writing at some point in their academic career, be it essays, research papers,
    technical write ups, or scripts.
    </pre>
 

.. activecode:: ac9_4_1
   :language: python
   :autograde: unittest
   :practice: T
   :available_files: school_prompt2.txt

   1. Usando el archivo ``school_prompt2.txt``, encuentre el número de caracteres en el archivo y asigne ese valor a la variable ``num_char``.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(num_char, 537, "Testing that num_char has the correct value.")

   myTests().main()


.. raw:: html

    <pre id="travel_plans.txt">
    This summer I will be travelling.
    I will go to...
    Italy: Rome
    Greece: Athens
    England: London, Manchester
    France: Paris, Nice, Lyon
    Spain: Madrid, Barcelona, Granada
    Austria: Vienna
    I will probably not even want to come back! 
    However, I wonder how I will get by with all the different languages.
    I only know English!
    </pre>

.. activecode:: ac9_4_2
   :available_files: travel_plans2.txt
   :language: python
   :autograde: unittest
   :practice: T

   2. Encuentre el número de líneas en el archivo, ``travel_plans2.txt``, y asígnelo a la variable ``num_lines``.
   ~~~~
   
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testTwo(self):
         self.assertEqual(num_lines, 11, "Testing that num_lines is assigned to correct value.")

   myTests().main()


.. raw:: html

    <pre id="emotion_words.txt">
    Sad upset blue down melancholy somber bitter troubled
    Angry mad enraged irate irritable wrathful outraged infuriated
    Happy cheerful content elated joyous delighted lively glad
    Confused disoriented puzzled perplexed dazed befuddled
    Excited eager thrilled delighted
    Scared afraid fearful panicked terrified petrified startled
    Nervous anxious jittery jumpy tense uneasy apprehensive
    </pre>

.. activecode:: ac9_4_3
   :available_files: emotion_words2.txt
   :language: python
   :autograde: unittest
   :practice: T
   
   3. Cree una cadena llamada ``first_forty`` que esté compuesta por los primeros 40 caracteres de ``emotion_words2.txt``.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(first_forty, 'Sad upset blue down melancholy somber bi', "Testing that first_forty was created correctly.")
   myTests().main() 

.. datafile:: travel_plans2.txt
   :fromfile: travel_plans.txt
   :hide:

.. datafile:: school_prompt2.txt
   :fromfile: school_prompt.txt
   :hide:

.. datafile:: emotion_words2.txt
   :fromfile: emotion_words.txt
   :hide:
