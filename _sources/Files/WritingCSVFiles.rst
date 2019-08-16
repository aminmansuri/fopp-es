
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

Escribir datos en un archivo CSV
====================================

El patrón típico para escribir datos en un archivo CSV será escribir una fila de encabezado y un bucle
a través de los elementos en una lista, generando una fila para
cada una. Aquí tenemos una lista de tuples, cada una representando a un olímpico, un subconjunto de las filas y columnas del archivo del que hemos estado leyendo.

.. activecode:: ac9_14_1

   olympians = [("John Aalberg", 31, "Cross Country Skiing"),
               ("Minna Maarit Aalto", 30, "Sailing"),
               ("Win Valdemar Aaltonen", 54, "Art Competitions"),
               ("Wakako Abe", 18, "Cycling")]

   outfile = open("reduced_olympics.csv","w")
   # salida de la fila del encabezado
   outfile.write('Name,Age,Sport')
   outfile.write('\n')
   # salida de cada una de las filas:
   for olympian in olympians:
       row_string = '{},{},{}'.format(olympian[0], olympian[1], olympian[2])
       outfile.write(row_string)
       outfile.write('\n')
   outfile.close()
   
Hay algunas cosas que vale la pena señalar en el código anterior.

Primero, usar .format() deja muy claro lo que estamos haciendo cuando creamos la variable row_string. Estamos haciendo un conjunto de valores separados por comas; las {} llaves indicaron dónde sustituir en los valores reales. La concatenación de cadena equivalente sería muy difícil de leer. Una alternativa, también una forma clara de hacerlo sería con el método .join : ``row_string = ','.join(olympian[0], olympian[1], olympian[2])``.

Segundo, a diferencia de la declaración de impresión, recuerde que el método .write() en un objeto de archivo no inserta automáticamente una nueva línea. En cambio, tenemos que agregar explícitamente el carácter ``\n`` al final de cada línea.

Tercero, tenemos que referirnos explícitamente a cada uno de los elementos de Olympian cuando construimos lel string para escribir. Tenga en cuenta que simplemente poner ``.format(olympian)`` no funcionaría porque el intérprete vería solo un valor (un tuple) cuando esperaba tres valores para intentar sustituir en la plantilla de string. Más adelante en el libro veremos que Python proporciona una técnica avanzada para desempaquetar automáticamente los tres valores de la tupla, con ``.format(*olympian)``.

Como se describió anteriormente, si una o más columnas contienen texto, y ese texto podría contener comas, debemos hacer algo
para distinguir una coma en el texto de una coma que separa diferentes valores (celdas en la
mesa). Si queremos encerrar cada valor entre comillas dobles, puede comenzar a ser un poco complicado, porque lo que haremos
debe tener el carácter de comillas dobles dentro de la salida de la cadena. Pero es factible. De hecho,
la razón por la que Python permite que las cadenas se delimiten con comillas simples o comillas dobles es que
ese puede usarse para delimitar el string y el otro puede ser un caracter en el string. Si llega al punto en el que necesita citar todos los valores, le recomendamos aprender a usar el módulo csv de python.

.. activecode:: ac9_14_2

   olympians = [("John Aalberg", 31, "Cross Country Skiing, 15KM"),
               ("Minna Maarit Aalto", 30, "Sailing"),
               ("Win Valdemar Aaltonen", 54, "Art Competitions"),
               ("Wakako Abe", 18, "Cycling")]

   outfile = open("reduced_olympics2.csv","w")
   # salida de la fila del encabezado
   outfile.write('"Name","Age","Sport"')
   outfile.write('\n')
   # salida de cada una de las filas:
   for olympian in olympians:
       row_string = '"{}", "{}", "{}"'.format(olympian[0], olympian[1], olympian[2])
       outfile.write(row_string)
       outfile.write('\n')
   outfile.close()

