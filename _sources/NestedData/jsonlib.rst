..  Copyright (C)  Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".


Procesando resultados JSON
===========================

JSON significa JavaScript Object Notation. Se parece mucho a la representación de diccionarios y listas anidados en
python cuando los escribimos como literales en un programa, pero con algunas pequeñas diferencias (por ejemplo, la palabra null en lugar de
None). Cuando su programa recibe una cadena con formato JSON, generalmente querrá convertirlo en un objeto de Python, una
lista o un diccionario.

Nuevamente, python proporciona un módulo para hacer esto. El módulo se llama json. Utilizaremos dos funciones en este módulo,
``loads`` y ``dumps``.

``json.loads()`` toma una cadena como entrada y produce un objeto python (un diccionario o una lista) como salida.

Considere, por ejemplo, algunos datos que podríamos obtener de iTunes de Apple, en formato JSON:

.. activecode:: ac17_3_1
    :language: python

    import json
    a_string = '\n\n\n{\n "resultCount":25,\n "results": [\n{"wrapperType":"track", "kind":"podcast", "collectionId":10892}]}'
    print(a_string)
    d = json.loads(a_string)
    print("------")
    print(type(d))
    print(d.keys())
    print(d['resultCount'])
    # print(a_string['resultCount'])

La otra función que usaremos es ``dumps``. Hace el inverso de ``loads``. Toma un objeto python, generalmente un diccionario o una lista, y devuelve una cadena, en formato JSON. Tiene algunos otros parámetros. Dos parámetros útiles son sort_keys e indent. Cuando se pasa el valor True para el parámetro sort_keys, las claves de los diccionarios se emiten en orden alfabético con sus valores. El parámetro de sangría espera un número entero. Cuando se proporciona, los volcados generan una cadena adecuada para mostrar a las personas, con nuevas líneas y sangría para listas anidadas o diccionarios. Por ejemplo, la siguiente función usa json.dumps para realizar una impresión legible por humanos de una estructura de datos anidada.

.. activecode:: ac17_3_2
    :language: python

    import json
    def pretty(obj):
        return json.dumps(obj, sort_keys=True, indent=2)

    d = {'key1': {'c': True, 'a': 90, 5: 50}, 'key2':{'b': 3, 'c': "yes"}}

    print(d)
    print('--------')
    print(pretty(d))

**Revisa tu entendimiento**

.. mchoice:: question17_3_1
   :answer_a: json.loads(d)
   :answer_b: json.dumps(d)
   :answer_c: d.json()
   :feedback_a: loads convierte una cadena con formato json en una lista o diccionario
   :feedback_b: dumps convierte una lista o diccionario en una cadena con formato json
   :feedback_c: .json() intenta invocar el método json, pero ese método no está definido para los diccionarios
   :correct: b
   :practice: T

   Como solo podemos escribir cadenas en un archivo, si quisiéramos convertir un diccionario `d` en una cadena con formato json para poder almacenarlo en un archivo, ¿qué usaríamos?

.. mchoice:: question17_3_2
   :multiple_answers:
   :answer_a: entertainment.json()
   :answer_b: json.dumps(entertainment)
   :answer_c: json.loads(entertainment)
   :feedback_a: El método .json() no está definido para strings.
   :feedback_b: dumps (dump to string) convierte una lista o diccionario en una cadena con formato json
   :feedback_c: loads (load from string) convierte una cadena con formato json en una lista o diccionario
   :correct: c
   :practice: T

   Digamos que teníamos un String JSON en el siguiente formato. ¿Cómo lo convertirías para que sea una lista de Python?

   .. sourcecode:: python

       entertainment = """[{"Library Data": {"count": 3500, "rows": 10, "locations": 3}}, {"Movie Theater Data": {"count": 8, "rows": 25, "locations": 2}}]"""
