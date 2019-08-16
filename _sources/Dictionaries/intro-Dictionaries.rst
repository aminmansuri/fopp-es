..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. index:: dictionary, mapping type, key-value pair
   single: [ ]; dictionary access
   value; dictionary

.. qnum::
   :prefix: dictionaries-1-
   :start: 1

Introducción: Diccionarios
===========================

Para proporcionar un ejemplo de este nuevo tipo de tipo de datos, crearemos un diccionario para traducir palabras en inglés al español.
Para este diccionario, las claves son cadenas y los valores también serán cadenas.

Una forma de crear un diccionario es comenzar con el diccionario vacío y agregar **pares clave-valor**. El diccionario vacio
se denota ``{}``.

.. codelens:: clens10_1_1
    :python: py3

    eng2sp = {}
    eng2sp['one'] = 'uno'
    eng2sp['two'] = 'dos'
    eng2sp['three'] = 'tres'
    print(eng2sp)

La primera asignación crea un diccionario vacío llamado ``eng2sp``. Las otras asignaciones agregan nuevos pares clave-valor a
el diccionario. El lado izquierdo muestra el diccionario y la clave asociada. El lado derecho da la
valor asociado con esa clave. Podemos imprimir el valor actual del diccionario de la manera habitual. El valor clave
Los pares del diccionario están separados por comas. Cada par contiene una clave y un valor separados por dos puntos.

El orden de los pares puede no ser el esperado. Python utiliza algoritmos complejos, diseñados para un acceso muy rápido, para
determinar dónde se almacenan los pares clave-valor en un diccionario. Para nuestros propósitos, podemos considerar este pedido como
impredecible.

Otra forma de crear un diccionario es proporcionar un grupo de pares clave-valor utilizando la misma sintaxis que la anterior.
salida.

.. codelens:: clens10_1_2
    :python: py3
    
    eng2sp = {'three': 'tres', 'one': 'uno', 'two': 'dos'}
    print(eng2sp)

No importa en qué orden escribimos los pares. Se accede a los valores en un diccionario con claves, no con índices,
así que no hay necesidad de preocuparse por ordenar.

Así es como usamos una tecla para buscar el valor correspondiente.

.. codelens:: clens10_1_3
    :python: py3

    eng2sp = {'three': 'tres', 'one': 'uno', 'two': 'dos'}

    value = eng2sp['two']
    print(value)
    print(eng2sp['one'])

La clave ``'two'`` produce el valor ``'dos'``. La clave ``one`` produce el valor ``uno``.

**Revisa tu entendimiento**

.. mchoice:: question10_1_1 
   :answer_a: Verdadero
   :answer_b: Falso
   :correct: a
   :feedback_a: Los diccionarios asocian claves con valores, pero no hay un orden asumido para las entradas.
   :feedback_b: Sí, los diccionarios son colecciones asociativas, lo que significa que almacenan pares clave-valor.

   Un diccionario es una colección desordenada de pares clave-valor.

.. mchoice:: question10_1_2
   :answer_a: 12
   :answer_b: 6
   :answer_c: 23
   :answer_d: Error, no puede usar el operador de índice con un diccionario.
   :correct: b
   :feedback_a: 12 es asociado con la clave cat.
   :feedback_b: Sí, 6 está asociado con la clave perro.
   :feedback_c: 23 is associated with the key elephant.
   :feedback_d: The [ ] operator, when used with a dictionary, will look up a value based on its key.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?
   
   .. sourcecode:: python

     mydict = {"cat":12, "dog":6, "elephant":23}
     print(mydict["dog"])

.. activecode:: ac10_1_1
   :language: python
   :autograde: unittest
   :practice: T

   **3.** Cree un diccionario que haga un seguimiento del recuento de medallas olímpicas de EE.UU. Cada clave del diccionario debe ser el tipo de medalla (oro, plata o bronce) y el valor de cada clave debe ser el número de ese tipo de medalla que ganó EE. UU. Actualmente, Estados Unidos tiene 33 medallas de oro, 17 de plata y 12 de bronce. Cree un diccionario guardado en la variable ``medals`` que refleje esta información.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(sorted(medals.items()), sorted([("gold", 33), ("silver", 17), ("bronze", 12)]), "Testing that medals is correct.")

   myTests().main()

.. activecode:: ac10_1_2
   :language: python
   :autograde: unittest
   :practice: T

   **4.** ¡Estás siguiendo las medallas olímpicas para Italia en los Juegos Olímpicos de Río 2016! Por el momento, Italia tiene 7 medallas de oro, 8 de plata y 6 de bronce. Cree un diccionario llamado ``olympics`` donde las claves son los tipos de medallas, y los valores son el número de ese tipo de medallas que Italia ha ganado hasta ahora.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(sorted(olympics.items()), sorted([('gold', 7), ('silver', 8), ('bronze', 6)]), "Testing that olympics was created correctly.")     

   myTests().main()
