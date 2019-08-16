..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: dictionaries-2-
   :start: 1

.. index:: del; dictionary
   statement; del

Operaciones de Diccionario
---------------------------

La declaración ``del`` elimina un par clave-valor de un diccionario. Por ejemplo, el siguiente diccionario contiene el
nombres de varias frutas y el número de cada fruta en stock. Si alguien compra todas las peras, podemos eliminar el
entrada del diccionario.

.. codelens:: clens10_2_1
    :python: py3

    inventory = {'apples': 430, 'bananas': 312, 'oranges': 525, 'pears': 217}
    
    del inventory['pears']

Los diccionarios son mutables, como lo indica la operación de eliminación anterior. Como hemos visto antes con las listas, esto significa que el
El diccionario se puede modificar haciendo referencia a una asociación en el lado izquierdo de la instrucción de asignación. En el
ejemplo anterior, en lugar de eliminar la entrada para ``pears``, podríamos haber configurado el inventario en ``0``.

.. codelens:: clens10_2_2
    :python: py3

    inventory = {'apples': 430, 'bananas': 312, 'oranges': 525, 'pears': 217}
    
    inventory['pears'] = 0

.. note:: 
   
   Establecer el valor asociado con ``pears`` en 0 tiene un efecto diferente que eliminar completamente el par clave-valor
   con ``del``. Intente imprimir los dos diccionarios en los ejemplos anteriores.

Del mismo modo, un nuevo envío de 200 plátanos que llegan podría manejarse de esta manera. Tenga en cuenta que ahora hay 512 plátanos
El diccionario ha sido modificado. Tenga en cuenta también que la función ``len`` también funciona en los diccionarios. Devuelve el número
de pares clave-valor.

.. codelens:: clens10_2_3
    :python: py3

    inventory = {'apples': 430, 'bananas': 312, 'oranges': 525, 'pears': 217}    
    inventory['bananas'] = inventory['bananas'] + 200

    numItems = len(inventory)

Tenga en cuenta que ahora hay 512 plátanos, el diccionario ha sido modificado. Tenga en cuenta también que la función ``len`` también
funciona en diccionarios. Devuelve el número de pares clave-valor.

**Revisa tu entendimiento**

.. mchoice:: question10_2_1
   :answer_a: 12
   :answer_b: 0
   :answer_c: 18
   :answer_d: Error, no hay entrada con el mouse como clave.
   :correct: c
   :feedback_a: 12 está asociado con el gato clave.
   :feedback_b: El mouse clave se asociará con la suma de los dos valores.
   :feedback_c: Sí, agregue el valor para cat y el valor para dog (12 + 6) y cree una nueva entrada para mouse.
   :feedback_d: Como la nueva clave se introduce en el lado izquierdo de la instrucción de asignación, se agrega un nuevo par clave-valor al diccionario.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?
   
   .. sourcecode:: python

     mydict = {"cat":12, "dog":6, "elephant":23}
     mydict["mouse"] = mydict["cat"] + mydict["dog"]
     print(mydict["mouse"])

.. activecode:: ac10_2_1
   :language: python
   :autograde: unittest

   **2.** Actualice el valor de "Phelps" en el diccionario ``swimmers`` para incluir sus medallas de los Juegos Olímpicos de Río agregando 5 al valor actual (Phelps ahora tendrá 28 medallas en total). No reescribas el diccionario.
   ~~~~

   swimmers = {'Manuel':4, 'Lochte':12, 'Adrian':7, 'Ledecky':5, 'Dirado':4, 'Phelps':23}
      
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testThree(self):
         self.assertEqual(sorted(swimmers.items()), sorted([('Adrian', 7), ('Dirado', 4), ('Ledecky', 5), ('Lochte', 12), ('Phelps', 28), ('Manuel',4)]), "Testing that swimmers is assigned to correct values.")

   myTests().main()
