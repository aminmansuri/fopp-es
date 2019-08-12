..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: turtle-9-
   :start: 1

👩‍💻 Errores comunes de ``turtle``
===================================

A continuación describiremos los errores comunes que los programadores principiantes encuentran al escribir el código de tortuga.
¡Algunos de estos errores también pueden aplicarse a otras instancias!

1. Olvidando un paréntesis

.. activecode:: ac3_9_1

   import turtle
   wn = turtle.Screen()
   alex = turtle.Turtle()

   alex.forward(50
   alex.right(90)

Cuando ejecute el ejemplo anterior, verá cómo se produce un error. Esto se debe a que accidentalmente dejamos el ")" cuando
dile a alex que siga adelante. Este es un error común para los programadores de cualquier nivel de habilidad: es fácil perderse uno y no
¡aviso! Si obtiene un error de sintaxis como este o -especialmente en este libro de texto- uno que dice que hubo una mala sintaxis en un
línea que no es visible para usted, entonces es probable que le falte un paréntesis, una cita o un corchete.

2. Problemas con nombres de variables

A veces escribimos mal un nombre de variable, ya sea poniéndolo en mayúscula cuando no estaba previamente en mayúscula o cambiando
letras alrededor. Otras veces nos referimos accidentalmente al nombre de variable incorrecto. Verifique el código a continuación para ver algunos ejemplos.
.. activecode:: ac3_9_2

   import turtle
   wn = turtle.Screen()
   alex = Turtle.turtle()      #'Tortuga' y 'tortuga' intercambiados

   alex.forward(50)
   alex.right(90)

.. activecode:: ac3_9_3

   import turtle
   wn = turtle.Screen()
   june = turtle.Turtle()      

   june.forward(50)
   right.june(90)             #cambió la variable para Jane con la dirección para girar

.. activecode:: ac3_9_4

   import turtle
   wn = turtle.Screen()
   june = turtle.Turtle()      

   june.forward(50)
   June.right(90)            #capitalizó la variable junio a pesar de que todas las demás estaban en minúsculas

3. Argumentos incorrectos

También podemos proporcionar argumentos incorrectos a un método o función. Cuando eso suceda, verá un mensaje de error como el
uno abajo.

.. activecode:: ac3_9_5

   import turtle
   wn = turtle.Screen()
   june = turtle.Turtle() 

   for _ in range():
       june.color("green", "yellow")
       june.forward("50")
       june.right(90)

Queríamos iterar y dibujar un cuadrado, pero olvidamos especificar cuántas veces deberíamos iterar sobre el ciclo for. Como un
resultado, nos encontramos con un error porque la función de rango requiere al menos un argumento. Intenta arreglar esto para que el código
Construye un cuadrado. ¿Crees que te encontrarás con otros problemas? ¡Predice lo que sucederá y luego pruébalo!


