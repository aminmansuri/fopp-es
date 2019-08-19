..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: nested-5-
   :start: 1

Deep Copy y Shallow Copy
========================

Anteriormente, cuando discutimos las listas de clonación y alias, mencionamos que simplemente clonar una lista usando [:] se ocuparía de cualquier problema
con tener dos listas conectadas involuntariamente entre sí. Eso fue definitivamente cierto para hacer copias poco profundas -*shallow copies*- (copiar una lista en el
nivel más alto), pero a medida que ingresamos a los datos anidados, y a las listas anidadas en particular, las reglas se vuelven un poco más complicadas. Podemos tener
alias de segundo nivel en estos casos, lo que significa que necesitamos hacer copias profundas.

Cuando copia una lista anidada, tampoco obtiene copias de las listas internas. Esto significa que si realiza una operación de mutación en uno
de las sublistas originales, la versión copiada también cambiará. Podemos ver que esto suceda en la siguiente lista anidada, que solo tiene dos niveles.

.. activecode:: ac17_100_1

    original = [['dogs', 'puppies'], ['cats', "kittens"]]
    copied_version = original[:]
    print(copied_version)
    print(copied_version is original)
    print(copied_version == original)
    original[0].append(["canines"])
    print(original)
    print("-------- Now look at the copied version -----------")
    print(copied_version)

Suponiendo que no desea tener listas con alias dentro de su lista anidada, deberá realizar una iteración anidada.

.. activecode:: ac17_100_2

    original = [['dogs', 'puppies'], ['cats', "kittens"]]
    copied_outer_list = []
    for inner_list in original:
        copied_inner_list = []
        for item in inner_list:
            copied_inner_list.append(item)
        copied_outer_list.append(copied_inner_list)
    print(copied_outer_list)
    original[0].append(["canines"])
    print(original)
    print("-------- Now look at the copied version -----------")
    print(copied_outer_list)

O, de manera equivalente, podría aprovechar el operador de división para copiar la lista interna.

.. activecode:: ac17_100_2a

    original = [['dogs', 'puppies'], ['cats', "kittens"]]
    copied_outer_list = []
    for inner_list in original:
        copied_inner_list = inner_list[:]
        copied_outer_list.append(copied_inner_list)
    print(copied_outer_list)
    original[0].append(["canines"])
    print(original)
    print("-------- Now look at the copied version -----------")
    print(copied_outer_list)

Este proceso anterior funciona bien cuando solo hay dos capas o niveles en una lista anidada. Sin embargo, si queremos hacer una copia de una
lista anidada que tiene *más* de dos niveles, entonces recomendamos usar el módulo ``copy``. En el módulo ``copy`` hay un método llamado
``deepcopy`` que se encargará de la operación por usted.

.. activecode:: ac17_100_3

    import copy
    original = [['canines', ['dogs', 'puppies']], ['felines', ['cats', 'kittens']]]
    shallow_copy_version = original[:]
    deeply_copied_version = copy.deepcopy(original)
    original.append("Hi there")
    original[0].append(["marsupials"])
    print("-------- Original -----------")
    print(original)
    print("-------- deep copy -----------")
    print(deeply_copied_version)
    print("-------- shallow copy -----------")
    print(shallow_copy_version)


