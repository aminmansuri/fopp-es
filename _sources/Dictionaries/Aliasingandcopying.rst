..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: dictionaries-4-
   :start: 1

.. index::
   alias; dictionary
   copy; dictionary
   dictionary; alias and copy

Creando Alias y Copias
------------------------

Debido a que los diccionarios son mutables, debe tener en cuenta el alias (como vimos con las listas). Cuando
dos variables se refieren al mismo objeto del diccionario, los cambios en uno afectan al otro. Por ejemplo, ``opposites``
es un diccionario que contiene pares de opuestos.

.. activecode:: ac10_4_1
    
    opposites = {'up': 'down', 'right': 'wrong', 'true': 'false'}
    alias = opposites

    print(alias is opposites)

    alias['right'] = 'left'
    print(opposites['right'])
    


Como puede ver en el operador ``is``, ``alias`` y ``opposites`` se refieren al mismo objeto.

Si desea modificar un diccionario y conservar una copia del original, use el diccionario
método ``copy``. Como *acopy* es una copia del diccionario, los cambios no afectarán al original.

.. sourcecode:: python
    
    acopy = opposites.copy()
    acopy['right'] = 'left'    # no hace cambios opposites

**Revisa tu entendimiento**

.. mchoice:: question10_4_1
   :answer_a: 23
   :answer_b: None
   :answer_c: 999
   :answer_d: Error, hay dos claves diferentes llamadas elefante.
   :correct: c
   :feedback_a: mydict y yourdict son nombres para el mismo diccionario.
   :feedback_b: El diccionario es mutable, por lo que se pueden hacer cambios en las claves y valores.
   :feedback_c: Sí, dado que yourdict es un alias para mydict, el valor para el elefante clave ha cambiado.
   :feedback_d: Solo hay un diccionario con una sola clave llamada elefante. El diccionario tiene dos nombres diferentes, mydict y yourdict.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?
   
   .. sourcecode:: python

     mydict = {"cat":12, "dog":6, "elephant":23, "bear":20}
     yourdict = mydict
     yourdict["elephant"] = 999
     print(mydict["elephant"])
