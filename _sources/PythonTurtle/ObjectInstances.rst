..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: turtle-4-
   :start: 1

Conceptos orientados a objetos
===============================

Ha sido divertido dibujar cosas con las tortugas. En el proceso, hemos introducido algunos conceptos y términos nuevos. Vamos a sacarlos y examinarlos un poco más cuidadosamente.

Clases definidas por el usuario
--------------------------------
Primero, al igual que Python proporciona una forma de definir nuevas funciones en sus programas, también proporciona una forma de definir nuevas clases de objetos. Más adelante en el libro aprenderá cómo definir funciones, y mucho más tarde, nuevas clases de objetos. Por ahora, solo necesita comprender cómo usarlos.

Instancias
----------

Dada una clase como ``Turtle`` o ``Screen``, creamos una nueva instancia con una sintaxis que se parece a una llamada de función, ``Turtle()``. El intérprete de Python descubre que Turtle es una clase en lugar de una función, por lo que crea una nueva instancia de la clase y la devuelve. Como la clase Turtle se definió en un módulo separado (confusamente, también llamado tortuga), tuvimos que referirnos a la clase como turtle.Turtle. Por lo tanto, en los programas escribimos ``turtle.Turtle()`` para hacer una nueva tortuga. También podríamos escribir ``turtle.Screen()`` para hacer una nueva ventana para que nuestras tortugas puedan pintar.

Atributos
----------

Dada una clase como ``Turtle`` o ``Screen``, creamos una nueva instancia con una sintaxis que se parece a una llamada de función, ``Turtle()``. El intérprete de Python descubre que Turtle es una clase en lugar de una función, por lo que crea una nueva instancia de la clase y la devuelve. Como la clase Turtle se definió en un módulo separado (confusamente, también llamado tortuga), tuvimos que referirnos a la clase como turtle.Turtle. Por lo tanto, en los programas escribimos ``turtle.Turtle()`` para hacer una nueva tortuga. También podríamos escribir ``turtle.Screen()`` para hacer una nueva ventana para que nuestras tortugas puedan pintar.

.. sourcecode:: python

   alex.price = 500
   tess.price = 600
   print(alex.price + tess.price)


Métodos
-------

Las clases tienen **métodos** asociados, que son solo un tipo especial de función. Considere la expresión ``alex.forward(50)`` El intérprete primero busca a alex y descubre que es una instancia de la clase Turtle. Luego busca el atributo hacia adelante y descubre que es un método. Como hay un paréntesis izquierdo directamente a continuación, el intérprete invoca el método, pasando 50 como parámetro.

La única diferencia entre la invocación de un método y otras llamadas a funciones es que la instancia del objeto en sí también se pasa como un parámetro. Así, ``alex.forward(50)`` mueve a alex, mientras que ``tess.forward(50)`` mueve a tess.

Algunos de los métodos de la clase Turtle establecen atributos que afectan las acciones de otros métodos. Por ejemplo, el método de cambio de tamaño cambia el ancho del lápiz de dibujo y el método de color cambia el color del lápiz.

Los métodos devuelven valores, tal como lo hacen las funciones. Sin embargo, ninguno de los métodos de la clase Turtle que ha utilizado devuelve valores útiles como lo hace la función ``len``. Por lo tanto, no tendría sentido construir una expresión compleja como ``tess.forward(50)+75``. Sin embargo, podría tener sentido poner una expresión compleja dentro de los paréntesis: ``tess.forward (x + y)``