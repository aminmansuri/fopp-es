..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: condition-11-
   :start: 1

👩‍💻 Configuración de condicionales
=======================================

Antes de escribir sus condicionales, puede ser útil hacer su propio diagrama de flujo que
trazar el flujo de cada condición. Al escribir el flujo, puede determinar mejor cómo
complejo el conjunto de condicionales será así como comprobar si alguna condición no es de
cuidado antes de comenzar a escribirlo.

Para asegurarse de que su código cubra todas las condiciones que desea que cubra, usted
debe agregar comentarios para que cada cláusula que explique lo que debe hacer esa cláusula. Entonces tú
Sin embargo, debe agregar pruebas para cada ruta posible que el programa pueda seguir. Lo que lleva
a ciertas declaraciones condicionales que se ejecutan? ¿Es eso lo que pretendías?

Elegir tu tipo de Condicional
---------------------------------

Al agregar condicionales a su programa, también debe considerar los tipos de condicionales
que están a su disposición y qué encajaría mejor.

.. image:: Figures/valid_conditionals.png

Aunque las usará con frecuencia, recuerde que las declaraciones condicionales no siempre necesitan una cláusula else.
Al decidir el flujo, pregúntese qué desea que suceda bajo una determinada condición.
Por ejemplo, si desea encontrar todas las palabras que tienen la letra 'n' en ellas. Si no hay nada,
eso debe suceder cuando una palabra no contiene la letra 'n', entonces no necesitará otra
cláusula. ¡El programa debería continuar!

.. mchoice:: question7_11_1
   :answer_a: Declaración If - Declaración Else
   :answer_b: Declaración If - Declaración Elif
   :answer_c: Declaración If - Declaración If
   :answer_d: Declaración If - Declaración Elif - Declaración Else
   :correct: c
   :feedback_a: El uso de if/else usa una instrucción else innecesaria o haría un seguimiento incorrecto de una de las variables del acumulador.
   :feedback_b: El uso de if/elif significa que las dos variables no contarían correctamente las palabras que tienen tanto una "t" como una "z".
   :feedback_c: Sí, dos sentencias if realizarán un seguimiento de las dos variables de acumulador diferentes y las actualizarán correctamente.
   :feedback_d: Usar if/elif/else aquí proporcionará una declaración else innecesaria y actualizará incorrectamente una de las variables del acumulador en el caso en que una palabra tenga tanto una "t" como una "z".
   :practice: T

   ¿Cuál es el mejor conjunto de declaraciones condicionales proporcionadas según el siguiente ejercicio? Desea realizar un seguimiento de todas las palabras que tienen la letra 't' y en una variable separada desea realizar un seguimiento de todas las palabras que tienen la letra 'z' en ellas.

.. mchoice:: question7_11_2
   :answer_a: Declaración If - Declaración Elif - Declaración Else
   :answer_b: Declaración If - Declaración Else
   :answer_c: Declaración If - Declaración Anidada If
   :answer_d: Declaración If
   :answer_e: Declaración If - Declaración Anidada If - Declaración Else
   :correct: d
   :feedback_a: Las declaraciones elif y else son innecesarias.
   :feedback_b: La instrucción else es innecesaria.
   :feedback_c: Aunque podría escribir un conjunto de declaraciones condicionales como esta y responder a la solicitud, hay una manera más concisa.
   :feedback_d: Sí, esta es la forma más concisa de escribir un condicional para ese aviso.
   :feedback_e: La declaración else es innecesaria.
   :practice: T

   Seleccione el conjunto más apropiado de declaraciones condicionales para la situación descrita: desea realizar un seguimiento de todas las palabras que contienen "t" y "z".
