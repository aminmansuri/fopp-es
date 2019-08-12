..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: turtle-8-
   :start: 1

👩‍💻  Programación Incremental
===============================

A estas alturas, es probable que haya encontrado ocasiones en las que su código será largo o complejo. Si tu
aborde problemas como este escribiendo todo el código y *luego* ejecutándolo, probablemente
se siente frustrado por el proceso de depuración. ¡Hay maneras de facilitar la programación!.

1. **Comience pequeño** Este es probablemente el consejo más importante para los programadores en
todos los niveles. Por supuesto, es tentador sentarse y poner en marcha un programa completo a la vez. Pero,
cuando el programa, inevitablemente, no funciona, entonces tienes una gran cantidad de opciones para las cosas
eso podría estar mal. ¿Donde empezar? ¿Dónde mirar primero? ¿Cómo averiguar qué salió mal?
Llegaré a eso en la siguiente sección. Entonces, comience con algo realmente pequeño. Tal vez solo dos
líneas y luego asegúrese de que funciona bien. Pulsar el botón de correr es rápido y fácil, y te da
retroalimentación inmediata sobre si lo que acaba de hacer está bien o no. Otro inmediato
El beneficio de tener algo pequeño que funciona es que tiene algo que entregar.
programa pequeño e incompleto, casi siempre es mejor que nada.

2. **Manténgalo funcionando** Una vez que tenga una pequeña parte de su programa trabajando, el siguiente paso es
para descubrir algo pequeño para agregarle. Si sigues agregando pequeñas piezas del programa uno
a la vez, es mucho más fácil descubrir qué salió mal, ya que lo más probable es que
El problema va a estar en el nuevo código que acaba de agregar. Menos código nuevo significa que es más fácil
averiguar dónde está el problema.

Esta noción de **Hacer que algo funcione y mantenerlo funcionando** es un mantra que puedes repetir
a lo largo de tu carrera como programador. Es una excelente manera de evitar las frustraciones mencionadas
encima. Piénsalo de esta manera. Cada vez que tienes un poco de éxito, tu cerebro libera un pequeño
Un poco de químico que te hace feliz. Entonces, puedes mantenerte feliz y hacer programación
más agradable creando muchas pequeñas victorias para ti.

A continuación ya hemos comenzado a construir una casa. Para practicar la programación incremental, intente dibujar
El resto de la casa. Cada vez que dibuje algo nuevo en la pantalla, ejecute el programa para ver si
se ejecutó de la manera que esperabas!

.. activecode:: ac3_100_1

    import turtle
    wn = turtle.Screen()
    bob = turtle.Turtle()
    bob.right(90)
    bob.forward(50)
    bob.left(90)
    bob.forward(50)

    # ¡Agrega tu código debajo!


