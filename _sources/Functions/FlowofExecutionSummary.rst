..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: func-10-
   :start: 1

.. index:: flow of execution

Resumen de flujo de ejecución
--------------------------------

Cuando trabaja con funciones, es realmente importante saber el orden en que se ejecutan las declaraciones. Esto es
llamado el **flujo de ejecución** y ya lo hemos hablado varias veces en este capítulo.

La ejecución siempre comienza en la primera declaración del programa. Las declaraciones se ejecutan una a la vez, en orden, desde
de arriba hacia abajo. Las definiciones de funciones no alteran el flujo de ejecución del programa, pero recuerde que las declaraciones
dentro de la función no se ejecutan hasta que se llama a la función. Las llamadas a funciones son como un desvío en el flujo de
ejecución. En lugar de pasar a la siguiente instrucción, el flujo salta a la primera línea de la función llamada, se ejecuta
todas las declaraciones allí, y luego regresa para continuar donde lo dejó.

Eso suena bastante simple, hasta que recuerdes que una función puede llamar a otra. Mientras está en el medio de una función,
el programa podría tener que ejecutar las declaraciones en otra función. Pero al ejecutar esa nueva función,
¡El programa podría tener que ejecutar otra función más!

Afortunadamente, el intérprete de Python es experto en realizar un seguimiento de dónde está, por lo que cada vez que se completa una función, el
el programa continúa donde lo dejó en la función que lo llamó. Cuando llega al final del programa, finaliza.

¿Qué significa todo eso para nosotros cuando tratamos de entender un programa? No lea de arriba a abajo. En cambio, siga el
flujo de ejecución. Esto significa que leerá las declaraciones def mientras escanea de arriba a abajo, pero usted
debe omitir el cuerpo de la función hasta llegar a un punto donde se llama esa función.

**Revisa tu entendimiento**

.. mchoice:: question11_10_1
   :answer_a: 25
   :answer_b: 5
   :answer_c: 125
   :answer_d: 32
   :correct: a
   :feedback_a: El cuadrado de la función devuelve el cuadrado de su entrada (a través de una llamada a pow).
   :feedback_b: Lo que se imprime es la salida de la función cuadrada. 5 es la entrada a la función cuadrada.
   :feedback_c: Note que pow se llama desde dentro del cuadrado con una base (b) de 5 y una potencia (p) de dos.
   :feedback_d: Note que pow se llama desde dentro del cuadrado con una base (b) de 5 y una potencia (p) de dos.
   :practice: T

   Considere el siguiente código de Python. Tenga en cuenta que los números de línea se incluyen a la izquierda.

   .. code-block:: python
      :linenos:

      def pow(b, p):
          y = b ** p
          return y
     
      def square(x):
          a = pow(x, 2)
          return a
     
      n = 5
      result = square(n)
      print(result)

   ¿Qué imprime esta función?
