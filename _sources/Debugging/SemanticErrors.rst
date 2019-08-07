..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: debug-6-
   :start: 1

.. index:: semantic error, logic error, error; semantic, error; logic
    single: Holmes, Sherlock
    single: Doyle, Arthur Conan
    single: Linux

Errores Semánticos
--------------------

El tercer tipo de error es el **error semántico**. Si hay un error semántico
en su programa, se ejecutará con éxito en el sentido de que la computadora
no generará ningún mensaje de error. Sin embargo, su programa no hará lo correcto. Va a hacer
algo más. Específicamente, hará lo que usted le dijo que hiciera.

El problema es que el programa que escribió no es el programa que deseaba
escribir. El significado del programa (su semántica) es incorrecto. Identificar
los errores semánticos puede ser complicado porque requieren que trabajes hacia atrás
mirando la salida del programa e intentando descubrir qué está haciendo.

**Chequea tu entendimiento**

.. mchoice:: question4_6_1
   :answer_a: Intentar dividir por 0.
   :answer_b: Olvidar un punto y coma al final de una declaración donde se requiere uno.
   :answer_c: Olvidar dividir entre 100 al imprimir una cantidad porcentual.
   :correct: c
   :feedback_a: Un error semántico es un error en la lógica. En este caso, el programa no produce la salida correcta porque el problema no se resuelve correctamente. Esto se consideraría un error en tiempo de ejecución.
   :feedback_b: Un error semántico es un error en la lógica. En este caso, el programa no produce la salida correcta porque el compilador o el intérprete no pueden procesar el código. Esto se consideraría un error de sintaxis.
   :feedback_c: Esto producirá la respuesta incorrecta porque el programador implementó la solución incorrectamente. Este es un error semántico.
   :practice: T

   ¿Cuál de los siguientes es un error semántico?

.. mchoice:: question4_6_2
   :answer_a: El Programador.
   :answer_b: El Compilador / intérprete.
   :answer_c: La Computadora.
   :answer_d: El Profesor / Instructor.
   :correct: a
   :feedback_a: Debe comprender completamente el problema para poder saber si su programa lo resuelve correctamente.
   :feedback_b: El compilador y / o el intérprete solo harán lo que usted le indique. No entiende cuál es el problema que desea resolver.
   :feedback_c: La computadora no entiende su problema. Simplemente ejecuta las instrucciones que se le dan.
   :feedback_d: Su maestro / instructor puede encontrar la mayoría de sus errores semánticos, pero solo porque tiene experiencia en la resolución de problemas. Sin embargo, es su responsabilidad comprender el problema para poder desarrollar una solución correcta.
   :practice: T

   ¿Quién o qué suele encontrar errores semánticos?
