..  Copyright (C) Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. _sort_stable:

.. qnum::
   :prefix: sort-5-
   :start: 1

Romper Lazos: segunda clasificación
----------------------------------------

¿Qué sucede cuando dos artículos están "tied" *atados* en el orden de clasificación? Por ejemplo, supongamos que ordenamos una lista de palabras por su longitud.
¿Qué palabra de cinco letras aparecerá primero?

La respuesta es que el intérprete de Python clasificará los elementos vinculados en el mismo orden en que estaban antes de la clasificación.

¿Qué pasaría si quisiéramos ordenarlos por alguna otra propiedad, digamos alfabéticamente, cuando las palabras tenían la misma longitud? Python nos permite especificar múltiples condiciones cuando realizamos una ordenación al devolver una tupla de una función clave.

Primero, veamos cómo Python clasifica las tuplas. Ya hemos visto que hay un orden de clasificación incorporado, si no especificamos ninguna función clave. Para los números, es de menor a mayor. Para strings, es el orden alfabético. Para una secuencia de tuplas, el orden de clasificación predeterminado se basa en el orden de clasificación predeterminado para los primeros elementos de las tuplas, con lazos rotos por los segundos elementos y luego los terceros elementos si es necesario, etc. Por ejemplo,

.. activecode:: ac18_5_0

    tups = [('A', 3, 2),
            ('C', 1, 4),
            ('B', 3, 1),
            ('A', 2, 4),
            ('C', 1, 2)]
    for tup in sorted(tups):
        print(tup)

En el siguiente código, vamos a ordenar una lista de palabras de fruta primero por su longitud, de menor a mayor, y luego alfabéticamente para romper los lazos entre palabras de la misma longitud. Para hacer eso, tenemos la función de tecla de devolver una tupla cuyo primer elemento es la longitud del nombre de la fruta, y el segundo elemento es el nombre de la fruta en sí.

.. activecode:: ac18_5_1

    fruits = ['peach', 'kiwi', 'apple', 'blueberry', 'papaya', 'mango', 'pear']
    new_order = sorted(fruits, key=lambda fruit_name: (len(fruit_name), fruit_name))
    for fruit in new_order:
        print(fruit)

Aquí, cada palabra se evalúa primero en su longitud, luego por su orden alfabético. Tenga en cuenta que podríamos seguir especificando otras condiciones al incluir más elementos en la tupla.

¿Qué pasaría si quisiéramos ordenarlo de mayor a menor y luego por orden alfabético?

.. activecode:: ac18_5_2

    fruits = ['peach', 'kiwi', 'apple', 'blueberry', 'papaya', 'mango', 'pear']
    new_order = sorted(fruits, key=lambda fruit_name: (len(fruit_name), fruit_name), reverse=True)
    for fruit in new_order:
        print(fruit)

¿Ves un problema aquí? ¡No solo ordena las palabras de mayor a menor, sino también en orden alfabético inverso! ¿Puedes pensar en alguna forma de resolver este problema?

Una solución es agregar un signo negativo delante de ``len(fruit_name)``, que convertirá todos los números positivos a negativos y todos los números negativos a positivos. Como resultado, los elementos más largos serían los primeros y los elementos más cortos serían los últimos.

.. activecode:: ac18_5_3

    fruits = ['peach', 'kiwi', 'apple', 'blueberry', 'papaya', 'mango', 'pear']
    new_order = sorted(fruits, key=lambda fruit_name: (-len(fruit_name), fruit_name))
    for fruit in new_order:
        print(fruit)
   
Podemos usar esto para cualquier valor numérico que queramos ordenar, sin embargo, esto no funcionará para cadenas.

**Revisa tu entendimiento**

.. mchoice:: question18_5_1
      :answer_a: primer nombre de la ciudad (alfabéticamente), luego temperatura (de menor a mayor)
      :answer_b: primera temperatura (de mayor a menor), luego nombre de la ciudad (alfabéticamente)
      :answer_c: primer nombre de ciudad (alfabéticamente), luego temperatura (de mayor a menor)
      :answer_d: primera temperatura (de menor a mayor), luego el nombre de la ciudad (alfabéticamente)
      :feedback_a: ¡Correcto! Primero ordenamos alfabéticamente por nombre de ciudad, luego por temperatura, de menor a mayor.
      :feedback_b: El orden de la tupla importa. El primer elemento de la tupla es la primera condición utilizada para ordenar.
      :feedback_c: No del todo, recuerde que, de manera predeterminada, la función ordenada se ordenará por orden alfabético, o de menor a mayor. ¿El parámetro inverso está configurado en Verdadero? ¿Se ha usado un signo negativo en el parámetro clave?
      :feedback_d: El orden de la tupla importa. El primer elemento de la tupla es la primera condición utilizada para ordenar.
      :correct: a
      :practice: T

      ¿Por qué ordenará la función ordenada?

      .. code-block:: python

         weather = {'Reykjavik': {'temp':60, 'condition': 'rainy'}, 
                    'Buenos Aires': {'temp': 55, 'condition': 'cloudy'}, 
                    'Cairo': {'temp': 96, 'condition': 'sunny'}, 
                    'Berlin': {'temp': 89, 'condition': 'sunny'}, 
                    'Caloocan': {'temp': 78, 'condition': 'sunny'}}

         sorted_weather = sorted(weather, key=lambda w: (w, weather[w]['temp']))

.. mchoice:: question18_5_2
      :answer_a: primer nombre de la ciudad (en orden alfabético inverso), luego temperatura (de menor a mayor)
      :answer_b: primera temperatura (de mayor a menor), luego nombre de la ciudad (alfabéticamente)
      :answer_c: primer nombre de la ciudad (en orden alfabético inverso), luego temperatura (de mayor a menor)
      :answer_d: primera temperatura (de menor a mayor), luego el nombre de la ciudad (alfabéticamente)
      :answer_e: primer nombre de la ciudad (alfabéticamente), luego temperatura (de menor a mayor)
      :feedback_a: ¡Correcto! En este caso, el parámetro inverso hará que el nombre del país se ordene alfabéticamente en lugar de alfabéticamente, y también negará el signo negativo frente a la temperatura.
      :feedback_b: El orden de la tupla importa. El primer elemento de la tupla es la primera condición utilizada para ordenar. Además, tome nota del parámetro inverso: ¿qué hará en este caso?
      :feedback_c: No del todo: ¿el parámetro inverso está establecido en True? ¿Se ha usado un signo negativo en el parámetro clave? ¿Qué sucede cuando ambos se usan?
      :feedback_d: El orden de la tupla importa. El primer elemento de la tupla es la primera condición utilizada para ordenar.
      :feedback_e: No del todo, recuerde que, de forma predeterminada, la función ordenada se ordenará por orden alfabético, o de menor a mayor. ¿El parámetro inverso está configurado en Verdadero? ¿Se ha usado un signo negativo en el parámetro clave?
      :correct: a
      :practice: T

      ¿Cómo se ordenarán los siguientes datos?

      .. code-block:: python

         weather = {'Reykjavik': {'temp':60, 'condition': 'rainy'}, 
                    'Buenos Aires': {'temp': 55, 'condition': 'cloudy'}, 
                    'Cairo': {'temp': 96, 'condition': 'sunny'}, 
                    'Berlin': {'temp': 89, 'condition': 'sunny'}, 
                    'Caloocan': {'temp': 78, 'condition': 'sunny'}}

         sorted_weather = sorted(weather, key=lambda w: (w, -weather[w]['temp']), reverse=True)
