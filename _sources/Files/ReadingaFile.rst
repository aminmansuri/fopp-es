..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: files-3-
   :start: 1

Leer un archivo
~~~~~~~~~~~~~~~

Como ejemplo, supongamos que tenemos un archivo de texto llamado ``olympics.txt`` que contiene
los datos que representan a los olímpicos en diferentes años. El contenido del archivo se muestra en la parte inferior de la página.

Para abrir este archivo, llamaremos a la función ``open``. La variable,
``fileref``, ahora contiene una referencia al objeto de archivo devuelto por
``open``. Cuando hayamos terminado con el archivo, podemos cerrarlo usando
el método ``close``. Después de cerrar el archivo, cualquier otro intento de
el uso de ``fileref`` dará como resultado un error.

.. activecode:: ac9_2_1
    :available_files: olympics.txt

    fileref = open("olympics.txt","r")
    ## otro código aquí que se refiere a la variable fileref
    fileref.close()

.. note::

    Un error común es confundirse acerca de si está proporcionando un nombre de variable o un literal de string como entrada para la función abierta. En el código anterior, "olympics.txt" es un literal de string que debe corresponder al nombre de un archivo en su computadora. Si coloca algo sin comillas, como ``open(x, "r")``, se tratará como un nombre de variable. En este ejemplo, x debería ser una variable que ya se ha vinculado a un valor de string como "olympics.txt".

.. datafile:: olympics.txt

    Name,Sex,Age,Team,Event,Medal
    A Dijiang,M,24,China,Basketball,NA
    A Lamusi,M,23,China,Judo,NA
    Gunnar Nielsen Aaby,M,24,Denmark,Football,NA
    Edgar Lindenau Aabye,M,34,Denmark/Sweden,Tug-Of-War,Gold
    Christine Jacoba Aaftink,F,21,Netherlands,Speed Skating,NA
    Christine Jacoba Aaftink,F,21,Netherlands,Speed Skating,NA
    Christine Jacoba Aaftink,F,25,Netherlands,Speed Skating,NA
    Christine Jacoba Aaftink,F,25,Netherlands,Speed Skating,NA
    Christine Jacoba Aaftink,F,27,Netherlands,Speed Skating,NA
    Christine Jacoba Aaftink,F,27,Netherlands,Speed Skating,NA
    Per Knut Aaland,M,31,United States,Cross Country Skiing,NA
    Per Knut Aaland,M,31,United States,Cross Country Skiing,NA
    Per Knut Aaland,M,31,United States,Cross Country Skiing,NA
    Per Knut Aaland,M,31,United States,Cross Country Skiing,NA
    Per Knut Aaland,M,33,United States,Cross Country Skiing,NA
    Per Knut Aaland,M,33,United States,Cross Country Skiing,NA
    Per Knut Aaland,M,33,United States,Cross Country Skiing,NA
    Per Knut Aaland,M,33,United States,Cross Country Skiing,NA
    John Aalberg,M,31,United States,Cross Country Skiing,NA
    John Aalberg,M,31,United States,Cross Country Skiing,NA
    John Aalberg,M,31,United States,Cross Country Skiing,NA
    John Aalberg,M,31,United States,Cross Country Skiing,NA
    John Aalberg,M,33,United States,Cross Country Skiing,NA
    John Aalberg,M,33,United States,Cross Country Skiing,NA
    John Aalberg,M,33,United States,Cross Country Skiing,NA
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
    Arvo Ossian Aaltonen,M,22,Finland,Swimming,NA
    Arvo Ossian Aaltonen,M,22,Finland,Swimming,NA
    Arvo Ossian Aaltonen,M,30,Finland,Swimming,Bronze
    Arvo Ossian Aaltonen,M,30,Finland,Swimming,Bronze
    Arvo Ossian Aaltonen,M,34,Finland,Swimming,NA
    Juhamatti Tapio Aaltonen,M,28,Finland,Ice Hockey,Bronze
    Paavo Johannes Aaltonen,M,28,Finland,Gymnastics,Bronze
    Paavo Johannes Aaltonen,M,28,Finland,Gymnastics,Gold
    Paavo Johannes Aaltonen,M,28,Finland,Gymnastics,NA
    Paavo Johannes Aaltonen,M,28,Finland,Gymnastics,Gold
    Paavo Johannes Aaltonen,M,28,Finland,Gymnastics,NA
    Paavo Johannes Aaltonen,M,28,Finland,Gymnastics,NA
    Paavo Johannes Aaltonen,M,28,Finland,Gymnastics,NA
    Paavo Johannes Aaltonen,M,28,Finland,Gymnastics,Gold
    Paavo Johannes Aaltonen,M,32,Finland,Gymnastics,NA
    Paavo Johannes Aaltonen,M,32,Finland,Gymnastics,Bronze
    Paavo Johannes Aaltonen,M,32,Finland,Gymnastics,NA
    Paavo Johannes Aaltonen,M,32,Finland,Gymnastics,NA
    Paavo Johannes Aaltonen,M,32,Finland,Gymnastics,NA
    Paavo Johannes Aaltonen,M,32,Finland,Gymnastics,NA
    Paavo Johannes Aaltonen,M,32,Finland,Gymnastics,NA
    Paavo Johannes Aaltonen,M,32,Finland,Gymnastics,NA
    Timo Antero Aaltonen,M,31,Finland,Athletics,NA
    Win Valdemar Aaltonen,M,54,Finland,Art Competitions,NA
