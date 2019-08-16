..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: dictionaries-3-
   :start: 1

Métodos de Diccionario
-----------------------

Los diccionarios tienen varios métodos útiles incorporados.
La siguiente tabla proporciona un resumen y se pueden encontrar más detalles en la
`Documentación de Python <http://docs.python.org/py3k/library/stdtypes.html#mapping-types-dict>`_.

==========  ==============      =======================================================
Método      Parametros          Descripción
==========  ==============      =======================================================
keys        none                Devuelve una vista de las teclas en el diccionario.
values      none                Devuelve una vista de los valores en el diccionario.
items       none                Devuelve una vista de los pares clave-valor en el diccionario
get         key                 Devuelve el valor asociado con la clave; Ninguno de lo contrario
get         key,alt             Devuelve el valor asociado con la clave; alt de lo contrario
==========  ==============      =======================================================

Como vimos anteriormente con cadenas y listas, los métodos de diccionario usan la notación de puntos, que especifica el nombre del método
a la derecha del punto y el nombre del objeto sobre el cual aplicar el método inmediatamente a la izquierda del punto.
Los paréntesis vacíos en el caso de `` claves '' indican que este método no toma parámetros. Si ``x`` es una variable
cuyo valor es un diccionario, ``x.keys`` es el objeto del método, y ``x.keys()`` invoca el método, devolviendo una vista de
el valor.

El método de claves devuelve las claves, no necesariamente en el mismo orden en que se agregaron al diccionario o cualquier otro
orden particular.

.. activecode:: ac10_3_1
    
    inventory = {'apples': 430, 'bananas': 312, 'oranges': 525, 'pears': 217}  
  
    for akey in inventory.keys():     # the order in which we get the keys is not defined
        print("Got key", akey, "which maps to value", inventory[akey])     
       
    ks = list(inventory.keys())
    print(ks)

    
Es tan común iterar sobre las claves en un diccionario que puede
omitir la llamada al método ``keys`` en el ciclo ``for`` ya que al iterar sobre
un diccionario itera implícitamente sobre sus claves.

.. activecode:: ac10_3_2
    
    inventory = {'apples': 430, 'bananas': 312, 'oranges': 525, 'pears': 217}  
    
    for k in inventory:     
        print("Got key", k)

 
Los métodos ``values`` y ``elements`` son similares a las ``keys``. Devuelven los objetos que se pueden iterar. Nota
que los objetos del artículo son tuplas que contienen la clave y el valor asociado.

.. activecode:: ac10_3_3
    
    inventory = {'apples': 430, 'bananas': 312, 'oranges': 525, 'pears': 217}  
    
    print(list(inventory.values()))
    print(list(inventory.items()))

    for k in inventory:
        print("Got",k,"that maps to",inventory[k])

.. note::

    Técnicamente, .keys(), .values() y .items() no devuelven listas reales. Como la función de rango descrita
    anteriormente, en python 3, devuelven objetos que producen los elementos uno a la vez, en lugar de producir y
    almacenarlos todos por adelantado como una lista. A menos que el diccionario tenga muchas claves, esto no hará que
    diferencia de rendimiento En cualquier caso, al igual que con la función de rango, es seguro para usted pensar en ellos como
    Regresar listas, para la mayoría de los propósitos. Para el intérprete de Python integrado en este libro de texto, en realidad producen
    liza. En un intérprete de Python nativo, si imprime ``type(inventory.keys())``, encontrará que es
    algo más que una lista real. Si desea obtener la primera clave, ``Inventory.keys()[0]`` funciona en línea
    libro de texto, pero en un intérprete de Python real, debe hacer la colección de claves en una lista real antes de usar
    ``[0]`` para indexarlo: ``list(Inventory.keys())[0]``.

Los operadores ``in`` y ``not in`` pueden probar si una clave está en el diccionario:

.. activecode:: ac10_3_4
    
    inventory = {'apples': 430, 'bananas': 312, 'oranges': 525, 'pears': 217}
    print('apples' in inventory)
    print('cherries' in inventory)

    if 'bananas' in inventory:
        print(inventory['bananas'])
    else:
        print("We have no bananas")
     

Este operador puede ser muy útil ya que buscar una clave inexistente en un diccionario provoca un error de tiempo de ejecución.

El método ``get`` nos permite acceder al valor asociado con una clave, similar al operador ``[]``. Lo importante
La diferencia es que ``get`` no causará un error de tiempo de ejecución si la clave no está presente. En su lugar, devolverá Ninguno.
Existe una variación de ``get`` que permite un segundo parámetro que sirve como un valor de retorno alternativo en el
caso donde la clave no está presente. Esto se puede ver en el ejemplo final a continuación. En este caso, ya que "cherries" no es
una clave, devuelve 0 (en lugar de None).

.. activecode:: ac10_3_5
    
    inventory = {'apples': 430, 'bananas': 312, 'oranges': 525, 'pears': 217}
    
    print(inventory.get("apples"))
    print(inventory.get("cherries"))

    print(inventory.get("cherries",0))


**Revisa tu entendimiento**

.. mchoice:: question10_3_1
   :answer_a: 2
   :answer_b: 0.5
   :answer_c: bear
   :answer_d: Error, dividir no es una operación válida en los diccionarios.
   :correct: a
   :feedback_a: get devuelve el valor asociado con una clave dada, por lo que divide 12 por 6.
   :feedback_b: 12 se divide por 6, no al revés.
   :feedback_c: Eche otro vistazo al ejemplo de arriba. get devuelve el valor asociado con una clave dada.
   :feedback_d: El operador de división entera se está utilizando en los valores devueltos por el método get, no en el diccionario.

   ¿Qué se imprime en las siguientes declaraciones?
   
   .. sourcecode:: python

     mydict = {"cat":12, "dog":6, "elephant":23, "bear":20}
     answer = mydict.get("cat")//mydict.get("dog")
     print(answer)
   
.. mchoice:: question10_3_2
   :answer_a: True
   :answer_b: False
   :correct: a
   :feedback_a: Sí, el perro es una clave en el diccionario.
   :feedback_b: El operador in devuelve True si hay una clave en el diccionario, False en caso contrario.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?
   
   .. sourcecode:: python

     mydict = {"cat":12, "dog":6, "elephant":23, "bear":20}
     print("dog" in mydict)


.. mchoice:: question10_3_3
   :answer_a: True
   :answer_b: False
   :correct: b
   :feedback_a: 23 es un valor en el diccionario, no una clave.
   :feedback_b: Sí, el operador in devuelve True si hay una clave en el diccionario, de lo contrario, False.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?
   
   .. sourcecode:: python

      mydict = {"cat":12, "dog":6, "elephant":23, "bear":20}
      print(23 in mydict)

.. mchoice:: question10_3_4
   :answer_a: 18
   :answer_b: 43
   :answer_c: 0
   :answer_d: 61
   :correct: b
   :feedback_a: Agregue los valores que tienen claves de más de 3 caracteres, no aquellos con exactamente 3 caracteres.
   :feedback_b: Sí, la instrucción for itera sobre las claves. Agrega los valores de las claves que tienen una longitud mayor que 3.
   :feedback_c: Este es el patrón del acumulador. El total comienza en 0 pero luego cambia a medida que avanza la iteración.
   :feedback_d: No todos los valores se suman. La declaración if solo elige algunos de ellos.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?
   
   .. sourcecode:: python

      total = 0
      mydict = {"cat":12, "dog":6, "elephant":23, "bear":20}
      for akey in mydict:
         if len(akey) > 3:
            total = total + mydict[akey]
      print(total)

.. activecode:: ac10_3_6
   :language: python
   :autograde: unittest
   :practice: T

   **5.** Cada cuatro años, los Juegos Olímpicos de verano se llevan a cabo en un país diferente. Agregue un par clave-valor al diccionario ``places`` que refleje que los Juegos Olímpicos de 2016 se celebraron en Brasil. ¡No reescribas todo el diccionario para hacer esto!
   ~~~~

   places = {"Australia":2000, "Greece":2004, "China":2008, "England":2012}

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(sorted(places.items()), sorted([("Australia", 2000), ("Greece", 2004), ("China", 2008), ("England", 2012), ("Brazil", 2016)]), "Testing that places has been updated correctly.")

   myTests().main()

.. activecode:: ac10_3_7
   :language: python
   :autograde: unittest
   :practice: T

   **6.** Tenemos un diccionario de los eventos específicos en los que Italia ha ganado medallas y el número de medallas que han ganado para cada evento. Asigne a la variable ``events`` una lista de las claves del diccionario ``medal_events``. No codifiques esto.
   ~~~~

   medal_events = {'Shooting': 7, 'Fencing': 4, 'Judo': 2, 'Swimming': 3, 'Diving': 2}

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(sorted(events), sorted(['Shooting', 'Fencing', 'Judo', 'Swimming', "Diving"]), "Testing that events was created correctly")   

   myTests().main()
