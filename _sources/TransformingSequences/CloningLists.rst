..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: seqmut-5-
   :start: 1

Clonando Listas
----------------

Si queremos modificar una lista y también conservar una copia del original, debemos ser
capaz de hacer una copia de la lista en sí, no solo la referencia. Este proceso es
a veces llamado **clonación**, para evitar la ambigüedad de la palabra copia.

La forma más fácil de clonar una lista es usar el operador slice.

Tomar cualquier porción de ``a`` crea una nueva lista. En este caso, el segmento pasa a
consiste en toda la lista.

.. activecode:: clens8_5_1

    a = [81,82,83]

    b = a[:]       # make a clone using slice
    print(a == b)
    print(a is b)

    b[0] = 5

    print(a)
    print(b)

Ahora somos libres de hacer cambios a ``b`` sin preocuparnos por ``a``. De nuevo, podemos ver claramente en
codelens que ``a`` y ``b`` son objetos de lista completamente diferentes.

**Revisa tu entendimiento**

.. mchoice:: question8_5_1
   :answer_a: [4,2,8,999,5,4,2,8,6,5]
   :answer_b: [4,2,8,999,5]
   :answer_c: [4,2,8,6,5]
   :correct: c
   :feedback_a: imprime alist no imprime blist
   :feedback_b: ha cambiado blist, no alist.
   :feedback_c: Sí, alist no fue modificado por la declaración de asignación. blist fue una copia de las referencias en alist.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?
   
   .. code-block:: python

     alist = [4,2,8,6,5]
     blist = alist * 2
     blist[3] = 999
     print(alist)
