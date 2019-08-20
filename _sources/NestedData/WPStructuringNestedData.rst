..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: nested-9-
   :start: 1

👩‍💻 Estructurando Datos Anidados
----------------------------------

Al construir sus propios datos anidados, es una buena idea mantener la estructura consistente en cada nivel. Por ejemplo,
si tiene una lista de diccionarios, entonces cada diccionario debe tener la misma estructura, es decir, las mismas claves y el mismo tipo de valor asociado con una clave particular en todos los diccionarios. La razón
Esto se debe a que cualquier desviación en la estructura utilizada requerirá un código adicional para manejar esos casos especiales. los
cuanto más se desvía la estructura, más tendrá que usar casos especiales.

Por ejemplo, reconsideremos esta iteración anidada, pero supongamos que no todos los elementos de la lista externa son listas.

.. activecode:: ac17_50_1
    :language: python

    nested1 = [1, 2, ['a', 'b', 'c'],['d', 'e'],['f', 'g', 'h']]
    for x in nested1:
        print("level1: ")
        for y in x:
            print("     level2: {}".format(y))

Ahora la iteración anidada falla.

Podemos resolver esto con un casing especial, un condicional que verifica el tipo.

.. activecode:: ac17_50_2
    :language: python

    nested1 = [1, 2, ['a', 'b', 'c'],['d', 'e'],['f', 'g', 'h']]
    for x in nested1:
        print("level1: ")
        if type(x) is list:
            for y in x:
                print("     level2: {}".format(y))
        else:
            print(x)

¿Puede imaginar cuántos casos especiales necesitaríamos, y cuán complicado se volvería el código, si tuviéramos muchas capas de anidamiento pero no siempre una estructura consistente?.