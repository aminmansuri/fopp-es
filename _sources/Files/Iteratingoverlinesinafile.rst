..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: files-5-
   :start: 1

Iterando sobre líneas en un archivo
-----------------------------------

Ahora usaremos este archivo como entrada en un programa que procesará algunos datos. En el programa, haremos que
examine cada línea del archivo e imprímalo con texto adicional. Porque ``readlines()`` devuelve una lista de
líneas de texto, podemos usar el bucle *for* para recorrer cada línea del archivo.

Una **línea** de un archivo se define como una secuencia de caracteres hasta e incluyendo un carácter especial llamado
caracter **newline**. Si evalúa un string que contiene un caracter newline, verá el caracter
representado como ``\n``. Si imprime una cadena que contiene newline, no verá el ``\n``, solo verá
sus efectos (un retorno de carro).

A medida que el bucle *for* recorre cada línea del archivo, la variable del bucle contendrá la línea actual del
archivo como un string. El patrón general para procesar cada línea de un archivo de texto es el siguiente:

::

        for line in myFile.readlines():
            statement1
            statement2
            ...

Para procesar todos nuestros datos olímpicos, utilizaremos un bucle *for* para iterar sobre las líneas del archivo. Utilizando
el método ``split``, podemos dividir cada línea en una lista que contiene todos los campos de interés sobre el
atleta. Luego podemos tomar los valores correspondientes a nombre, equipo y evento a
construir una oración simple.

.. activecode:: ac9_5_1

    olypmicsfile = open("olypmics.txt","r")

    for aline in olypmicsfile.readlines():
        values = aline.split(",")
        print(values[0], "es desde", values[3], "y está en la lista de", values[4])

    olypmicsfile.close()

Para simplificar un poco el código y permitir un procesamiento más eficiente, Python proporciona una forma integrada de
iterar a través del contenido de un archivo línea por línea, sin leerlos primero en una lista. Algunos estudiantes encuentran esto confuso inicialmente, por lo que no recomendamos hacerlo de esta manera, hasta que obtenga un
poco más cómodo con Python. Pero este lenguaje es preferido por los programadores de Python, por lo que debes estar preparado
para leerlo Y cuando comience a lidiar con archivos grandes, puede notar las ganancias de eficiencia de usarlo.

.. activecode:: ac9_5_2

    olypmicsfile = open("olypmics.txt","r")

    for aline in olypmicsfile:
        values = aline.split(",")
        print(values[0], "es desde", values[3], "y está en la lista de", values[4])

    olypmicsfile.close()

.. raw:: html

    <pre hidden id="olypmics.txt">
    Name,Sex,Age,Team,Event,Medal
    A Dijiang,M,24,China,Basketball,NA
    A Lamusi,M,23,China,Judo,NA
    Gunnar Nielsen Aaby,M,24,Denmark,Football,NA
    Edgar Lindenau Aabye,M,34,Denmark/Sweden,Tug-Of-War,Gold
    Christine Jacoba Aaftink,F,21,Netherlands,Speed Skating,NA
    Christine Jacoba Aaftink,F,25,Netherlands,Speed Skating,NA
    Christine Jacoba Aaftink,F,25,Netherlands,Speed Skating,NA
    Christine Jacoba Aaftink,F,27,Netherlands,Speed Skating,NA
    Per Knut Aaland,M,31,United States,Cross Country Skiing,NA
    Per Knut Aaland,M,33,United States,Cross Country Skiing,NA
    John Aalberg,M,31,United States,Cross Country Skiing,NA
    John Aalberg,M,33,United States,Cross Country Skiing,NA
    "Cornelia ""Cor"" Aalten (-Strannood)",F,18,Netherlands,Athletics,NA
    "Cornelia ""Cor"" Aalten (-Strannood)",F,18,Netherlands,Athletics,NA
    Antti Sami Aalto,M,26,Finland,Ice Hockey,NA
    "Einar Ferdinand ""Einari"" Aalto",M,26,Finland,Swimming,NA
    Jorma Ilmari Aalto,M,22,Finland,Cross Country Skiing,NA
    Jyri Tapani Aalto,M,31,Finland,Badminton,NA
    Minna Maarit Aalto,F,30,Finland,Sailing,NA
    Minna Maarit Aalto,F,34,Finland,Sailing,NA
    Pirjo Hannele Aalto (Mattila-),F,32,Finland,Biathlon,NA
    Timo Antero Aaltonen,M,31,Finland,Athletics,NA
    Win Valdemar Aaltonen,M,54,Finland,Art Competitions,NA
    </pre>


**Revisa tu entedimiento**

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

.. activecode:: ac9_5_3
   :available_files: emotion_words.txt
   :language: python
   :autograde: unittest
   :practice: T

   1. Escriba el código para averiguar cuántas líneas hay en el archivo ``emotion_words.txt`` como se muestra arriba. Guarde este valor en la variable ``num_lines``. No use el método len.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(num_lines, 7, "Testing that num_lines was assigned to the correct value.")
         self.assertNotIn('len', self.getEditorText(), "Testing your code (Don't worry about actual and expected values).")

   myTests().main() 
