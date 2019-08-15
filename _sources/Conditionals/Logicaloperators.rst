..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: condition-3-
   :start: 1

.. index::logical operator
   operator; logical
   single: and 
   single: or
   single: not

Operadores lógicos
------------------

Hay tres **operadores lógicos**: ``and``, ``or`` y ``not``.
La semántica (significado) de estos operadores es similar a su significado en inglés.
Por ejemplo, ``x > 0 and x < 10`` es verdadero solo si ``x`` es mayor que 0 *y*
al mismo tiempo, x es menor que 10. ¿Cómo describirías esto en palabras? Dirías que
x está entre 0 y 10, sin incluir los puntos finales.

``n % 2 == 0 or n % 3 == 0`` es verdadero si *alguna* de las condiciones es verdadera,
es decir, si el número es divisible por 2 *o* divisible por 3. En este caso, uno u otro, o
ambas partes tienen que ser verdaderas para que el resultado sea verdadero.

Finalmente, el operador ``not`` niega una expresión booleana, por lo que ``not  x > y``
es verdadero si ``x > y`` es falso, es decir, si ``x`` es menor o igual que
``y``.

.. activecode:: ac7_3_1

    x = 5
    print(x>0 and x<10)

    n = 25
    print(n%2 == 0 or n%3 == 0)

.. admonition:: ¡Error común!

   Hay un error muy común que ocurre cuando los programadores intentan escribir expresiones boolean.
   Por ejemplo, ¿qué pasa si tenemos una variable ``number`` y queremos verificar si su valor es 5, 6 o 7?
   En palabras podríamos decir: "número igual a 5 o 6 o 7". Sin embargo, si traducimos esto a Python, ``number == 5 or 6 or 7``, no será correcto.
   El operador ``or`` debe unir los resultados de tres comprobaciones de igualdad. La forma correcta de escribir esto es ``number == 5 or number == 6 or number == 7``.

   Esto puede parecer una gran cantidad de tipeo, pero es absolutamente necesario. No puedes tomar un atajo.

   Bueno, en realidad, puedes tomar un atajo pero no de esa manera. Más adelante en este capítulo aprenderá sobre
   el operador ``in`` para strings y secuencias: puede escribir ``number in [5, 6, 7]``.

**Revisa tu entendimiento**

.. mchoice:: question7_3_1
   :answer_a: x &gt; 0 and &lt; 5
   :answer_b: 0 &lt; x &lt; 5
   :answer_c: x &gt; 0 or x &lt; 5
   :answer_d: x &gt; 0 and x &lt; 5
   :correct: d
   :feedback_a: Cada comparación debe ser entre exactamente dos valores. En este caso, la expresión de la mano derecha &lt; 5 carece de un valor a su izquierda.
   :feedback_b: Esto es complicado. Aunque la mayoría de los otros lenguajes de programación no permiten esta sintaxis, en Python, esta sintaxis sí está permitida. Sin embargo, no debe usarlo. En cambio, haga comparaciones múltiples usando and u or.
   :feedback_c: Aunque esta es una sintaxis legal de Python, la expresión es incorrecta. Se evaluará como verdadero para todos los números que sean mayores que 0 o menores que 5. Debido a que todos los números son mayores que 0 o menores que 5, esta expresión siempre será verdadera.
   :feedback_d: Sí, con una palabra clave ``and`` ambas expresiones deben ser verdaderas, por lo que el número debe ser mayor que 0 y menor que 5 para que esta expresión sea verdadera.
   :practice: T

   ¿Cuál es la expresión correcta de Python para verificar si un número almacenado en una variable x está entre 0 y 5?
