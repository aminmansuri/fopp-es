..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: buildP-4-
   :start: 1

👩‍💻 Limpiar
==============

¡Felicidades! Hemos resuelto el problema ahora, pero nuestro código no es muy agradable de leer. Podemos limpiarlo ahora y eliminar las declaraciones de impresión.

.. activecode:: ac500_4_1
   
    # initialize a dictionary
    user_dictionary = {}

    # write a for loop that will iterate five times. I can use the range function for this!
    for _ in range(5):
        # in the for loop, I should ask for input from the user
        response = input("Please enter two words to add to a dictionary. The first word is the definition, the second will be the word associated with it.")

        # next, I should separate the words
        separated_response = response.split()
        response_key = separated_response[0]
        response_value = separated_response[1]

        # finally, I should add the key value pair to the dictionary
        user_dictionary[response_key] = response_value


También podemos corregir los comentarios para que no sean tan obvios.

.. activecode:: ac500_4_2
   
    user_dictionary = {}

    # le pide al usuario dos palabras para agregar al diccionario del usuario; lo hará cinco veces.
    # la primera palabra será la clave, la segunda palabra será el valor.
    for _ in range(5):
        response = input("Please enter two words to add to a dictionary. The first word is the definition, the second will be the word associated with it.")

        separated_response = response.split()
        response_key = separated_response[0]
        response_value = separated_response[1]

        user_dictionary[response_key] = response_value

En este punto, el código se ha limpiado completamente: puede escribir fácilmente los comentarios de una manera diferente, pero esto debería ser fácil de entender para otros programadores ¡y para nosotros mismos si volvemos al código días, semanas o meses después!