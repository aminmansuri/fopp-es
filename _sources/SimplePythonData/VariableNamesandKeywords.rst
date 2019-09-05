..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-8-
   :start: 1

Nombres de variables y palabras clave
-----------------------------------------

**Los nombres de variables** pueden ser arbitrariamente largos. Pueden contener tanto letras como
dígitos, pero tienen que comenzar con una letra o un guión bajo. Aunque es
legal usar letras mayúsculas, por convención no lo hacemos. Si lo haces, recuerda que
ese caso importa. ``Bruce`` y ``bruce`` son variables diferentes.

.. caution::

    Los nombres de las variables nunca pueden contener espacios.

El carácter de subrayado ( ``_``) también puede aparecer en un nombre. A menudo se usa en
nombres con varias palabras, como ``mi_nombre`` o ``precio_del_te_en_china``.
Hay algunas situaciones en las que los nombres que comienzan con un guión bajo tienen un
significado especial, por lo que una regla segura para principiantes es comenzar todos los nombres con una
letra.

Si le da un nombre ilegal a una variable, obtendrá un error de sintaxis. En el siguiente ejemplo, cada uno
de los nombres de variables es ilegal.

::

    76trombones = "gran desfile"
    more$ = 1000000
    class = "Informática 101"


``76trombones`` es ilegal porque no comienza con una letra.  ``more$``
es ilegal porque contiene un carácter ilegal, el signo de dólar. Pero,
¿qué tiene de malo ``class``?

Resulta que ``class`` es una de las **palabras clave** de Python . Las palabras clave definen
las reglas y la estructura de la sintaxis del lenguaje, y no se pueden usar como nombres de
variables.
Python tiene treinta palabras clave (y de vez en cuando con las actualizaciones,
Python introduce o elimina uno o dos):

======== ======== ======== ======== ======== ========
and      as       assert   break    class    continue
def      del      elif     else     except   exec
finally  for      from     global   if       import
in       is       lambda   nonlocal not      or
pass     raise    return   try      while    with
yield    True     False    None
======== ======== ======== ======== ======== ========

Es posible que desee tener esta lista a mano. Si el intérprete se queja de uno
de sus nombres de variables y no sabe por qué, vea si está en esta lista.

**Revisa tu entendimiento**

.. mchoice:: question2_8_1
   :answer_a: Verdadero
   :answer_b: Falso
   :correct: b
   :feedback_a: - El carácter + no está permitido en nombres de variables.
   :feedback_b: - El carácter + no está permitido en nombres de variables (todo lo demás en este nombre está bien).
   :practice: T

   Verdadero o falso: el siguiente es un nombre de variable legal en Python: A_good_grade_is_A+
