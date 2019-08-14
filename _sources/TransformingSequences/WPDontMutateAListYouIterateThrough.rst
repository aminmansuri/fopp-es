..  Copyright (C)  Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: seqmut-12-
   :start: 1

👩‍💻  No mutes una lista por la que estás iterando
=========================================================

Hasta ahora te hemos mostrado cómo recorrer una lista:

.. activecode:: ac8_12_1

    colors = ["Red", "Orange", "Yellow", "Green", "Blue", "Indigo", "Violet"]

    for color in colors:
        print(color)

¡Además de acumular una lista agregando o eliminando elementos!

.. activecode:: ac8_12_2

    colors = ["Red", "Orange", "Yellow", "Green", "Blue", "Indigo", "Violet"]
    initials = []

    for color in colors:
        initials.append(color[0])

    print(initials)

Ahora puede tener la tentación de recorrer una lista y acumular algunos datos en ella o eliminar datos de ella, sin embargo eso
a menudo se vuelve muy confuso. En el siguiente código, filtraremos todas las palabras que comienzan con P, B o T.

.. activecode:: ac8_12_3

    colors = ["Red", "Orange", "Yellow", "Green", "Blue", "Indigo", "Violet", "Purple", "Pink", "Brown", "Teal", "Turquois", "Peach", "Beige"]

    for position in range(len(colors)):
        color = colors[position]
        print(color)
        if color[0] in ["P", "B", "T"]:
            del colors[position]

    print(colors)

En el código anterior, iteramos a través de ``range(len(colors))`` porque facilitó la localización de la posición del
elemento de la lista y elimínelo. Sin embargo, nos encontramos con un problema porque a medida que eliminamos contenido de la lista, la lista
se acorta No solo tenemos un problema de indexación en la línea 4 después de un cierto punto, sino que también omitimos algunas cadenas porque se han movido. Para ver esto más fácilmente, intente recorrer este código en codelens. Tenga en cuenta que cada vez que iteramos por la lista, Python no reevalúa la variable iterador.

También podemos intentar acumular una lista a través de la cual estamos iterando también. ¿Qué crees que pasará aquí?

.. activecode:: ac8_12_4

    colors = ["Red", "Orange", "Yellow", "Green", "Blue", "Indigo", "Violet"]

    for color in colors:
        if color[0] in ["A", "E", "I", "O", "U"]:
            colors.append(color)

    print(colors)

Aunque no hay un error, el comportamiento puede no ser esperado. Cuando nos encontramos con un color que comienza con una vocal,
ese color se agrega al final de la lista. Nuevamente, debido a que Python no reevalúa la variable iteradora, no somos
pegado agregando colores que comienzan con vocales por un número infinito de veces. Eso es bueno en este caso! En última instancia, sin embargo,
Puede ser confuso escribir código como este. Recomendamos no iterar sobre una lista que va a mutar
dentro del ciclo for.
