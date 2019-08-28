..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: debug-4-
   :start: 1

.. index:: syntax error, error; syntax; runtime error, exception, safe language

Errores de Sintaxis
----------------------

Python solo puede ejecutar un programa si el programa es sintácticamente correcto;
de lo contrario, el proceso falla y devuelve un mensaje de error. **Sintaxis** se refiere
a la estructura de un programa y las reglas sobre esa estructura. Por ejemplo,
en inglés, una oración debe comenzar con una letra mayúscula y terminar con un punto.
esta oración contiene un **error de sintaxis**. Esta también

Para la mayoría de los lectores, algunos errores de sintaxis no son un problema significativo, que es la razón
por la que podemos leer la poesía de E. E. Cummings sin problemas.
Python no es tan indulgente. Si hay un solo error de sintaxis en cualquier lugar de su
programa, Python mostrará un mensaje de error y se cerrará. No serás capaz
de completar la ejecución de tu programa. Durante las primeras semanas de su carrera de programación, usted
probablemente pasará mucho tiempo rastreando errores de sintaxis. Sin embargo, a medida que gana
experiencia, cometerá menos errores y también podrá encontrar sus errores más rápido.

¿Puedes detectar el error de sintaxis en el código a continuación?

.. activecode:: ac4_4_1

   print("Hello World!"

**Verifica tu Trabajo**

.. mchoice:: question4_4_1
   :answer_a: Intentar dividir por 0.
   :answer_b: Olvidar los dos puntos al final de una declaración donde se los requiere.
   :answer_c: Olvidar dividir entre 100 al imprimir una cantidad porcentual.
   :correct: b
   :feedback_a: Un error de sintaxis es un error en la estructura del código de Python que se puede detectar antes de ejecutar el programa. Python generalmente no puede decir si está tratando de dividir entre 0 hasta que esté ejecutando su programa (por ejemplo, podría estar pidiéndole un valor al usuario y luego dividirlo por ese valor; no puede saber qué valor ingresará el usuario antes de ejecutar el programa programa).
   :feedback_b: Este es un problema con la estructura formal del programa. Python sabe dónde se requieren dos puntos y puede detectar cuándo falta uno simplemente mirando el código sin ejecutarlo.
   :feedback_c: Esto producirá la respuesta incorrecta, pero Python no lo considerará un error en absoluto. El programador es el que entiende que la respuesta producida es incorrecta.
   :practice: T

   ¿Cuál de los siguientes es un error de sintaxis?

.. mchoice:: question4_4_2
   : respuesta_a: El programador.
   :answer_b: El compilador / intérprete.
   :answer_c: La computadora.
   :answer_d: El profesor / instructor.
   :correct: b
   :feedback_a: Los programadores rara vez encuentran todos los errores de sintaxis, hay un programa de computadora que lo hará por nosotros.
   :feedback_b: El compilador y/o intérprete es un programa de computadora que determina si su programa está escrito de manera que pueda traducirse al lenguaje de máquina para su ejecución.
   :feedback_c: Bueno, más o menos. Pero es una cosa especial en la computadora que lo hace. La computadora independiente sin esta pieza adicional no puede hacerlo.
   :feedback_d: es posible que su maestro e instructor puedan encontrar la mayoría de sus errores de sintaxis, pero solo porque tienen experiencia en mirar código y posiblemente escribir código. Con la experiencia, los errores de sintaxis son más fáciles de encontrar. Pero también tenemos una forma automatizada de encontrar este tipo de errores.
   :practice: T

    ¿Quién o qué suele encontrar errores de sintaxis?

