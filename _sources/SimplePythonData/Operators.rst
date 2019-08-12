..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-3-
   :start: 1

.. _input:

.. index:: input, input dialog
    single: +; addition
    single: - 
    single: *; multiplication of numbers
    single: **
    multiplication
    operators and operands

Operadores y Operandos
----------------------

Puede construir expresiones complejas a partir de las más simples utilizando **operadores**. Los operadores son tokens especiales que representan cálculos como la suma,
multiplicación y división. Los valores en los que trabaja el operador se denominan
**operandos**.

Las siguientes son todas las expresiones legales de Python cuyo significado es más o menos
claro::

    20 + 32
    5 ** 2
    (5 + 9) * (15 - 7)

Los tokens ``+``, ``-`` y ``*``, y el uso de paréntesis para la agrupación,
significan en Python lo que significan en matemáticas. El asterisco (``*``) es el
token para multiplicación, y ``**`` es el token para exponenciación.
La suma, la resta, la multiplicación y la exponenciación hacen todo lo que usted
esperar.

Recuerde que si queremos ver los resultados del cálculo, el programa debe especificarlo con la palabra ``print``. Se producen los primeros tres cálculos, pero sus resultados no se imprimen.

.. activecode:: ac2_3_1
    :nocanvas:

    20 + 32
    5 ** 2
    (5 + 9) * (15 - 7)
    print(7 + 5)

En Python 3, que usaremos, el operador de división ``/`` produce un resultado de coma flotante (incluso si el resultado es un entero; ``4/2`` es ``2.0``). Si desea una división truncada, que ignora el resto, puede usar el operador ``//`` (por ejemplo, ``5//2`` es ``2``).

.. activecode:: ac2_3_2
    :nocanvas:

    print(9 / 5)
    print(5 / 9)
    print(9 // 5)

Presta especial atención a los ejemplos anteriores. Tenga en cuenta que ``9//5`` se trunca en lugar de redondear, por lo que produce el valor 1 en lugar de 2.

El operador de división truncado, ``//``, también funciona en números de coma flotante. Se trunca al número entero más cercano, pero aún produce un resultado de coma flotante. Por lo tanto, ``7.0 // 3.0`` es ``2.0``.

.. activecode:: ac2_3_3
   :nocanvas:

   print(7.0 / 3.0)
   print(7.0 // 3.0)

.. index:: modulus
    single: %
    remainder

El **operador de módulo**, a veces también llamado **operador restante** o **operador resto entero** funciona en enteros (y expresiones enteras) y produce
el resto cuando el primer operando se divide por el segundo. En Python, el
operador de módulo es un signo de porcentaje (``%``). La sintaxis es la misma que para otros
operadores

.. activecode:: ac2_3_4
    :nocanvas:

    print(7 // 3)    # Este es el operador de división entera
    print(7 % 3)     # Este es el operador restante o módulo

En el ejemplo anterior, 7 dividido por 3 es 2 cuando usamos división entera y hay un resto de 1.

El operador de módulo resulta ser sorprendentemente útil. Por ejemplo, puedes
compruebe si un número es divisible por otro --- si ``x % y`` es cero, entonces
``x`` es divisible por ``y``.
Además, puede extraer el dígito o dígitos más a la derecha de un número.
Por ejemplo, ``x % 10`` produce el dígito más a la derecha de ``x`` (en la base 10).
Del mismo modo, ``x % 100`` produce los dos últimos dígitos.


**Revisa tu entendimiento**

.. mchoice:: question2_3_1
   :answer_a: 4.5
   :answer_b: 5
   :answer_c: 4
   :answer_d: 4.0
   :answer_e: 2
   :correct: a
   :feedback_a: Como el resultado no es un entero, se produce una respuesta de coma flotante.
   :feedback_b: Incluso si "//" se usara, aún se truncaría, no redondearía
   :feedback_c: Quizás esté pensando en el operador de división entera, //
   :feedback_d: / realiza una división exacta, sin truncamiento
   :feedback_e: / hace división. Tal vez estabas pensando en%, que calcula el resto?
   :practice: T

   ¿Qué valor se imprime cuando se ejecuta la siguiente instrucción?

   .. code-block:: python

      print(18 / 4)

.. mchoice:: question2_3_2
   :answer_a: 4.5
   :answer_b: 5
   :answer_c: 4
   :answer_d: 4.0
   :answer_e: 2
   :correct: d
   :feedback_a: - // realiza una división truncada.
   :feedback_b: - Ni "/" ni "//" conduce al redondeo
   :feedback_c: - Aunque se trunca, produce un resultado de coma flotante
   :feedback_d: - Sí, aunque se trunca, produce un resultado de coma flotante porque 18.0 es flotante
   :feedback_e: - / hace división. Tal vez estabas pensando en %, que calcula el resto?
   :practice: T

   ¿Qué valor se imprime cuando se ejecuta la siguiente instrucción?

   .. code-block:: python

      print(18.0 // 4)


.. mchoice:: question2_3_3
   :answer_a: 4.25
   :answer_b: 5
   :answer_c: 4
   :answer_d: 2
   :correct: d
   :feedback_a: El operador % devuelve el resto después de la división.
   :feedback_b: El operador % devuelve el resto después de la división.
   :feedback_c: El operador % devuelve el resto después de la división.
   :feedback_d: El operador % devuelve el resto después de la división.
   :practice: T

   ¿Qué valor se imprime cuando se ejecuta la siguiente instrucción?

   .. code-block:: python

      print(18 % 4)
