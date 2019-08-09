..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: turtle-2-
   :start: 1

.. index:: instance

Nuestro Primer Programa con Turtle
-----------------------------------

Probemos un par de líneas de código Python para crear una nueva tortuga y
comienza a dibujar una figura simple como un rectángulo.
Nos referiremos a nuestra primera tortuga usando el nombre de la variable alex, pero recuerda que puede
elegir cualquier nombre que desee siempre y cuando siga las reglas de nomenclatura del capítulo anterior.

El programa como se muestra solo dibujará los dos primeros lados del rectángulo.
Después de la línea 4, tendrá una línea recta que va desde el centro de la
dibujando lienzo hacia la derecha. Después de la línea 6, tendrá un lienzo con un
tortuga y medio rectángulo dibujado. Presione el botón Ejecutar para probarlo.

.. activecode:: ac3_2_1
    :tour_1: "Overall Tour"; 1-6: Example01_Tour01_Line01; 3: Example01_Tour01_Line02; 4: Example01_Tour01_Line03; 5: Example01_Tour01_Line04; 6: Example01_Tour01_Line05;
    :tour_2: "Line by Line Tour"; 1: Example01_Tour02_Line01; 2: Example01_Tour02_Line02; 3: Example01_Tour02_Line03; 4: Example01_Tour02_Line04; 5: Example01_Tour02_Line05; 6: Example01_Tour02_Line06;
    :nocodelens:

    import turtle             # Nos permite usar la biblioteca de turtle
    wn = turtle.Screen()      # crea la vntana de graficos
    alex = turtle.Turtle()    # crea una tortuga llamada alex
    alex.forward(150)         # le dice a alex que se mueva 150 unidades hacia adelante
    alex.left(90)             # gira 90 grados
    alex.forward(75)          # completa el segundo lado del rectángulo




Aquí hay un par de cosas que necesitará comprender sobre este programa.

La primera línea le dice a Python que cargue un **módulo** llamado ``tortuga``. Ese módulo
nos trae dos tipos nuevos que podemos usar: el tipo ``Tortuga`` y el tipo ``pantalla``.
La notación de punto ``tortuga.Tortuga`` significa *"El tipo de tortuga que se define dentro del módulo de tortuga"*.
(Recuerde que Python es sensible a mayúsculas y minúsculas), por lo que el nombre del módulo, ``tortuga``, con una ``t`` minúscula, es diferente
a ``Tortuga`` debido a la mayúscula ``T``.)

Luego creamos y abrimos lo que el módulo de tortuga llama una *pantalla* (habríamos
preferido llamarlo una ventana, o en el caso de esta versión web de Python
simplemente un lienzo), que asignamos a la variable ``wn``. Cada ventana
contiene un **lienzo**, que es el área dentro de la ventana, en la que podemos dibujar.

En la línea 3 creamos una tortuga. La variable ``alex`` está hecha para referirse a esta
Tortuga. Estas tres primeras líneas nos preparan para que estemos listos para dibujar.

En las líneas 4-6, le indicamos al **objeto** alex que se mueva y gire. Nosotros hacemos esto
**invocando** o activando **los métodos de alex** --- estas son las instrucciones que todas
las tortugas saben cómo responder.


.. admonition:: Completa el retángulo ...

   Modifique el programa agregando los comandos necesarios para que *alex* complete el rectángulo.

**Revisa tu entendimiento**

.. mchoice:: question3_2_1
   :answer_a: Norte
   :answer_b: Sur
   :answer_c: Este
   :answer_d: Oeste
   :correct: c
   :feedback_a: Algunos sistemas de tortugas comienzan con la tortuga mirando hacia el norte, pero este no.
   :feedback_b: No, mira el primer ejemplo con una tortuga. ¿En qué dirección se mueve la tortuga?
   :feedback_c: Sí, la tortuga comienza mirando hacia el este.
   :feedback_d: No, mira el primer ejemplo con una tortuga. ¿En qué dirección se mueve la tortuga?

   ¿En qué dirección mira la tortuga cuando se crea?

**Programas mezclados**

.. parsonsprob:: pp3_2_1

   El siguiente programa usa una tortuga para dibujar una L mayúscula como se muestra en la imagen a la izquierda de este texto, <img src="../_static/TurtleL4.png" width="150" align="left" hspace="10" vspace="5" alt="image of a navigational compass and a letter L which is drawn by Turtle"/> Pero las líneas están mezcladas. El programa debe hacer toda la configuración necesaria: importar el módulo de tortuga, obtener la ventana para dibujar y crear la tortuga. Recuerde que la tortuga comienza mirando hacia el este cuando se crea. La tortuga debe girar hacia el sur y dibujar una línea de 150 píxeles de largo y luego girar hacia el este y dibujar una línea de 75 píxeles de largo. Hemos agregado una brújula a la imagen para indicar las direcciones norte, sur, oeste y este. <br /><br /><p>Arrastre los bloques de declaraciones de la columna izquierda a la columna derecha y colóquelos en el orden correcto. Luego haga clic en <i>Check Me</i> para ver si tienes razón. Se le informará si alguna de las líneas está en el orden incorrecto.</p>
   -----
   import turtle
   window = turtle.Screen()
   ella = turtle.Turtle()
   =====
   ella.right(90)
   ella.forward(150)
   =====
   ella.left(90)
   ella.forward(75)

.. parsonsprob:: pp3_2_2

   El siguiente programa usa una tortuga para dibujar una marca de verificación como se muestra a la izquierda, <img src="../_static/TurtleCheckmark4.png" width="150" align="left" hspace="10" vspace="5" alt="image of a navigational compass and a checkmark which is drawn by Turtle."/> Pero las líneas están mezcladas. El programa debe hacer toda la configuración necesaria: importar el módulo de tortuga, obtener la ventana para dibujar y crear la tortuga. La tortuga debe girar hacia el sudeste, dibujar una línea de 75 píxeles de largo, luego girar hacia el noreste y dibujar una línea de 150 píxeles de largo. Hemos agregado una brújula a la imagen para indicar las direcciones norte, sur, oeste y este. El noreste está entre el norte y el este. El sudeste está entre el sur y el este <br /><br /><p>Arrastre los bloques de declaraciones de la columna izquierda a la columna derecha y colóquelos en el orden correcto. Luego haga clic en <i>Check Me</i> para ver si tienes razón. Se le informará si alguna de las líneas está en el orden incorrecto.</p>
   -----
   import turtle
   =====
   window = turtle.Screen()
   =====
   maria = turtle.Turtle()
   =====
   maria.right(45)
   maria.forward(75)
   =====
   maria.left(90)
   maria.forward(150)

.. parsonsprob:: pp3_2_3

  El siguiente programa usa una tortuga para dibujar una sola línea hacia el oeste como se muestra a la izquierda, <img src="../_static/TurtleLineToWest.png" width="150" align="left" hspace="10" vspace="5" alt="image of a line moving in west direction drawn by Turtle. Turtle uses following steps: left turn of 180 degrees, and 75 pixels long line"/> pero las líneas del programa están mezcladas. El programa debe hacer toda la configuración necesaria: importar el módulo de tortuga, obtener la ventana para dibujar y crear la tortuga. La tortuga debe girar hacia el oeste y dibujar una línea de 75 píxeles de largo. <br /><br /><p>Arrastre los bloques de declaraciones de la columna izquierda a la columna derecha y colóquelos en el orden correcto. Luego haga clic en <i>Check Me</i> para ver si tienes razón Se le informará si alguna de las líneas está en el orden incorrecto.</p>
   -----
   import turtle
   window = turtle.Screen()
   jamal = turtle.Turtle()
   jamal.left(180)
   jamal.forward(75)


Un objeto puede tener varios métodos, cosas que puede hacer, y también puede
tener **atributos** ---a veces llamados *propiedades*).Por ejemplo, cada tortuga tiene un atributo *color*.
La invocación del método ``alex.color("rojo")`` hará que alex se ponga roja y la línea que dibuja también será roja.

El color de la tortuga, el ancho de su pluma (cola), la posición de la tortuga
dentro de la ventana, en qué dirección está mirando, y así sucesivamente son parte de su
**estado** actual. Del mismo modo, el objeto de la ventana tiene un color de fondo que forma parte de su estado.

Existen numerosos métodos que nos permiten modificar la tortuga y
objetos de ventana En el ejemplo a continuación, mostramos solo mostrar una pareja y solo hemos comentado
aquellas líneas que son diferentes del ejemplo anterior. Tenga en cuenta también que hemos decidido
llamar a nuestro objeto tortuga *tess*.

.. activecode:: ac3_2_2
    :tour_1: "Overall Tour"; 1-10: Example02_Tour01_Line01; 4: Example02_Tour01_Line02; 6: Example02_Tour01_Line03; 7: Example02_Tour01_Line04; 8: Example02_Tour01_Line05; 10: Example02_Tour01_Line06; 11: Example02_Tour01_Line07; 12: Example02_Tour01_Line08; 14: Example02_Tour01_Line09;
    :tour_2: "Line by Line Tour"; 1: Example01_Tour02_Line01; 3: Example01_Tour02_Line02; 4: Example02_Tour02_Line03; 6: Example02_Tour02_Line04; 7: Example02_Tour02_Line05; 8: Example02_Tour02_Line06; 10: Example02_Tour02_Line07; 11: Example02_Tour02_Line08; 12: Example02_Tour02_Line09; 14: Example02_Tour02_Line10;
    :nocodelens:

    import turtle

    wn = turtle.Screen()
    wn.bgcolor("lightgreen")        # Establece el color de fondo de la ventana

    tess = turtle.Turtle()
    tess.color("blue")              # Hacer azul a tess
    tess.pensize(3)                 # Establece el ancho del pincel

    tess.forward(50)
    tess.left(120)
    tess.forward(50)

    wn.exitonclick()                # espera un clic del usuario en el lienzo


La última línea juega un papel muy importante. La variable wn se refiere a la ventana mostrada
encima. Cuando invocamos su método ``exitonclick``, el programa detiene la ejecución y espera a que el usuario haga clic con el mouse en algún lugar de la ventana.
Cuando se produce este evento de clic, la respuesta es cerrar la ventana de la tortuga y
salir (detener la ejecución) del programa Python.

Cada vez que ejecutamos este programa, aparece una nueva ventana de dibujo y permanecerá en el
pantalla hasta que hagamos clic en él.

.. admonition:: Amplíe este programa ...

    #. Modifique este programa para que antes de crear la ventana, se le solicite el usuario debe ingresar
    el color de fondo deseado. Debe almacenar la respuestas del usuario en una variable, y modificar el color
    de la ventana según los deseos del usuario. (Sugerencia: puede encontrar una lista de nombres de colores
    permitidos en https://www.w3schools.com/colors/colors_names.asp. Incluye algunos bastante
    inusuales, como "PeachPuff" y "HotPink".)
    #. Realice cambios similares para permitir al usuario, en tiempo de ejecución, establecer el color de tess.
    #. Haga lo mismo para el ancho de la pluma de Tess. *Sugerencia:* su diálogo con el usuario devolverá una
    cadena, pero el método ``pensize`` de tess espera que su argumento sea un ``int``. Eso significa que necesitas
    convertir la cadena a un int antes de pasarla a ``pensize``.


**Revisa tu entendimiento**

.. mchoice:: question3_2_2
   :answer_a: Crea un nuevo objeto tortuga que se puede usar para dibujar.
   :answer_b: Define el módulo tortuga que le permitirá crear un objeto Tortuga y dibujar con él.
   :answer_c: Hace que la tortuga dibuje la mitad de un rectángulo en la pantalla.
   :answer_d: Nada, es innecesario.
   :correct: b
   :feedback_a: La línea &quotalex = turtle.Turtle()&quot es lo que realmente crea el objeto tortuga.
   :feedback_b: Tsu línea importa el módulo llamado tortuga, que tiene todas las funciones integradas para dibujar en la pantalla con el objeto Tortuga.
   :feedback_c: Esta funcionalidad se realiza con las líneas: &quotalex.forward(150)&quot, &quotlex.left(90)&quot, and &quotalex.forward(75)&quot
   :feedback_d: Si lo dejamos afuera, Python dará un error diciendo que no conoce el nombre &quotturtle&quot cuando llega a la línea &quotwn = turtle.Screen()&quot

   Considera el siguiente código:

   .. code-block:: python

     import turtle
     wn = turtle.Screen()
     alex = turtle.Turtle()
     alex.forward(150)
     alex.left(90)
     alex.forward(75)

   ¿Qué hace la línea "importar tortuga"?

.. mchoice:: question3_2_3
   :answer_a: Testo es simplemente por claridad. También funcionaría simplemente escribiendo "Turtle()" en lugar de "turtle.Turtle()".
   :answer_b: El punto (.) Es lo que le dice a Python que queremos invocar un nuevo objeto.
   :answer_c: La primera "tortuga" (antes del punto) le dice a Python que nos estamos refiriendo al módulo de tortuga, que es donde se encuentra el objeto "Tortuga".
   :correct: c
   :feedback_a: Debemos especificar el nombre del módulo donde Python puede encontrar el objeto Turtle.
   :feedback_b: El punto separa el nombre del módulo del nombre del objeto. Los paréntesis al final son los que le dicen a Python que invoque un nuevo objeto.
   :feedback_c: Sí, el tipo de tortuga se define en el módulo tortuga. Recuerde que Python distingue entre mayúsculas y minúsculas y Turtle es diferente de la tortuga.

   ¿Por qué escribimos ``turtle.Turtle()`` para obtener un nuevo objeto Turtle?

.. mchoice:: question3_2_4
   :answer_a: Verdadero
   :answer_b: Falso
   :correct: a
   :feedback_a: En este capítulo viste uno llamado alex y otro llamado tess, pero se permite cualquier nombre de variable legal.
   :feedback_b: Una variable, incluida una que se refiere Turtle, puede tener el nombre que elija siempre y cuando siga las convenciones de nomenclatura del Capítulo 2.

   Verdadero o Falso: Un objeto Turtle puede tener cualquier nombre que siga las reglas de nomenclatura del Capítulo 2.

.. mchoice:: question3_2_5
   :answer_a: <img src="../_static/test1Alt1.png" alt="right turn of 90 degrees before drawing, draw a line 150 pixels long, turn left 90, and draw a line 75 pixels long">
   :answer_b: <img src="../_static/test1Alt2.png" alt="left turn of 180 degrees before drawing,  draw a line 150 pixels long, turn left 90, and draw a line 75 pixels long">
   :answer_c: <img src="../_static/test1Alt3.png" alt="left turn of 270 degrees before drawing,  draw a line 150 pixels long, turn left 90, and draw a line 75 pixels long">
   :answer_d: <img src="../_static/test1Alt4v2.png" alt="right turn of 270 degrees before drawing, draw a line 150 pixels long, turn right 90, and draw a line 75 pixels long">
   :answer_e: <img src="../_static/test1correct.png" alt="left turn of 90 degrees before drawing,  draw a line 150 pixels long, turn left 90, and draw a line 75 pixels long">
   :correct: e
   :feedback_a: Este código giraría la tortuga hacia el sur antes de dibujar
   :feedback_b: Este código giraría la tortuga hacia el oeste antes de dibujar
   :feedback_c: Este código giraría la tortuga hacia el sur antes de dibujar
   :feedback_d: Este código es casi correcto, pero el extremo corto estaría orientado hacia el este en lugar de hacia el oeste.
   :feedback_e: Sí, la tortuga comienza a mirar hacia el este, por lo que para girarla hacia el norte puede girar a la izquierda 90 o derecha 270 grados.

   ¿Cuál de los siguientes códigos produciría la siguiente imagen?

   .. image:: Figures/turtleTest1.png
      :alt: long line to north with shorter line to west on top

**Programas mezclados**

.. parsonsprob:: pp3_3_4

   El siguiente programa usa una tortuga para dibujar una L mayúscula en blanco sobre un fondo azul como se muestra a la izquierda, <img src="../_static/BlueTurtleL.png" width="150" align="left" hspace="10" vspace="5" alt="image of a navigational compass and a letter L drawn by Turtle."/> Pero las líneas están mezcladas. El programa debe hacer toda la configuración necesaria y crear la tortuga y establecer el tamaño del corral en 10. La tortuga debe girar hacia el sur, dibujar una línea de 150 píxeles de largo, girar hacia el este y dibujar una línea que sea 75 píxeles de largo. Finalmente, configure la ventana para que se cierre cuando el usuario haga clic en ella.<br /><br /><p>Arrastre los bloques de declaraciones de la columna izquierda a la columna derecha y colóquelos en el orden correcto. Luego haga clic en <i>Check Me</i> para ver si tienes razón Se le informará si alguna de las líneas está en el orden incorrecto.</p>
   -----
   import turtle
   wn = turtle.Screen()
   =====
   wn.bgcolor("blue")
   jamal = turtle.Turtle()
   =====
   jamal.color("white")
   jamal.pensize(10)
   =====
   jamal.right(90)
   jamal.forward(150)
   =====
   jamal.left(90)
   jamal.forward(75)
   wn.exitonclick()

.. parsonsprob:: pp3_2_5

   El siguiente programa usa una tortuga para dibujar una T mayúscula en blanco sobre un fondo verde como se muestra a la izquierda, <img src="../_static/TurtleT.png" width="150" align="left" hspace="10" vspace="5" alt="image of a letter T drawn by Turtle."/> Pero las líneas están mezcladas. El programa debe hacer toda la configuración necesaria, crear la tortuga y establecer el tamaño de la pluma en 10. Después de eso, la tortuga debe girar hacia el norte, dibujar una línea de 150 píxeles de largo, girar hacia el oeste y dibujar una línea eso es 50 píxeles de largo. Luego, la tortuga debe girar 180 grados y dibujar una línea de 100 píxeles de largo. Finalmente, configure la ventana para que se cierre cuando el usuario haga clic en ella.<br /><br /><p>Arrastre los bloques de declaraciones de la columna izquierda a la columna derecha y colóquelos en el orden correcto. Luego haga clic en <i>Check Me</i> para ver si tienes razón Se le informará si alguna de las líneas está en el orden incorrecto.</p>
   -----
   import turtle
   wn = turtle.Screen()
   wn.bgcolor("green")
   jamal = turtle.Turtle()
   jamal.color("white")
   jamal.pensize(10)
   =====
   jamal.left(90)
   jamal.forward(150)
   =====
   jamal.left(90)
   jamal.forward(50)
   =====
   jamal.right(180)
   jamal.forward(100)
   =====
   wn.exitonclick()
