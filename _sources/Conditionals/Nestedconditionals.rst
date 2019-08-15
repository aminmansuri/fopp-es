..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: condition-8-
   :start: 1

.. index::
   single: nested conditionals
   single: conditional; nested

Condicionales anidados
----------------------

Un condicional también puede ser **anidado** dentro de otro. Por ejemplo, supongamos que tenemos dos variables enteras, ``x`` e
``y``. El siguiente patrón de selección muestra cómo podríamos decidir cómo se relacionan entre sí.

.. sourcecode:: python

    if x < y:
        print("x es menor que y")
    else:
        if x > y:
            print("x es mayor que y")
        else:
            print("x e y deben ser iguales")

El condicional externo contiene dos ramas.
La segunda rama (la otra desde el exterior) contiene otra declaración ``if``, que
tiene dos ramas propias. Esas dos ramas podrían contener
declaraciones condicionales también.

El flujo de control para este ejemplo se puede ver en esta ilustración de diagrama de flujo.

.. image:: Figures/flowchart_nested_conditional.png


Aquí hay un programa completo que define valores para ``x`` e ``y``. Ejecute el programa y vea el resultado. Luego cambie los valores de las variables para cambiar el flujo de control.

.. activecode:: ac7_8_1

    x = 10
    y = 10

    if x < y:
        print("x es menor que y")
    else:
        if x > y:
            print("x es mayor y")
        else:
            print("x e y deben ser iguales")

.. note::

    En algunos lenguajes de programación, emparejar el if y el else es un problema. Sin embargo, en Python esto no es
    el caso. El patrón de sangría nos dice exactamente qué más pertenece a qué si.

Si todavía está un poco inseguro, aquí está la misma selección como parte de un ejemplo de codelens. Recórralo para ver cómo se elige el ``print`` correcto.

.. codelens:: clens7_8_1
    :python: py3
    :showoutput:

    x = 10
    y = 10

    if x < y:
        print("x es menor que y")
    else:
        if x > y:
            print("x es mayor que y")
        else:
            print("x e y deben ser iguales")


**Revisa tu entendimiento**

.. mchoice:: question7_8_1
   :answer_a: No
   :answer_b: Yes
   :correct: a
   :feedback_a: Esta es una declaración legal anidada if-else. La declaración interna if-else está contenida completamente dentro del cuerpo del bloque else externo.
   :feedback_b: Esta es una declaración legal anidada if-else. La declaración interna if-else está contenida completamente dentro del cuerpo del bloque else externo.
   :practice: T

   ¿El siguiente código causará un error?

   .. code-block:: python

     x = -10
     if x < 0:
         print("El número negativo ",  x, " no es válido aquí.")
     else:
         if x > 0:
             print(x, " es un número positivo")
         else:
             print(x," es 0")
