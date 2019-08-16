..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: dictionaries-10-
   :start: 1

👩‍💻 Cuando Usar un Diccionario
--------------------------------

Ahora que tiene experiencia en el uso de listas y diccionarios, tendrá que decidir cuál es el mejor para cada situación. Las siguientes pautas le ayudarán a reconocer cuándo un diccionario será beneficioso:

* Cuando un dato consiste en un conjunto de propiedades de un solo elemento, un diccionario a menudo es mejor. Podría intentar hacer un seguimiento mental de que la propiedad del código postal está en el índice 2 de una lista, pero su código será más fácil de leer y cometerá menos errores si puede buscar `mydiction['zipcode']` que si busque `mylst[2]`.
* Cuando tiene una colección de pares de datos, y a menudo tendrá que buscar uno de los pares en función de su primer valor, es mejor usar un diccionario que una lista de tuplas (clave, valor). Con un diccionario, puede encontrar el valor de cualquier tupla (clave, valor) buscando la clave. Con una lista de tuplas, necesitaría recorrer la lista, examinando cada par para ver si tenía la clave que desea.
* Por otro lado, si tendrá una colección de pares de datos donde varios pares comparten el mismo primer elemento de datos, entonces no puede usar un diccionario, porque un diccionario requiere que todas las claves sean distintas entre sí.

.. Verá estructuras de datos más complicadas más adelante, pero por ahora imagine datos sobre estados de EE. UU., Que contienen datos de población, el nombre del estado, la capital del estado y la apertura del estado. Si tuviera que poner la información sobre cada estado en una lista, entonces el orden de cada bit de datos tendría que ser coherente. Puede verse así:

.. .. sourcecode python

.. data = [4779736, "Alabama", "Montgomery", "AL", 710231, "Alaska", "Juneau", "AK", 6392017, "Arizona", "Phoenix" , "AZ" ......]

.. Para extraer todos los datos de población, por ejemplo, debe saber que siempre fue la primera información sobre un estado, y que cada estado tenía cuatro piezas de información. Luego, necesitaría descubrir cómo extraer la información que podría verse así:

.. .. activecode ac10_10_1

..     data = [4779736, "Alabama", "Montgomery", "AL", 710231, "Alaska", "Juneau", "AK", 6392017, "Arizona", "Phoenix" , "AZ"]

..     position = 0

..     for info in data:
..         if position % 4 == 0:
..             print("Population of a State: " + str(data[position]))

.. Si la población estaba en cambio en un diccionario, entonces podríamos tener un diccionario para buscar recuentos de población y otro para buscar abreviaturas, como se ilustra a continuación. (Más adelante en el curso, veremos estructuras de datos anidados, lo que nos permitiría tener un solo diccionario, cada uno de cuyos valores era una lista o un diccionario).

.. .. sourcecode python

..     state_populations = {"Alabama": 4779736, "Alaska": 710231 "Arizona" : 6392017,  ...}
..     state_abbreviations = {"Alabama": "AL", "Alaska": "AL", "Arizona": "AZ",  ...}




