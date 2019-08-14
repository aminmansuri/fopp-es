..  Copyright (C) Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: iter-8-
   :start: 1

.. _naming_variables_in_for_loops:

👩‍💻 Nombrando Variables en bucles For
=======================================

Hemos mencionado antes acerca de elegir cuidadosamente sus nombres de variables. Aunque el
los nombres que elija no son significativos para el programa, pueden serlo para usted. Cuando nosotros
elija nombres para variables en bucles for, cuanto más comprensibles sean para nosotros,
más fácil será usarlos. Aquí hay algunos consejos para hacer más bucles
legible para usted y para cualquier otra persona que pueda leer sus programas:

1. Use sustantivos singulares para la variable iteradora, que también se llama variable de bucle (cosas como "canción", "libro", "publicación", "letra", "palabra").
2. Use sustantivos en plural para la variable de secuencia (cosas como "canciones", "libros", "publicaciones", "letras", "palabras").

Si bien estos dos consejos no siempre se aplican, son mejores prácticas generales cuando
viene a elegir nombres de variables. ¡A continuación tenemos un ejemplo!

.. activecode:: ac6_8_1
   :include: ac6_8_3

   # x es una lista definida en alguna parte

   for y in x:
       print(y)

Como no podemos ver el contenido de x en este momento, este podría ser el caso si tenemos
un programa largo, entonces estos nombres harían que el programa sea difícil de entender. Vamos
a comparar esto con un programa que hace lo mismo, pero usa mejores nombres.

.. activecode:: ac6_8_2
   :include: ac6_8_3

   # genres es una lista definida en alguna parte

   for genre in genres:
       print(genre)

¡Aquí lo que esperamos es mucho más claro, incluso si no vemos cómo se inicializaron los géneros!

El código a continuación se usó para inicializar x y genres para que pueda verlo pero usted,
¡no es necesario ejecutarlo!

.. activecode:: ac6_8_3
   :hidecode:

   x = ["jazz", "pop", "rock", "country", "punk", "folk", "hip-hop", "rap", "alternative"]
   genres = ["jazz", "pop", "rock", "country", "punk", "folk", "hip-hop", "rap", "alternative"]

