..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: turtle-7-
   :start: 1

Un poco más de ``turtle`` Métodos y Observaciones
---------------------------------------------------

Aquí hay algunas cosas más que pueden resultarle útiles a medida que escribe programas que usan turtle.

* Los métodos de tortuga pueden usar ángulos negativos o distancias. Entonces ``Tess.forward(-100)`` moverá
  a Tess hacia atrás, y ``tess.left(-30)`` la gira hacia la derecha. Además, porque hay
  360 grados en un círculo, girando 30 a la izquierda te dejará mirando en la mismo
  dirección como girar 330 a la derecha! (La animación en pantalla será diferente, aunque
  --- ¡podrás saber si tess está girando en sentido horario o antihorario!)

  Esto sugiere que no necesitamos un método de giro a la izquierda y a la derecha --- podríamos ser
  minimalistas, y solo tengo un método. También hay un método *backward*. (Si usted es
  muy nerd, puede que disfrutes diciendo ``alex.backward(-100)`` para mover a alex hacia adelante)

  Revisar algunos hechos básicos sobre geometría y rectas numéricas, como lo hemos hecho aquí, es un
  Buen comienzo si vamos a jugar con turtle.

* El bolígrafo de una tortuga se puede levantar o bajar. Esto nos permite mover una tortuga
  a un lugar diferente sin dibujar una línea. Los métodos son ``up`` y ``down``.
  Tenga en cuenta que los métodos ``penup`` y ``pendown`` hacen lo mismo.

  .. sourcecode:: python

     alex.up()
     alex.forward(100)     # this moves alex, but no line is drawn
     alex.down()

* Cada tortuga puede tener su propia forma. Los disponibles "listos para usar" son ``flecha``,
  ``en blanco``, ``círculo``, ``clásico``, ``cuadrado``, ``triángulo``, ``tortuga``.

  .. sourcecode:: python

     ...
     alex.shape("turtle")
     ...


* Puedes acelerar o ralentizar la velocidad de animación de la tortuga. (La animación
  controla qué tan rápido la tortuga gira y avanza). La configuración de velocidad puede
  establecerse entre 1 (el más lento) a 10 (el más rápido). Pero si configura la velocidad a 0,
  tiene un significado especial --- apaga la animación y ve lo más rápido posible.

  .. sourcecode:: python

     alex.speed(10)

* Una tortuga puede "estampar" su huella en el lienzo, y esto permanecerá después de
  la tortuga se ha mudado a otro lugar. El estampado funciona incluso cuando la pluma está arriba.

Hagamos un ejemplo que muestre algunas de estas nuevas características.

.. activecode:: ac3_7_1
    :nocodelens:

    import turtle
    wn = turtle.Screen()
    wn.bgcolor("lightgreen")
    tess = turtle.Turtle()
    tess.color("blue")
    tess.shape("turtle")

    dist = 5
    tess.up()                     # this is new
    for _ in range(30):    # start with size = 5 and grow by 2
        tess.stamp()                # leave an impression on the canvas
        tess.forward(dist)          # move tess along
        tess.right(24)              # and turn her
        dist = dist + 2
    wn.exitonclick()


Si tiene curiosidad acerca de qué tan lejos viaja la tortuga cada vez que el ciclo for itera, puede agregar una impresión
declaración dentro del bucle for para imprimir el valor de ``dist``.

Una cosa más para tener cuidado. Todas menos una de las formas que ves en la pantalla aquí son
huellas creadas por ``sello``. Pero el programa todavía solo tiene *una* instancia de tortuga --- ¿puedes
averiguar cuál es la verdadera Tess? (Sugerencia: si no está seguro, escriba una nueva línea de código después del
bucle ``for`` para cambiar el color de Tess, o para dejar su pluma y dibujar una línea, o para cambiar su forma, etc.)

**Programas mixtos**

.. parsonsprob:: pp3_7_1

   El siguiente programa usa el método de estampar para crear un círculo de formas de tortuga como se muestra a la izquierda, <img src="../_static/TurtleCircle.png" width="150" align="left" hspace="10" vspace="5" alt="image of a circle of turtle shapes"/> Pero las líneas están mezcladas. El programa debe hacer toda la configuración necesaria, crear la tortuga, establecer la forma en "tortuga" y levantar la pluma. Luego, la tortuga debe repetir las siguientes diez veces: avanzar 50 píxeles, dejar una copia de la tortuga en la posición actual, retroceder 50 píxeles y luego girar a la derecha 36 grados. Después del ciclo, configure la ventana para que se cierre cuando el usuario haga clic en ella.<br /><br /><p>Arrastre los bloques de declaraciones desde la columna izquierda a la columna derecha y colóquelos en el orden correcto con la sangría correcta. Haga clic en <i>Check Me</i> para ver si tiene razón. Se le informará si alguna de las líneas está en el orden incorrecto o tiene una sangría incorrecta.</p>
   -----
   import turtle
   wn = turtle.Screen()
   jose = turtle.Turtle()
   jose.shape("turtle")
   jose.penup()
   =====
   for size in range(10):
   =====
     jose.forward(50)
   =====
     jose.stamp()
   =====
     jose.forward(-50)
   =====
     jose.right(36)
   =====
   wn.exitonclick()

**Programas Mixtos**

.. parsonsprob:: pp3_7_2

   El siguiente programa usa el método de estampar para crear una línea de formas de tortuga como se muestra a la izquierda, <img src="../_static/Turtle3Stamp.png" width="150" align="left" hspace="10" vspace="5" alt="image of a line of turtle shapes"/> Pero las líneas están mezcladas. El programa debe hacer toda la configuración necesaria, crear la tortuga, establecer la forma en "turtle" y levantar la pluma. Luego, la tortuga debe repetir las siguientes tres veces: avanzar 50 píxeles y dejar una copia de la tortuga en la posición actual. Después del ciclo, configure la ventana para que se cierre cuando el usuario haga clic en ella.<br/><br/><p> Arrastre los bloques de declaraciones de la columna izquierda a la columna derecha y colóquelos en el orden correcto con el correcto sangría Haga clic en <i>Check Me</i> para ver si tiene razón. Se le informará si alguna de las líneas está en el orden incorrecto o tiene sangría incorrecta.</p>
   -----
   import turtle
   wn = turtle.Screen()
   =====
   nikea = turtle.Turtle()
   =====
   nikea.shape("turtle")
   =====
   nikea.penup()
   =====
   for size in range(3):
   =====
     nikea.forward(50)
   =====
     nikea.stamp()
   =====
   wn.exitonclick()
