..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: UFunc-1-
   :start: 1

👩‍💻 Decodificando una Función
-----------------------------------

En general, cuando vea una definición de función, intentará descubrir qué hace la función, pero,
a menos que esté escribiendo la función, no le importará *cómo lo hace*.

Por ejemplo, aquí hay un resumen de algunas funciones que ya hemos visto.

* ``input`` toma un parámetro, un string. Se muestra al usuario.
  Lo que el usuario escriba se devuelve, como un string.

* ``int`` toma un parámetro. Puede ser de cualquier tipo que se pueda convertir
  en un número entero, como un número de coma flotante o un string cuyos caracteres
  son todos dígitos.

A veces, se le presentará una definición de función cuya operación no se resume tan claramente
como anteriormente. A veces tendrá que mirar el código, ya sea la definición de la función o el código que
invoca la función para descubrir qué hace.

Para comprender mejor cualquier función, debe intentar responder las siguientes preguntas:

1. ¿Cuántos parámetros tiene?

#. ¿Cuál es el tipo de valores que se pasarán cuando la función es
   invocado?

#. ¿Cuál es el tipo del valor de retorno que produce la función cuando
   ejecuta?

Si intenta utilizar funciones, las que escribe o las que otros escriben, sin poder responder
En estas preguntas, encontrará que sus sesiones de depuración son largas y dolorosas.

La primera pregunta siempre es fácil de responder. Mira la línea con la definición de la función, mira dentro
los paréntesis y cuente cuántos nombres de variables hay.

La segunda y la tercera pregunta no siempre son tan fáciles de responder. En Python, a diferencia de otros idiomas de
programación, no se declara que las variables tengan tipos fijos, y lo mismo se aplica a los nombres de las variables
que aparecen como parámetros formales de funciones. Tienes que resolverlo por contexto.

Para averiguar los tipos de valores que una función espera recibir como parámetros, puede mirar las
invocaciones de funciones o puede mirar las operaciones que se realizan en los parámetros dentro de la función.

Aquí hay algunas pistas que pueden ayudarlo a determinar el tipo de objeto asociado con cualquier variable, incluido un
parámetro de función. Si tú ves...

* ``len(x)``, entonces x debe ser una cadena o una lista. (En realidad, también puede ser un
  diccionario, en cuyo caso es equivalente a la expresión
  ``len(x.keys())``. Más adelante en el curso, también veremos alguna otra secuencia de
  tipos que podrían ser). x no puede ser un número o un Boolean.
* ``x - y``, x e y deben ser números (int o float)
* ``x + y``, x e y deben ser números, ambas strings o ambas listas
* ``x[3]``, x debe ser una cadena o una lista que contenga al menos cuatro elementos, o x
  debe ser un diccionario que incluya 3 como clave.
* ``x['3']``, x debe ser un diccionario, con '3' como clave.
* ``x[y:z]``, x debe ser una secuencia (cadena o lista), z e y deben ser
  enteros
* ``x and y``, x e y deben ser Boolean
* ``for x in y``, y debe ser una secuencia (string o lista) o un diccionario (en cuyo caso son realmente las claves del diccionario); x debe ser un caracter
  si y es una cadena; si y es una lista, x podría ser de cualquier tipo.

**Revisa tu entendimiento: decodificar esta definición de función**

.. mchoice:: question200_1_1
   :answer_a: 0
   :answer_b: 1
   :answer_c: 2
   :answer_d: 3
   :answer_e: No sabría decirlo
   :correct: d
   :feedback_a: Cuente el número de nombres de variables dentro de los paréntesis en la línea 1.
   :feedback_b: Cuente el número de nombres de variables dentro de los paréntesis en la línea 1.
   :feedback_c: Cuente el número de nombres de variables dentro de los paréntesis en la línea 1.
   :feedback_d: x, y, & z.
   :feedback_e: Puede verlo mirando dentro de los paréntesis en la línea 1. Cada nombre de variable está separado por una coma.
   :practice: T

   ¿Cuántos parámetros toma la función cyu3?

   .. code-block:: python

      def cyu3(x, y, z):
         if x - y > 0:
            return y -2
         else:
            z.append(y)
            return x + 3
         
.. mchoice:: question200_1_2
   :multiple_answers:
   :answer_a: integer
   :answer_b: float
   :answer_c: list
   :answer_d: string
   :answer_e: No sabría decirlo
   :correct: a,b
   :feedback_a: x - y, y-2, y x+3 se pueden realizar en enteros.
   :feedback_b: x - y, y-2, y x+3 se pueden realizar en floats.
   :feedback_c: x - y, y-2, y x+3 no se pueden realizar en listas.
   :feedback_d: x - y e y-2 no se puede realizar en cadenas.
   :feedback_e: Puede distinguir algunas de las operaciones que se realizan en ellos.
   :practice: T

   ¿Cuáles son los posibles tipos de variables x e y?

   .. code-block:: python

      def cyu3(x, y, z):
         if x - y > 0:
            return y -2
         else:
            z.append(y)
            return x + 3
         
.. mchoice:: question200_1_3
   :multiple_answers:
   :answer_a: integer
   :answer_b: float
   :answer_c: list
   :answer_d: string
   :answer_e: No sabría decirlo
   :correct: c
   :feedback_a: append no se puede realizar en enteros.
   :feedback_b: append no se puede realizar en floats.
   :feedback_c: append se puede realizar en lists.
   :feedback_d: append no se puede realizar en strings.
   :feedback_e: Puede distinguir algunas de las operaciones que se realizan en él.
   :practice: T

   ¿Cuáles son los posibles tipos de variable z?

   .. code-block:: python

      def cyu3(x, y, z):
         if x - y > 0:
            return y -2
         else:
            z.append(y)
            return x + 3

.. mchoice:: df_question200_1_3
   :multiple_answers:
   :answer_a: integer
   :answer_b: float
   :answer_c: list
   :answer_d: string
   :answer_e: No sabría decirlo
   :correct: a,b
   :feedback_a: y-2 o  x+3 podría producir un número entero.
   :feedback_b: y-2 o  x+3 podría producir un float.
   :feedback_c: y-2 o  x+3 podría producir una lista.
   :feedback_d: ninguno de y-2 o  x+3 podría producir un string.
   :feedback_e: Se puede deducir de las expresiones que siguen a la palabra retorno.
   :practice: T

   ¿Cuáles son los tipos posibles del valor de retorno de cyu3?

   .. code-block:: python

      def cyu3(x, y, z):
         if x - y > 0:
            return y -2
         else:
            z.append(y)
            return x + 3
