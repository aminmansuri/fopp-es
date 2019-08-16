..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. Week 4 Assessment 1

Evaluación del Capítulo - Métodos de Lista
-------------------------------------------

**Chequea tu entendimiento**

.. mchoice:: assess_question4_1_1_1
   :answer_a: I.
   :answer_b: II.
   :answer_c: Tampoco es el diagrama de referencia correcto.
   :feedback_a: Sí, cuando usamos el método remove, solo estamos editando la lista existente, no haciendo una nueva copia.
   :feedback_b: Cuando usamos el método remove, simplemente editamos la lista existente. No hacemos una nueva copia que no incluya el objeto eliminado.
   :feedback_c: Uno de los diagramas es correcto: mire nuevamente lo que le está sucediendo a lst.
   :correct: a
   :practice: T
   :topics: TransformingSequences/MutatingMethods

   ¿Cuál de estos es un diagrama de referencia correcto después de la ejecución del siguiente código?

   .. sourcecode:: python
   
    lst = ['mercury', 'venus', 'earth', 'mars', 'jupiter', 'saturn', 'uranus', 'neptune', 'pluto']
    lst.remove('pluto')
    first_three = lst[:3]

   I. 

   .. image:: Figures/week3a1_1.png
      :alt: First Potential Solution

   II. 

   .. image:: Figures/week3a1_2.png
      :alt: Second Potential Solution

.. mchoice:: assess_question4_1_1_2
   :answer_a: .pop()
   :answer_b: .insert()
   :answer_c: .count()
   :answer_d: .index()
   :feedback_a: pop elimina y devuelve elementos (el comportamiento predeterminado es eliminar y devolver el último elemento de la lista).
   :feedback_b: insert agregará un elemento en cualquier posición especificada.
   :feedback_c: cuenta devuelve el número de veces que ocurre algo en una lista
   :feedback_d: Sí, el índice devolverá la posición de la primera aparición de un elemento.
   :correct: d
   :practice: T
   :topics: TransformingSequences/MutatingMethods

   ¿Qué método usarías para determinar la posición de un elemento en una lista?

.. mchoice:: assess_question4_1_1_3
   :answer_a: .insert()
   :answer_b: .pop()
   :answer_c: .append()
   :answer_d: .remove()
   :feedback_a: Si bien puede usar la inserción, no es el mejor método para usar porque debe especificar que desea pegar el nuevo elemento al final.
   :feedback_b: pop elimina un elemento de una lista
   :feedback_c: Sí, aunque puede usar la inserción para hacer lo mismo, no necesita proporcionar la posición.
   :feedback_d: remove elimina la primera aparición de cualquier elemento que se le indique. No agrega un elemento.
   :correct: c
   :practice: T
   :topics: TransformingSequences/MutatingMethods

   ¿Qué método es el mejor para agregar un elemento al final de una lista?


.. activecode:: assess_ac4_1_1_4
    :language: python
    :practice: T
    :topics: TransformingSequences/MutatingMethods

    Escriba el código para agregar 'equitación' a la tercera posición (es decir, justo antes del voleibol) en la lista ``sports``.
    ~~~~
    sports = ['cricket', 'football', 'volleyball', 'baseball', 'softball', 'track and field', 'curling', 'ping pong', 'hockey']


    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

      def test_output(self):
        self.assertEqual(sports, ['cricket', 'football', 'horseback riding', 'volleyball', 'baseball', 'softball', 'track and field', 'curling', 'ping pong', 'hockey'], "Testing that sports is set correctly.")

    myTests().main()

.. activecode:: assess_ac4_1_1_5
    :language: python
    :practice: T
    :topics: TransformingSequences/MutatingMethods

    Escriba el código para sacar a 'Londres' de la lista ``trav_dest``.
    ~~~~
    trav_dest = ['Beirut', 'Milan', 'Pittsburgh', 'Buenos Aires', 'Nairobi', 'Kathmandu', 'Osaka', 'London', 'Melbourne']


    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

      def test_output(self):
        self.assertEqual(trav_dest, ['Beirut', 'Milan', 'Pittsburgh', 'Buenos Aires', 'Nairobi', 'Kathmandu', 'Osaka', 'Melbourne'], "Testing that trav_dest is set correctly.")

    myTests().main()

.. activecode:: assess_ac4_1_1_6
    :language: python
    :practice: T
    :topics: TransformingSequences/MutatingMethods

    Escriba el código para agregar 'Guadalajara' al final de la lista ``trav_dest`` usando un método de lista.
    ~~~~
    trav_dest = ['Beirut', 'Milan', 'Pittsburgh', 'Buenos Aires', 'Nairobi', 'Kathmandu', 'Osaka', 'Melbourne']


    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

      def test_output(self):
        self.assertEqual(trav_dest, ['Beirut', 'Milan', 'Pittsburgh', 'Buenos Aires', 'Nairobi', 'Kathmandu', 'Osaka', 'Melbourne', 'Guadalajara'], "Testing that trav_dest is set correctly.")
        self.assertNotIn('+', self.getEditorText(), "Testing that you are not using concatenation (+).")
        self.assertIn('.', self.getEditorText(), "Testing that a method invocation was used in your code.")

    myTests().main()


Evaluación del capítulo: alias y referencias
=============================================

**Revisa tu entendimiento**

.. fillintheblank:: assess_question3_3_1_1
   :practice: T
   :topics: TransformingSequences/ObjectsandReferences

   What will be the value of ``a`` after the following code has executed?

   .. sourcecode:: python

    a = ["holiday", "celebrate!"]
    quiet = a
    quiet.append("company")


   The value of ``a`` will be

   -  :\[["']holiday["'], ["']celebrate!["'], ["']company["']\]: Good work!
      :\[["']holiday["'], ["']celebrate!["']\]: This is the old value of a - a has changed.
      :.*: Incorrect, try again. Don't forget to include a space between list elements.

.. mchoice:: assess_question3_3_1_2
   :answer_a: yes
   :answer_b: no
   :feedback_a: Sí, b y z hacen referencia a la misma lista y los cambios se realizan utilizando ambos alias.
   :feedback_b: ¿Puedes averiguar cuál es el valor de b solo mirando las líneas que mencionan b?
   :correct: a
   :practice: T
   :topics: TransformingSequences/Aliasing

   ¿Podría el alias causar una posible confusión en este problema?

   .. sourcecode:: python

    b = ['q', 'u', 'i']
    z = b
    b[1] = 'i'
    z.remove('i')
    print(z)

.. mchoice:: assess_question3_3_1_4
   :answer_a: yes
   :answer_b: no
   :feedback_a: Como una cadena es inmutable, el alias no será tan confuso. Tenga cuidado de usar algo como item = item + new_item con objetos mutables porque crea un nuevo objeto. Sin embargo, cuando usamos +=, eso no sucede.
   :feedback_b: Como una cadena es inmutable, el alias no será tan confuso. Tenga cuidado de usar algo como item = item + new_item con objetos mutables porque crea un nuevo objeto. Sin embargo, cuando usamos +=, eso no sucede.
   :correct: b
   :practice: T
   :topics: TransformingSequences/Aliasing

   ¿Podría el alias causar una posible confusión en este problema?

   .. sourcecode:: python

    sent = "Holidays can be a fun time when you have good company!"
    phrase = sent
    phrase = phrase + " Holidays can also be fun on your own!"

.. mchoice:: assess_question3_3_1_5
   :answer_a: I.
   :answer_b: II.
   :answer_c: III.
   :answer_d: IV.
   :feedback_a: Cuando un objeto se concatena con otro usando +=, extiende el objeto original. Si esto se hace en la forma más larga (ítem = ítem + objeto), entonces hace una copia.
   :feedback_b: Cuando un objeto se concatena con otro usando +=, extiende el objeto original. Si esto se hace en la forma más larga (ítem = ítem + objeto), entonces hace una copia.
   :feedback_c: Cuando un objeto se concatena con otro usando +=, extiende el objeto original. Si esto se hace en la forma más larga (ítem = ítem + objeto), entonces hace una copia.
   :feedback_d: Sí, el comportamiento de obj = obj + object_two es diferente de obj += object_two cuando obj es una lista. La primera versión crea un nuevo objeto por completo y lo reasigna a obj. La segunda versión cambia el objeto original para que el contenido de object_two se agregue al final de la primera.
   :correct: d
   :practice: T
   :topics: TransformingSequences/ObjectsandReferences

   ¿Cuál de estos es un diagrama de referencia correcto después de la ejecución del siguiente código?
   
   .. sourcecode:: python

    x = ["dogs", "cats", "birds", "reptiles"]
    y = x
    x += ['fish', 'horses']
    y = y + ['sheep']

   I.

   .. image:: Figures/week3a3_1.png
      :alt: First Potential Solution
   
   II.

   .. image:: Figures/week3a3_2.png
      :alt: Second Potential Solution
   
   III.

   .. image:: Figures/week3a3_3.png
      :alt: Third Potential Solution
   
   IV.

   .. image:: Figures/week3a3_4.png
      :alt: Fourth Potential Solution

Evaluación del capítulo: Split y Join
=======================================

.. mchoice:: assess_question4_1_3_1
   :answer_a: I.
   :answer_b: II.
   :answer_c: III.
   :answer_d: IV.
   :feedback_a: Sí, cuando hacemos nuestros propios diagramas, queremos mantener la información anterior porque a veces otras variables dependen de ellos. Sin embargo, puede estar abarrotado si hay mucha información.
   :feedback_b: No del todo, queremos hacer un seguimiento de la información antigua porque a veces otras variables dependen de ellas.
   :feedback_c: Mire nuevamente lo que sucede cuando se ejecuta la unión.
   :feedback_d: ¿Qué les sucede a los espacios en una cadena cuando se divide por espacios en blanco?
   :correct: a
   :practice: T
   :topics: TransformingSequences/MutatingMethods

   ¿Cuál de estos es un diagrama de referencia correcto después de la ejecución del siguiente código?

   .. sourcecode:: python

    sent = "The mall has excellent sales right now."
    wrds = sent.split()
    wrds[1] = 'store'
    new_sent = " ".join(wrds)

   I.

   .. image:: Figures/week3a2_1.png
      :alt: First Potential Solution
   
   II.

   .. image:: Figures/week3a2_2.png
      :alt: Second Potential Solution
   
   III.

   .. image:: Figures/week3a2_3.png
      :alt: Third Potential Solution
   
   IV.

   .. image:: Figures/week3a2_4.png
      :alt: Fourth Potential Solution


.. activecode:: assess_ac_4_1_3_2
    :language: python
    :autograde: unittest
    :practice: T
    :topics: TransformingSequences/MutatingMethods

    Escriba el código para encontrar la posición de la cadena "Tony" en la lista ``awards`` y guarde esa información en la variable ``pos``.
    ~~~~
    awards = ['Emmy', 'Tony', 'Academy', 'Grammy']


    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

      def test_output(self):
        self.assertEqual(pos, 1, "Testing that pos is set correctly.")

    myTests().main()

Evaluación del Capítulo - Mecánicas del bucle For
==================================================

**Revisa tu entendimientos**

.. mchoice:: assess_question5_1_1_1
   :answer_a: byzo
   :answer_b: x
   :answer_c: z
   :answer_d: c
   :correct: d
   :feedback_a: Esta es la variable con nuestra cadena, pero no acumula nada.
   :feedback_b: Esta es la variable iteradora. Cambia cada vez pero no se acumula.
   :feedback_c: Esta es una variable dentro del ciclo for. Cambia cada vez, pero no acumula ni retiene las expresiones antiguas que se le asignaron.
   :feedback_d: Sí, esta es la variable acumuladora. Al final del programa, tendrá un recuento completo de cuántos elementos hay en byzo.
   :practice: T
   :topics: TransformingSequences/TheAccumulatorPatternwithStrings

   ¿Cuál de estas es la variable acumuladora?
   
   .. sourcecode:: python

    byzo = 'hello world!'
    c = 0
    for x in byzo:
        z = x + "!"
        print(z)
        c = c + 1

.. mchoice:: assess_question5_1_1_2
   :answer_a: cawdra
   :answer_b: elem
   :answer_c: t
   :correct: a
   :feedback_a: Sí, esta es la secuencia sobre la que iteramos.
   :feedback_b: Esta es la variable iteradora. Cambia cada vez, pero no es toda la secuencia en sí.
   :feedback_c: Esta es la variable acumuladora. Al final del programa, tendrá un recuento completo de cuántos elementos hay en cawdra.
   :practice: T
   :topics: TransformingSequences/TheAccumulatorPatternwithLists

   ¿Cuál de estos es la secuencia?
   
   .. sourcecode:: python

    cawdra = ['candy', 'daisy', 'pear', 'peach', 'gem', 'crown']
    t = 0
    for elem in cawdra:
        t = t + len(elem)

.. mchoice:: assess_question5_1_1_3
   :answer_a: item
   :answer_b: lst
   :answer_c: num
   :correct: a
   :feedback_a: Sí, esta es la variable iteradora. Cambia cada vez, pero no es toda la secuencia en sí.
   :feedback_b: Esta es la secuencia sobre la que iteramos.
   :feedback_c: Esta es la variable acumuladora. Al final del programa, tendrá el valor total de los enteros que están en lst.
   :practice: T
   :topics: TransformingSequences/TheAccumulatorPatternwithLists

   ¿Cuál de estos es la variable iterador (bucle)?
   
   .. sourcecode:: python

    lst = [5, 10, 3, 8, 94, 2, 4, 9]
    num = 0
    for item in lst:
        num += item

.. fillintheblank:: assess_question5_1_1_4
   :practice: T
   :topics: TransformingSequences/TheAccumulatorPatternwithLists

   ¿Cuál es la variable iterador (bucle) a continuación?

   .. sourcecode:: python

    rest = ["sleep", 'dormir', 'dormire', "slaap", 'sen', 'yuxu', 'yanam']
    let = ''
    for phrase in rest:
        let += phrase[0]

   La variable iteradora es

   -  :phrase: ¡Buen trabajo!
      :rest: rest es la secuencia, no la variable iteradora.
      :let: let es la variable acumuladora, no la variable iteradora.
      :.*: Incorrecto. Inténtelo de nuevo.

.. activecode:: assess_week5_01
   :language: python
   :autograde: unittest
   :practice: T
   :topics: TransformingSequences/TheAccumulatorPatternwithStrings

   Actualmente hay una cadena llamada ``str1``. Escriba el código para crear una lista llamada ``chars`` que debe contener los caracteres de ``str1``. Cada carácter en ``str1`` debe ser su propio elemento en la lista ``chars``.
   ~~~~
   str1 = "Yo amo Python"
   # PISTA: ¿Qué es el acumulador? Eso debería ir aquí.
      
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(chars, ['I', ' ', 'l', 'o', 'v', 'e', ' ', 'p', 'y', 't', 'h', 'o', 'n'], "Testing that chars is assigned the correct value.")

   myTests().main()

Evaluación de capítulos - Accumulator Pattern
===============================================

**Revisa tu entendimiento**

.. mchoice:: assess_question5_2_1_1
   :answer_a: I.
   :answer_b: II.
   :answer_c: III.
   :answer_d: ninguno de los anteriores sería apropiado para el problema.
   :correct: c
   :feedback_a: Este patrón solo contará cuántos elementos hay en la lista, no proporcionará el valor acumulado total.
   :feedback_b: Esto restablecería el valor de s cada vez que el ciclo for repitiera, por lo que al final s se le asignaría el valor del último elemento de la lista más el último elemento de la lista.
   :feedback_c: Sí, esto resolverá el problema.
   :feedback_d: Uno de los patrones anteriores es una forma correcta de resolver el problema.
   :practice: T
   :topics: TransformingSequences/WPAccumulatorPatternStrategies

   Dado que queremos acumular la suma total de una lista de números, ¿cuál de los siguientes patrones de acumuladores sería apropiado?
   
   I.
   
   .. sourcecode:: python
   
    nums = [4, 5, 2, 93, 3, 5]
    s = 0
    for n in nums:
        s = s + 1
   
   II.
   
   .. sourcecode:: python
   
    nums = [4, 5, 2, 93, 3, 5]
    s = 0
    for n in nums:
        s = n + n
   
   III.
   
   .. sourcecode:: python
   
    nums = [4, 5, 2, 93, 3, 5]
    s = 0
    for n in nums:
        s = s + n

.. mchoice:: assess_question5_2_1_2
   :answer_a: 1.
   :answer_b: 2.
   :answer_c: 3.
   :answer_d: 4.
   :answer_e: ninguno de los anteriores sería apropiado para el problema.
   :correct: d
   :feedback_a: ¿Cómo sabe esta solución que el elemento de lst es una cadena y que s debe actualizarse?
   :feedback_b: ¿Qué le sucede a s cada vez que el ciclo for itera?
   :feedback_c: Vuelva a leer el mensaje nuevamente, ¿qué queremos acumular?
   :feedback_d: Sí, esto resolverá el problema.
   :feedback_e: Uno de los patrones anteriores es una forma correcta de resolver el problema.
   :practice: T
   :topics: TransformingSequences/WPAccumulatorPatternStrategies

   Dado que queremos acumular el número total de cadenas en la lista, ¿cuál de los siguientes patrones de acumulador sería apropiado?

   1.
   
   .. sourcecode:: python
   
    lst = ['plan', 'answer', 5, 9.29, 'order, items', [4]]
    s = 0
    for n in lst:
        s = s + n
   
   2.
   
   .. sourcecode:: python
   
    lst = ['plan', 'answer', 5, 9.29, 'order, items', [4]]
    for item in lst:
        s = 0
        if type(item) == type("string"):
            s = s + 1
   
   3.

   .. sourcecode:: python
   
    lst = ['plan', 'answer', 5, 9.29, 'order, items', [4]]
    s = ""
    for n in lst:
        s = s + n
   
   4.
   
   .. sourcecode:: python
   
    lst = ['plan', 'answer', 5, 9.29, 'order, items', [4]]
    s = 0
    for item in lst:
        if type(item) == type("string"):
            s = s + 1
 
.. mchoice:: assess_question5_2_1_3
   :multiple_answers:
   :answer_a: sum
   :answer_b: x
   :answer_c: total
   :answer_d: accum
   :answer_e: Ninguna de las anteriores
   :correct: c,d
   :feedback_a: No, aunque la suma podría ser clara, también es el nombre de una función de uso común en Python, por lo que puede haber problemas si la suma se usa como una variable acumuladora.
   :feedback_b: No, x no es un nombre lo suficientemente claro como para ser usado para una variable acumuladora.
   :feedback_c: Sí, total es un buen nombre para acumular números.
   :feedback_d: Sí, accum es un buen nombre. Es corto y fácil de recordar.
   :feedback_e: Al menos una de las respuestas anteriores es un buen nombre para una variable acumuladora.
   :practice: T
   :topics: TransformingSequences/WPAccumulatorPatternStrategies

   ¿Cuáles de estos son buenos nombres para una variable acumuladora? Selecciona todas las que apliquen.

.. mchoice:: assess_question5_2_1_4
   :multiple_answers:
   :answer_a: item
   :answer_b: y
   :answer_c: elem
   :answer_d: char
   :answer_e: Ninguna de las anteriores
   :correct: a,c,d
   :feedback_a: Sí, el elemento puede ser un buen nombre para usar como variable iteradora.
   :feedback_b: No, es probable que y no sea un nombre claro para la variable iteradora.
   :feedback_c: Sí, elem puede ser un buen nombre para usar como variable iteradora, especialmente cuando se repite en listas.
   :feedback_d: Sí, char puede ser un buen nombre para usar al iterar sobre una cadena, porque a la variable iteradora se le asignaría un carácter cada vez.
   :feedback_e: Al menos una de las respuestas anteriores es un buen nombre para una variable iteradora.
   :practice: T
   :topics: TransformingSequences/WPAccumulatorPatternStrategies

   ¿Cuáles de estos son buenos nombres para una variable iterador (bucle)? Selecciona todas las que apliquen.

.. mchoice:: assess_question5_2_1_5
   :multiple_answers:
   :answer_a: num_lst
   :answer_b: p
   :answer_c: sentence
   :answer_d: names
   :answer_e: ninguna de las anteriores
   :correct: a,c,d
   :feedback_a: Sí, num_lst es bueno para una variable de secuencia si el valor es en realidad una lista de números.
   :feedback_b: No, es probable que p no sea un nombre claro para la variable iteradora.
   :feedback_c: Sí, es bueno usarlo si el ciclo for está iterando a través de una cadena.
   :feedback_d: Sí, los nombres son buenos, suponiendo que el ciclo for esté iterando a través de nombres reales y no algo no relacionado con los nombres.
   :feedback_e: Al menos una de las respuestas anteriores es un buen nombre para una variable de secuencia
   :practice: T
   :topics: TransformingSequences/WPAccumulatorPatternStrategies

   ¿Cuáles de estos son buenos nombres para una variable de secuencia? Selecciona todas las que apliquen.

.. mchoice:: assess_question5_2_1_6
   :answer_a: variable acumuladora: x | variable iteradora: s | variable de secuencia: lst
   :answer_b: variable acumuladora: total | variable iteradora: s | variable de secuencia: lst
   :answer_c: variable acumuladora: x | variable iteradora: sentences | variable de secuencia: sentence_lst
   :answer_d: variable acumuladora: total | variable iteradora: sentence | variable de secuencia: sentence_lst
   :answer_e: Ninguna de las anteriores
   :correct: d
   :feedback_a: Aunque lst es un nombre aceptable, x y s no son nombres informativos para las variables de acumulador e iterador.
   :feedback_b: Aunque total es excelente y lst es un nombre aceptable, s es un poco críptico como un nombre variable que se refiere a una oración.
   :feedback_c: Aunque sentence_lst es un buen nombre, la variable iteradora debe ser singular en lugar de plural, y x no es un nombre informativo para la variable acumuladora.
   :feedback_d: Sí, esta combinación de nombres de variables es la más clara.
   :feedback_e: Una de las opciones anteriores tiene buenos nombres para el escenario.
   :practice: T
   :topics: TransformingSequences/WPAccumulatorPatternStrategies

   Dado el siguiente escenario, ¿cuáles son los buenos nombres para la variable acumuladora, la variable iteradora y la variable de secuencia? Está escribiendo un código que usa una lista de oraciones y acumula el número total de oraciones que tienen la palabra 'happy' en ellas.

.. activecode:: access_ac_5_2_1_1
   :language: python
   :autograde: unittest
   :practice: T
   :topics: TransformingSequences/TheAccumulatorPatternwithStrings

   Para cada carácter en la cadena guardada en ``ael``, agregue ese carácter a una lista que debe guardarse en una variable ``app``.
   ~~~~
   ael = "python!"

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(app, ['p','y','t','h','o','n', "!"], "Testing that app has the correct elements." )
         self.assertIn('append', self.getEditorText(), "Testing that your code uses append.")

   myTests().main()

.. activecode:: access_ac_5_2_1_2
   :language: python
   :autograde: unittest
   :practice: T
   :topics: TransformingSequences/TheAccumulatorPatternwithLists

   Para cada cadena en ``wrds``, agregue 'ed' al final de la palabra (para conjugar la palabra en tiempo pasado). Guarde estas palabras en tiempo pasado en una lista llamada ``past_wrds``.
   ~~~~
   wrds = ["end", 'work', "play", "start", "walk", "look", "open", "rain", "learn", "clean"]
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(past_wrds, ["ended", 'worked', "played", "started", "walked", "looked", "opened", "rained", "learned", "cleaned"], "Testing that past_wrds has the correct value." )

   myTests().main()

.. activecode:: assess_ps_02_06
    :language: python
    :autograde: unittest
    :practice: T
    :topics: TransformingSequences/TheAccumulatorPatternwithLists

    Escriba código para crear una **lista de longitudes de palabras** para las palabras en ``original_str`` usando el patrón de acumulación y asigne la respuesta a una variable ``num_words_list``. (Debe usar la función ``len``).

    ~~~~
    original_str = "The quick brown rhino jumped over the extremely lazy fox"


    =====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

        def testOne(self):
           self.assertEqual(num_words_list, map(len, original_str.split()), "Testing whether num_words_list has the correct value")
           self.assertIn('for', self.getEditorText(), "Testing that you are using a for loop in your code.")

    myTests().main()


.. activecode:: assess_pc_02_10
   :language: python
   :autograde: unittest
   :practice: T
   :topics: TransformingSequences/TheAccumulatorPatternwithStrings

   Cree una cadena vacía y asígnela a la variable ``lett``. Luego, usando el rango, escriba el código de manera que cuando se ejecute su código, ``lett`` tenga 7 b (``"bbbbbbb"``).
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(lett, "bbbbbbb", "Testing that lett has the correct value." )
         self.assertNotIn("bbbbbbb", self.getEditorText(), "Testing that you didn't hardcode the answer.")

   myTests().main()

Evaluación del capítulo: resolución de problemas
=================================================

.. activecode:: asign_c01_01
   :language: python
   :autograde: unittest
   :practice: T
   :topics: TransformingSequences/TheAccumulatorPatternwithStrings

   A continuación hay un conjunto de puntajes que los estudiantes han recibido en el semestre pasado. Escriba el código para determinar cuántos son de 90 o más y asigne ese resultado al valor ``a_scores``.
   ~~~~
   scores = "67 80 90 78 93 20 79 89 96 97 92 88 79 68 58 90 98 100 79 74 83 88 80 86 85 70 90 100"

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(a_scores, 10, "Testing that you got the right count.")
         self.assertIn('for', self.getEditorText(), "Testing that you used a for loop.")
         self.assertIn('if', self.getEditorText(), "Testing that you used a conditional.")

   myTests().main()

.. activecode:: asign_c01_02
   :language: python
   :autograde: unittest
   :practice: T
   :topics: TransformingSequences/TheAccumulatorPatternwithStrings

   Escriba el código que usa la cadena almacenada en ``org`` y crea un acrónimo que se asigna a la variable ``acro``. Solo se debe usar la primera letra de cada palabra, cada letra del acrónimo debe ser mayúscula y no debe haber nada que separe las letras del acrónimo. Las palabras que no deben incluirse en el acrónimo se almacenan en la lista ``stopwords``. Por ejemplo, si a ``org`` se le asignó la cadena "hello to world", el acrónimo resultante debería ser "HW".
   ~~~~
   stopwords = ['to', 'a', 'for', 'by', 'an', 'am', 'the', 'so', 'it', 'and', "The"]
   org = "The organization for health, safety, and education"

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(acro, 'OHSE', 'Checking that acro has been set correctly.')
         self.assertTrue(type(acro) == type("string"), "Checking that acro is a string.")
         self.assertIn('for', self.getEditorText(), "Testing that you used a for loop.")

   myTests().main()

.. activecode:: asign_c01_03
   :language: python
   :autograde: unittest
   :practice: T
   :topics: TransformingSequences/TheAccumulatorPatternwithStrings

   Escriba el código que usa la cadena almacenada en ``sent`` y crea un acrónimo que se asigna a la variable ``acro``. Deben usarse las dos primeras letras de cada palabra, cada letra en el acrónimo debe ser una letra mayúscula y cada elemento del acrónimo debe estar separado por un ". " (Punto y espacio). Las palabras que no deben incluirse en el acrónimo se almacenan en la lista ``stopwords``. Por ejemplo, si a ``sent`` se le asignó la cadena "height and ewok wonder", entonces el acrónimo resultante debería ser "HE. EW. WO".
   ~~~~
   stopwords = ['to', 'a', 'for', 'by', 'an', 'am', 'the', 'so', 'it', 'and', 'The']
   sent = "The water earth and air are vital"

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(acro, 'WA. EA. AI. AR. VI', 'Checking that acro has been set correctly.')
         self.assertTrue(type(acro) == type("string"), "Checking that acro is a string.")
         self.assertIn('for', self.getEditorText(), "Testing that you used a for loop.")

   myTests().main()

.. activecode:: asign_c01_04
   :language: python
   :autograde: unittest
   :practice: T
   :topics: TransformingSequences/TheAccumulatorPatternwithStrings

   Un palíndromo es una frase que, si se invierte, se leería exactamente igual. Escriba un código que verifique si ``p_phrase`` es un palíndromo invirtiéndolo y luego verificando si la versión invertida es igual a la original. Asigne la versión invertida de ``p_phrase`` a la variable ``r_phrase`` para que podamos verificar su trabajo.
   ~~~~
   p_phrase = "was it a car or a cat I saw"

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(r_phrase, "was I tac a ro rac a ti saw", "checking that r_phrase is set correctly")
         stripped_phrase = p_phrase.replace(" ", "").lower()
         stripped_r_phrase = r_phrase.replace(" ", "").lower()
         self.assertEqual(stripped_phrase, stripped_r_phrase, "checking that r_phrase and p_phrase are equivalent if the spaces are placed in the correct locations.")
         self.assertIsNot(p_phrase, r_phrase, "checking that r_phrase and p_phrase are not the same object.")

   myTests().main()

.. activecode:: asign_c01_05
   :language: python
   :autograde: unittest
   :practice: T
   :topics: TransformingSequences/NonmutatingMethodsonStrings

   Se proporciona una lista de datos sobre el inventario de una tienda donde cada artículo de la lista representa el nombre de un artículo, cuánto hay en stock y cuánto cuesta. Imprima cada elemento de la lista con el mismo formato, utilizando el método .format (no la concatenación de cadenas). Por ejemplo, la primera declaración impresa debería decir ``The store has 12 shoes, each for 29.99 USD.``.
   ~~~~
   inventory = ["shoes, 12, 29.99", "shirts, 20, 9.99", "sweatpants, 25, 15.00", "scarves, 13, 7.75"]


   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
          self.assertIn('for', self.getEditorText(), "Testing whether your code includes a for loop.")
          self.assertIn('.format(', self.getEditorText(), "Testing whether your code invokes the .format method.")
          self.assertIn('The store has 12 shoes, each for 29.99 USD.\nThe store has 20 shirts, each for 9.99 USD.\nThe store has 25 sweatpants, each for 15.00 USD.\nThe store has 13 scarves, each for 7.75 USD.\n', self.getOutput(), "Testing your output.")

         

   myTests().main()
