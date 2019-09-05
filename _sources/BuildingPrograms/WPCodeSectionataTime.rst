..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: buildP-3-
   :start: 1

👩‍💻 Codificar una sección a la vez
====================================

Como recordatorio, este es nuestro aviso:

*Cree un programa que reproduzca un diccionario físico que pueda usar. El programa debe tomar cinco entradas diferentes del usuario. Cada entrada tendrá dos palabras y crearemos un diccionario donde las palabras son las claves y los valores*.

¡Comenzaremos a construir las secciones de una en una ahora! Primero, necesitamos elegir un nombre para el diccionario. Intentaremos elegir un nombre claro para cada una de estas variables

.. activecode:: ac500_3_1
   
    # inicializa un diccionario
    user_dictionary = {}
    print("---------- keys in user_dictionary: " + str(list(user_dictionary.keys())) + " ----------")

    # escribe un bucle for que iterará cinco veces. ¡Puedo usar la función range para esto!

    # en el bucle for, debería solicitar la entrada del usuario

    # luego, debería separar las palabras

    # finalmente, debería agregar el par de valores clave al diccionario

Elegimos el nombre de la variable ``user_dictionary`` porque será un diccionario creado por un usuario. Otros nombres podrían ser
apropiados también! Aunque parezca innecesario, agregaremos una sentencia de impresión para recordarnos que ``user_dictionary`` está vacío.

¡Luego construiremos el bucle for!

.. activecode:: ac500_3_2
   
    # inicializa un diccionario
    user_dictionary = {}
    print("---------- keys in user_dictionary: " + str(list(user_dictionary.keys())) + " ----------")

    # escriba un bucle for que iterará cinco veces. ¡Puedo usar la función range para esto!
    for _ in range(5):
        print("---------- LOOP HAS STARTED ----------")
        # en el bucle for, debería solicitar la entrada del usuario

        # luego, debería separar las palabras

        # finalmente, debería agregar el par de valores clave al diccionario
        print("---------- LOOP HA TERMINADO ----------")

Si queremos asegurarnos de que el ciclo for esté iterando cinco veces, entonces podemos agregar estas sentencias de impresión para ejecutarlas de modo que podamos
Puede seguir el progreso del programa.

A continuación, ¡recibiremos la entrada del usuario!

.. activecode:: ac500_3_3
   
    # inicializa un diccionario
    user_dictionary = {}
    print("---------- keys in user_dictionary: " + str(list(user_dictionary.keys())) + " ----------")

    # escriba un bucle for que iterará cinco veces. ¡Puedo usar la función range para esto!
    for _ in range(5):
        print("---------- LOOP HAS STARTED ----------")
        # en el bucle for, debería solicitar la entrada del usuario
        response = input("Please enter two words to add to a dictionary. The first word is the definition, the second will be the word associated with it.")
        print("---------- The response: " + response + " ----------")

        # a continuación, debería separar las palabras

        # finalmente, debería agregar el par de valores clave al diccionario
        print("---------- LOOP HAS ENDED ----------")

Ahora queremos imprimir la respuesta. Esperamos que sea como una cadena, por lo que deberíamos poder agregarlo a la sentencia
print con otras cadenas sin ningún problema. Si hay un problema, entonces algo podría estar mal con la forma en que estamos recibiendo aportes
del usuario

¡Ahora, podemos separar las palabras para tener nuestra clave y valor para agregar al diccionario!

.. activecode:: ac500_3_4
   
    # inicializa un diccionario
    user_dictionary = {}
    print("---------- keys in user_dictionary: " + str(list(user_dictionary.keys())) + " ----------")

    # escriba un bucle for que iterará cinco veces. ¡Puedo usar la función range para esto!
    for _ in range(5):
        print("---------- LOOP HAS STARTED ----------")
        # en el bucle for, debería solicitar la entrada del usuario
        response = input("Please enter two words to add to a dictionary. The first word is the definition, the second will be the word associated with it.")
        print("---------- The response: " + response + " ----------")

        # a continuación, debería separar las palabras
        separated_response = response.split()
        print("---------- The separated response: " + str(separated_response) + " ----------")
        response_key = separated_response[0]
        print("---------- The response key: " + response_key + " ----------")
        response_value = separated_response[1]
        print("---------- The response value: " + response_value + " ----------")

        # finalmente, debería agregar el par de valores clave al diccionario
        print("---------- LOOP HAS ENDED ----------")

Aquí sabemos que ``response`` es una cadena que contiene dos palabras. Podemos usar el método de división para separar las palabras, lo que nos dará
una lista. La primera palabra será la clave y la segunda será el valor, por lo que podemos usar la indexación para acceder a esa información.

.. activecode:: ac500_3_5
   
    # inicializa un diccionario
    user_dictionary = {}
    print("---------- keys in user_dictionary: " + str(list(user_dictionary.keys())) + " ----------")

    # escriba un bucle for que iterará cinco veces. ¡Puedo usar la función range para esto!
    for _ in range(5):
        print("---------- LOOP HAS STARTED ----------")
        # en el bucle for, debería solicitar la entrada del usuario
        response = input("Please enter two words to add to a dictionary. The first word is the definition, the second will be the word associated with it.")
        print("---------- The response: " + response + " ----------")

        # a continuación, debería separar las palabras
        separated_response = response.split()
        print("---------- The separated response: " + str(separated_response) + " ----------")
        response_key = separated_response[0]
        print("---------- The response key: " + response_key + " ----------")
        response_value = separated_response[1]
        print("---------- The response value: " + response_value + " ----------")

        # finalmente, debería agregar el par de valores clave al diccionario
        user_dictionary[response_key] = response_value
        print("---------- LOOP HAS ENDED ----------")

    print("---------- The user dictionary")
    print(user_dictionary)
    print("----------")

Finalmente, agregamos código para agregar el par clave y valor en un diccionario. Podemos imprimir el resultado final del diccionario una vez que
el ciclo ha terminado para que podamos determinar si se ha realizado correctamente.
