..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: debug-5
   :start: 1

.. index:: error;runtime, runtime error

Errores de tiempo de ejecución
---------------------------------

El segundo tipo de error es un error de tiempo de ejecución, llamado así porque el error
no aparecerá hasta que ejecute el programa. Estos errores también se llaman
**excepciones** porque generalmente indican que algo excepcional (y
mal) ha sucedido.

Los errores de tiempo de ejecución son raros en los programas simples que verá en los primeros
capítulos, por lo que puede pasar un tiempo antes de que encuentre uno.

**Chequea tu entendimiento**

.. mchoice:: question4_5_1
   :answer_a: Intentar dividir por 0.
   :answer_b: Olvidar los dos puntos al final de una declaración donde se requieren.
   :answer_c: Olvidarse de dividir entre 100 al imprimir una cantidad porcentual.
   :correct: a
   :feedback_a: Python no puede determinar de manera confiable si está tratando de dividir entre 0 hasta que esté ejecutando su programa (por ejemplo, podría estar pidiéndole un valor al usuario y luego dividirlo por ese valor; no puede saber qué valor ingresará el usuario antes de ejecutar el programa).
   :feedback_b: Este es un problema con la estructura formal del programa. Python sabe dónde se requieren dos puntos y puede detectar cuándo falta uno simplemente mirando el código sin ejecutarlo.
   :feedback_c: Esto producirá una respuesta incorrecta, pero Python no lo considerará un error en absoluto. El programador es el que entiende que la respuesta producida es incorrecta.
   :practice: T

   ¿Cuál de los siguientes es un error en tiempo de ejecución?

.. mchoice:: question4_5_2
   :answer_a: El Programador.
   :answer_b: El Intérprete.
   :answer_c: La Computadora.
   :answer_d: El Profesor / Instructor.
   :correct: b
   :feedback_a: Los programadores rara vez encuentramos todos los errores de tiempo de ejecución, hay un programa informático que lo hará por nosotros.
   :feedback_b: Si es ilegal realizar una instrucción en ese punto de la ejecución, el intérprete se detendrá con un mensaje que describa la excepción.
   :feedback_c: Algo así. Pero es una cosa especial en la computadora que lo hace. La computadora independiente sin esta pieza adicional no puede hacerlo.
   :feedback_d: Su profesor o instructor puede encontrar la mayoría de sus errores de tiempo de ejecución, pero solo porque tienen experiencia mirando código y posiblemente escribiendo código. Con experiencia, los errores de tiempo de ejecución son más fáciles de encontrar. Pero también tenemos una forma automatizada de encontrar este tipo de errores.
   :practice: T

   ¿Quién o qué suele encontrar errores de tiempo de ejecución?