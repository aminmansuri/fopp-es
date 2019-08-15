..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: seqmut-2-
   :start: 1

Eliminación de Elementos en una Lista
--------------------------------------

El uso de slices para eliminar elementos de la lista puede ser incómodo y, por lo tanto, propenso a errores.
Python proporciona una alternativa que es más legible.
La sentencia ``del`` elimina un elemento de una lista mediante el uso de su posición.

.. activecode:: ac8_2_1
    
    a = ['one', 'two', 'three']
    del a[1]
    print(a)

    alist = ['a', 'b', 'c', 'd', 'e', 'f']
    del alist[1:5]
    print(alist)

Como es de esperar, ``del`` maneja índices negativos y provoca un error de tiempo de ejecución
si el índice está fuera de rango. Además, puede usar un segmento como índice para ``del``.
Como de costumbre, slice selecciona todos los elementos hasta, pero sin incluir, el segundo índice.
