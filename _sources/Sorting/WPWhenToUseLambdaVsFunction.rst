..  Copyright (C) Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: sort-6-
   :start: 1


👩‍💻 Cuándo usar una expresión lambda
------------------------------------------

Aunque a menudo puede usar una expresión lambda o una función con nombre de manera intercambiable al ordenar, generalmente es mejor usar expresiones lambda hasta que el proceso sea demasiado complicado, y luego se debe usar una función. Por ejemplo, en los siguientes ejemplos, clasificaremos las claves de un diccionario por las propiedades de sus valores. Cada clave es un nombre de estado y cada valor es una lista de nombres de ciudades.

Para nuestro primer orden de clasificación, queremos ordenar los estados en orden por la longitud del primer nombre de ciudad. Aquí, es bastante fácil calcular esa propiedad. ``states[state]`` es la lista de ciudades asociadas con un estado en particular. Entonces, si ``state`` es una lista de strings de ciudades, ``len(states[state][0])`` es la longitud del primer nombre de ciudad. Por lo tanto, podemos usar una expresión lambda:

.. activecode:: ac18_6_1

    states = {"Minnesota": ["St. Paul", "Minneapolis", "Saint Cloud", "Stillwater"],
              "Michigan": ["Ann Arbor", "Traverse City", "Lansing", "Kalamazoo"],
              "Washington": ["Seattle", "Tacoma", "Olympia", "Vancouver"]}

    print(sorted(states, key=lambda state: len(states[state][0])))

Eso ya está empujando los límites de lo complejo que puede ser una expresión lambda antes de que sea realmente difícil de leer (o depurar).

Para nuestro segundo orden de clasificación, la propiedad por la que queremos clasificar es el número de ciudades que comienzan con la letra 'S'. La función que define esta propiedad es más difícil de expresar, ya que requiere un filtro y un patrón de acumulación de conteo. Por lo tanto, es mejor definir una función separada con nombre. Aquí, hemos optado por hacer una expresión lambda que busque el valor asociado con el estado particular y pasar ese valor a la función nombrada `s_cities_count`. Podríamos haber pasado solo la clave, pero entonces la función tendría que buscar el valor, y sería un poco confuso, a partir del código, averiguar en qué diccionario se supone que debe buscarse la clave. Aquí, nosotros hicmimos la búsqueda directamente en la expresión lambda, lo que deja un poco más claro que solo estamos ordenando las claves del diccionario de estados en función de una propiedad de sus valores. También facilita la reutilización de la función de conteo en otras listas de ciudades, incluso si no están integradas en ese diccionario de estados en particular.

.. activecode:: ac18_6_2

    def s_cities_count(city_list):
        ct = 0
        for city in city_list:
            if city[0] == "S":
                ct += 1
        return ct

    states = {"Minnesota": ["St. Paul", "Minneapolis", "Saint Cloud", "Stillwater"],
              "Michigan": ["Ann Arbor", "Traverse City", "Lansing", "Kalamazoo"],
              "Washington": ["Seattle", "Tacoma", "Olympia", "Vancouver"]}

    print(sorted(states, key=lambda state: s_cities_count(states[state])))

En este punto del curso, ni siquiera sabemos cómo hacer ese filtro y acumulación como parte de una expresión lambda. Hay una manera, usando algo llamado listas de comprensión, pero aún no lo hemos cubierto.

Habrá otras situaciones que son aún más complicadas que esta. ¡En algunos casos, pueden ser demasiado complicados de resolver con una expresión lambda! Siempre puede recurrir a escribir una función con nombre cuando una expresión lambda será demasiado complicada.
