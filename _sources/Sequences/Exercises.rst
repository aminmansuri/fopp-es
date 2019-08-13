..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

:skipreading:`True`

.. qnum::
   :prefix: seq-11-
   :start: 1

Ejercicios
----------

#.

   .. parsonsprob:: pp5_11_1

      Escriba un programa que imprima la longitud de cada elemento de la lista, así como el primer y último carácter del elemento.
      -----
      weather = ["sunny", "cloudy", "partially sunny", 
                 "rainy", "storming", "windy", "foggy", 
                 "snowy", "hailing"]
      =====
      por condición climática:
      =====
          print("La palabra es", len(condition), "characters")
      =====
          first_char = condition[0]
          last_char = condition[-1]
      =====
          print("El primer caracter es: " + first_char)
          print("El último caracter es: " + last_char)

#.

   .. parsonsprob:: pp5_11_2

      Escriba el código para determinar cuántas t hay en las siguientes oraciones.
      -----
      phrases = ["My, what a lovely day today is!", 
      "Have you mastered cooking yet? A tasty treat could be in your future.", 
      "Have you ever seen the leaves change color?"]
      =====
      para las oración en frases:
      =====
          print(sentence.count("t"))

