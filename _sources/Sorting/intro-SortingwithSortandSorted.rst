..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. _sort_chap:

.. qnum::
   :prefix: sort-1-
   :start: 1

Introducción: Ordenamiento con Sort y Sorted
================================================

Cuando presentamos las listas por primera vez, notamos la existencia de un método de clasificación. Cuando se invoca en una lista,
se cambia el orden de los elementos de la lista. Si no se especifican parámetros opcionales, los elementos se organizan en
cualquiera que sea el orden natural para el tipo de artículo. Por ejemplo, si los elementos son todos enteros, entonces
los números más pequeños van antes en la lista. Si los elementos son todos strings, se ordenan en orden alfabético.

.. activecode:: ac18_1_1

    L1 = [1, 7, 4, -2, 3]
    L2 = ["Cherry", "Apple", "Blueberry"]
    
    L1.sort()
    print(L1)
    L2.sort()
    print(L2)
    
Tenga en cuenta que el método de clasificación **no** devuelve una versión ordenada de la lista. De hecho,
devuelve el valor None. Pero la lista misma ha sido modificada. Este tipo de operación
funciona al tener un *efecto secundario* en la lista, puede ser bastante confuso.

En este curso, generalmente usaremos una forma alternativa de ordenar, la función ``sorted`` en lugar de
el método ``sort``. Debido a que es una función en lugar de un método, se invoca en una lista pasando la
lista como un parámetro dentro de los paréntesis, en lugar de poner la lista antes del punto. Más importante,
``sorted`` no cambia la lista original. En cambio, devuelve una nueva lista.

.. activecode:: ac18_1_2

    L2 = ["Cherry", "Apple", "Blueberry"]
    
    L3 = sorted(L2)
    print(L3)
    print(sorted(L2))
    print(L2) # unchanged
    
    print("----")
    
    L2.sort()
    print(L2)
    print(L2.sort())  #return value is None
