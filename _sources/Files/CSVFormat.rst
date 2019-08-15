..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: files-8-
   :start: 1

Formato CSV
===========

CSV significa valores separados por comas. Si imprime datos tabulares en formato CSV, puede importarse fácilmente a otros programas como Excel, hojas de cálculo de Google o un paquete de estadísticas (R, stata, SPSS, etc.).

Por ejemplo, podemos hacer un archivo con los siguientes contenidos. Si lo guarda como un nombre de archivo ratings.csv, puede importarlo a uno de esos programas. La primera línea proporciona los nombres de las columnas y las líneas posteriores proporcionan los datos para una fila.

.. sourcecode:: python

   Name,score,grade
   Jamal,98,A+
   Eloise,87,B+
   Madeline,99,A+
   Wei,94,A
