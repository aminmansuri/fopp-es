..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: files-13-
   :start: 1

Lectura de datos de un archivo CSV
==================================

Podemos leer en archivos CSV de la misma manera que lo hacemos con otros archivos de texto. Debido a la estructura estandarizada de los datos, existe un patrón común para procesarlos. Para practicar esto,
utilizaremos datos sobre eventos olímpicos.

Por lo general, los archivos CSV tendrán un encabezado como primera línea, que contiene los nombres de las columnas. Entonces,
cada fila siguiente en el archivo contendrá datos que corresponden a las columnas apropiadas.

Todos los métodos de archivo que hemos mencionado - ``read``, ``readline``, y ``readlines``, y simplemente iterar sobre el objeto del archivo en sí, funcionarán en archivos CSV. En nuestros ejemplos, iteraremos sobre las líneas. Debido a que los valores en cada línea están separados por comas, podemos usar el método ``.split()`` para analizar cada línea en una colección de valores separados.

.. activecode:: ac9_13_1

    fileconnection = open("olympics.txt", 'r')
    lines = fileconnection.readlines()
    header = lines[0]
    field_names = header.strip().split(',')
    print(field_names)
    for row in lines[1:]:
        vals = row.strip().split(',')
        if vals[5] != "NA":
            print("{}: {}; {}".format(
                    vals[0],
                    vals[4],
                    vals[5]))

En el código anterior, abrimos el archivo, olympics.txt, que contiene datos sobre algunos juegos olímpicos. El contenido es similar a nuestro archivo olímpico anterior, pero incluye una columna adicional con información sobre las medallas que ganaron.

Dividimos la primera fila para obtener los nombres de los campos. Dividimos otras filas para obtener valores. Tenga en cuenta que especificamos dividir en comas pasando eso como un parámetro. También tenga en cuenta que primero pasamos la fila a través del método .strip() para deshacernos del \n.

Una vez que hemos analizado las líneas en sus valores separados, podemos usar esos valores en el programa. Por ejemplo, en el código anterior, seleccionamos solo aquellas filas donde el olímpico ganó una medalla, e imprimimos solo tres de los campos, en un formato diferente.

Tenga en cuenta que el truco de dividir el texto para cada fila en función de la presencia de comas solo funciona porque las comas no se utilizan en ninguno de los valores de campo. Supongamos que algunos de nuestros eventos fueron más específicos y utilizaron comas. Por ejemplo, "Swimming, 100M Freestyle". ¿Cómo sabrá un programa que procesa un archivo .csv cuándo una coma está separando columnas y cuándo es solo parte de la cadena de texto que da un valor dentro de una columna?

El formato CSV es en realidad un poco más general de lo que hemos descrito y tiene un par de soluciones para ese problema. Un formato alternativo utiliza un separador de columna diferente, como | o una pestaña (\t). A veces, cuando se usa una pestaña, el formato se llama tsv, para valores separados por tabulaciones). Si obtiene un archivo usando un separador diferente, puede llamar a  ``.split('|')`` o ``.split('\\t')``.

El otro formato CSV avanzado usa comas para separar pero encierra todos los valores entre comillas dobles.

Por ejemplo, el archivo de datos podría verse así:

.. raw:: html

    <pre id="sample.txt">
    "Name","Sex","Age","Team","Event","Medal"
    "A Dijiang","M","24","China","Basketball","NA"
    "Edgar Lindenau Aabye","M","34","Denmark/Sweden","Tug-Of-War","Gold"
    "Christine Jacoba Aaftink","F","21","Netherlands","Speed Skating, 1500M","NA"
    </pre>

Si está leyendo un archivo .csv que ha encerrado todos los valores entre comillas dobles, en realidad es un problema de programación bastante complicado dividir el texto de una fila en una lista de valores. No querrás intentar hacerlo directamente. En su lugar, debe usar el módulo csv incorporado de python. Sin embargo, hay una pequeña curva de aprendizaje para eso, y descubrimos que los estudiantes obtienen una mejor comprensión de la lectura del formato CSV al aprender primero a leer el formato simple, sin comillas y las líneas divididas en comas.