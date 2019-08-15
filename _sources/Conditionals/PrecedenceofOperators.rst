..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: condition-5-
   :start: 1

.. index:: conditional branching, conditional execution, if, elif, else,
           if statement, compound statement, statement block, block, body,
           pass statement

Precedencia de operadores
-------------------------

Los operadores aritméticos tienen prioridad sobre los operadores lógicos. Python siempre evaluará primero los operadores aritméticos (**es el más alto, luego la multiplicación / división, luego la suma / resta**). Luego vienen los operadores relacionales. Finalmente, los operadores lógicos se hacen al final. Esto significa que la expresión ``x*5 >= 10 and y-6 <= 20`` se evaluará para realizar primero la aritmética y luego verificar las relaciones. El ``and`` se hará al final. Muchos programadores pueden colocar paréntesis alrededor de las dos expresiones relacionales, ``(x*5 >= 10) and (y-6 <= 20)``. No es necesario hacerlo, pero no causa ningún daño y puede facilitar que las personas lean y entiendan el código.

La siguiente tabla resume la prioridad del operador de mayor a menor. Se puede encontrar una tabla completa para todo el idioma en el `Python Documentation <http://docs.python.org/py3k/reference/expressions.html#expression-lists>`_.

=======   ==============  ===============
Nivel     Categoría        Operadores
=======   ==============  ===============
7(high)   exponent        \**
6         multiplication  \*,/,//,%
5         addition        +,-
4         relational      ==,!=,<=,>=,>,<
3         logical         not
2         logical         and
1(low)    logical         or
=======   ==============  ===============

.. note::

  Este espacio de trabajo se proporciona para su conveniencia. Puede usar esta ventana de activecode para probar lo que quiera.

  .. activecode:: ac7_5_1

.. admonition:: ¡Error común!

   Los estudiantes a menudo combinan incorrectamente los operadores in y or. Por ejemplo, si quieren verificar
   que la letra x está dentro de cualquiera de las dos variables, entonces tienden a escribirla de la siguiente
   forma: ``'x' in y or z``

   Escrito de esta manera, el código no siempre haría lo que el programador pretendía. Esto es porque el
   operador ``in`` está solo en el lado izquierdo de la instrucción o. No se implementa en ambos
   lados de la declaración or. Para verificar adecuadamente que x está dentro de cualquiera de las variables, el
   operador debe usarse en ambos lados, que se ve así:

   .. sourcecode:: python

       'x' in y or 'x' in z

**Revisa tu entendimiento**

.. mchoice:: question7_5_1
   :answer_a: ((5*3) &gt; 10) and ((4+6) == 11)
   :answer_b: (5*(3 &gt; 10)) and (4 + (6 == 11))
   :answer_c: ((((5*3) &gt; 10) and 4)+6) == 11
   :answer_d: ((5*3) &gt; (10 and (4+6))) == 11
   :correct: a
   :feedback_a: Sí, * y + tienen mayor prioridad, seguido de &gt; y ==, y luego la palabra clave &quot;and&quot;
   :feedback_b: Los operadores aritméticos (*, +) tienen mayor prioridad que los operadores de comparación (&gt;, ==)
   :feedback_c: Esta agrupación supone que Python simplemente evalúa de izquierda a derecha, lo cual es incorrecto. Sigue la precedencia que figura en la tabla de esta sección.
   :feedback_d: Esta agrupación supone que &quot; y &quot; tiene una precedencia mayor que ==, lo cual no es cierto.
   :practice: T

   ¿Cuál de los siguientes expresa correctamente la precedencia de los operadores (usando paréntesis) en la siguiente expresión: 5*3 > 10 and 4+6==11

Aquí hay una animación para la expresión anterior:

.. showeval:: se_ac7_5_1
   :trace_mode: true

   5 * 3 > 10 and 4 + 6 == 11
   ~~~~
   {{5 * 3}}{{15}} > 10 and 4 + 6 == 11
   {{15 > 10}}{{True}} and 4 + 6 == 11
   True and {{4 + 6}}{{10}} == 11
   True and {{10 == 11}}{{False}}
   {{True and False}}{{False}}
