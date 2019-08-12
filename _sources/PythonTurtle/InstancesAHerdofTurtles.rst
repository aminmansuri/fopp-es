..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: turtle-3-
   :start: 1

.. index:: for loop

Instancias: una manada de tortugas
----------------------------------

Al igual que podemos tener muchos enteros diferentes en un programa, podemos tener muchos
tortugas. Cada uno de ellos es un objeto independiente y llamamos a cada uno una **instancia** del
Tipo tortuga (clase). Cada instancia tiene sus propios atributos y métodos --- por lo que Alex podría
dibuja con un bolígrafo rosado delgado y ponte en alguna posición, mientras que Tess podría ir sola
dirección con una pluma negra gorda. Entonces, esto es lo que sucede cuando Alex completa un cuadrado y
Tess completa su triángulo:

.. activecode:: ac3_3_1
   :tour_1: "Overall Tour"; 1-31: Example03_Tour01_Line01; 1-3: Example03_Tour01_Line02; 6-8: Example03_Tour01_Line03; 10: Example03_Tour01_Line04; 6,10: Example03_Tour01_Line05; 12-17: Example03_Tour01_Line06; 19-20: Example03_Tour01_Line07; 22-29: Example03_Tour01_Line08; 31: Example03_Tour01_Line09;
   :tour_2: "Line by Line Tour"; 1: Example01_Tour02_Line01; 2: Example01_Tour02_Line02; 3: Example02_Tour02_Line03; 6: Example02_Tour02_Line04; 7: Example03_Tour02_Line05; 8: Example03_Tour02_Line06; 10: Example01_Tour02_Line03; 6,10: Example03_Tour01_Line05; 12-17: Example03_Tour02_Line09; 12-13: Example03_Tour02_Line10; 12: Example03_Tour02_Line11; 13: Example03_Tour02_Line12; 14-15: Example03_Tour02_Line13; 14: Example03_Tour02_Line14; 15: Example03_Tour02_Line15; 16-17: Example03_Tour02_Line16; 16: Example03_Tour02_Line17; 17: Example03_Tour02_Line18; 19-20: Example03_Tour01_Line07; 19: Example03_Tour02_Line20; 20: Example03_Tour02_Line21; 22-29: Example03_Tour01_Line08; 10: Example03_Tour02_Line23; 22-23: Example03_Tour02_Line24; 22: Example03_Tour02_Line25; 23: Example03_Tour02_Line26; 24-25: Example03_Tour02_Line27; 26-27: Example03_Tour02_Line28; 28-29: Example03_Tour02_Line29; 31: Example02_Tour02_Line10;
   :nocodelens:

   import turtle
   wn = turtle.Screen()             # Configurar la ventana y sus atributos.
   wn.bgcolor("lightgreen")


   tess = turtle.Turtle()           # crear tess y establecer el ancho de su bolígrafo
   tess.pensize(5)

   alex = turtle.Turtle()           # crear a alex
   alex.color("hotpink")            # establecer su color

   tess.forward(80)                 # Deje que tess dibuje un triángulo equilátero
   tess.left(120)
   tess.forward(80)
   tess.left(120)
   tess.forward(80)
   tess.left(120)                   # completa el triángulo

   tess.right(180)                  # girar a Tess
   tess.forward(80)                 # moverla del origen para que podamos ver a Alex

   alex.forward(50)                 # haz que alex dibuje un cuadrado
   alex.left(90)
   alex.forward(50)
   alex.left(90)
   alex.forward(50)
   alex.left(90)
   alex.forward(50)
   alex.left(90)

   wn.exitonclick()


Aquí hay algunas observaciones *Cómo pensar como un científico de la computación*:

* Hay 360 grados en un círculo completo. Si sumas todos los turnos que un
  tortuga hace, *no importa qué pasos ocurrieron entre los turnos*, puedes
  averiguar fácilmente si suman un múltiplo de 360. Esto debería
  convencerte de que Alex está mirando exactamente en la misma dirección que él cuando
  Fue creado por primera vez. (Las convenciones de geometría tienen 0 grados hacia el este y
  ¡Ese es el caso aquí también!)
* Podríamos haber dejado fuera el último turno para Alex, pero eso no habría sido
  tan satisfactorio Si se le pide que dibuje una forma cerrada como un cuadrado o un
  rectángulo, es una buena idea completar todos los giros y dejar el
  tortuga de regreso donde comenzó, mirando en la misma dirección en que comenzó.
  Esto hace que el razonamiento sobre el programa y la composición de fragmentos de código en
  ¡Programas más grandes más fáciles para nosotros los humanos!
* Hicimos lo mismo con Tess: dibujó su triángulo y dio vuelta
  360 degress. Luego la dimos la vuelta y la apartamos. Incluso el blanco
  la línea 18 es una pista sobre cómo está funcionando el *fragmentado mental* del programador: en
  En términos generales, los movimientos de Tess se fragmentaron como "dibujar el triángulo" (líneas 12-17)
  y luego "alejarse del origen" (líneas 19 y 20).
* Uno de los usos clave para los comentarios es registrar su fragmentación mental y
  ideas No siempre son explícitos en el código.
* Y, uh-huh, dos tortugas pueden no ser suficientes para un rebaño, ¡pero se entiende la idea!


**Revisa tu entendimiento**

.. mchoice:: question3_3_1
   :answer_a: Verdadero
   :answer_b: Falso
   :correct: b
   :feedback_a: Puedes crear y usar tantas tortugas como quieras. Siempre que tengan nombres diferentes, puede operarlos de forma independiente y hacer que se muevan en el orden que desee. Para convencerse de que esto es cierto, intente entrelazar las instrucciones para Alex y Tess en el cuadro ActiveCode 3.
   :feedback_b: Puedes crear y usar tantas tortugas como quieras. Siempre que tengan nombres diferentes, puede operarlos de forma independiente y hacer que se muevan en el orden que desee. Si no está totalmente convencido, intente entrelazar las instrucciones para Alex y Tess en el cuadro ActiveCode 3.

   Verdadero o Falso: Solo puedes tener una tortuga activa a la vez. Si crea una segunda, ya no podrá acceder o usar la primera.

**Programas mixtos**

.. parsonsprob:: pp3_3_1

   El siguiente programa tiene una tortuga, "jamal", dibuja una L mayúscula en azul y luego otra, "tina", dibuja una línea hacia el oeste en naranja como se muestra a la izquierda, <img src="../_static/TwoTurtles1.png" width="150" align="left" hspace="10" vspace="5" alt="image of a capital letter L in blue color drawn by one Turtle and a line to the west in orange color drawn by another Turtle. Both the Turtles have same starting point."/>. El programa debe hacer toda la configuración, hacer que "jamal" dibuje la L y luego que "tina" dibuje la línea. Finalmente, debe configurar la ventana para que se cierre cuando el usuario haga clic en ella.<br/><br/><p> Arrastre los bloques de declaraciones de la columna izquierda a la columna derecha y colóquelos en el orden correcto. Luego haga clic en <i>Check Me</i>para ver si tiene razón. Se le informará si alguna de las líneas está en el orden incorrecto.</p>
   -----
   import turtle
   wn = turtle.Screen()
   =====
   jamal = turtle.Turtle()
   jamal.pensize(10)
   jamal.color("blue")
   jamal.right(90)
   jamal.forward(150)
   =====
   jamal.left(90)
   jamal.forward(75)
   =====
   tina = turtle.Turtle()
   tina.pensize(10)
   tina.color("orange")
   tina.left(180)
   tina.forward(75)
   =====
   wn.exitonclick()

.. parsonsprob:: pp3_3_2

   El siguiente programa tiene una tortuga, "jamal", dibuja una línea hacia el norte en azul y luego otra, "tina", dibuja una línea hacia el este en naranja como se muestra a la izquierda, <img src="../_static/TwoTurtlesL.png" width="150" align="left" hspace="10" vspace="5" alt="image of a line to the north in blue color drawn by one Turtle and a line to the east in orange drawn by another Turtle. Both the Turtles have a same starting point."/>. El programa debe importar el módulo de tortuga, obtener la ventana para dibujar, crear la tortuga "jamal", hacer que dibuje una línea hacia el norte, luego crear la tortuga "tina" y hacer que dibuje una línea hacia el este. Finalmente, debe configurar la ventana para que se cierre cuando el usuario haga clic en ella.<br/><br /><p> Arrastre los bloques de declaraciones de la columna izquierda a la columna derecha y colóquelos en el orden correcto. Luego haga clic en <i>Check Me</i> para ver si tiene razón. Se le informará si alguna de las líneas está en el orden incorrecto.</p>
   -----
   import turtle
   =====
   wn = turtle.Screen()
   =====
   jamal = turtle.Turtle()
   jamal.color("blue")
   jamal.pensize(10)
   =====
   jamal.left(90)
   jamal.forward(150)
   =====
   tina = turtle.Turtle()
   tina.pensize(10)
   tina.color("orange")
   tina.forward(150)
   =====
   wn.exitonclick()
