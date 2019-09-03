..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-10-
   :start: 1

.. index:: expression

Sentencias y expresiones
---------------------------

.. youtube:: 3WgmLIsXFkI
    :divid: expression_vid
    :height: 315
    :width: 560
    :align: left

Una **sentencia** es una instrucción que el intérprete de Python puede ejecutar. Solo has visto la sentencia
de asignación hasta ahora. Algunos otros tipos de sentencias que verá en capítulos futuros son sentencias ``while``,
sentencias ``for``, sentencias ``if`` y sentencias ``import``. (¡Hay otros tipos también!)

Una **expresión** es una combinación de literales, nombres de variables, operadores y llamadas a funciones.
Las expresiones necesitan ser evaluadas. El resultado de evaluar una expresión es un *valor* u *objeto*.

.. image:: Figures/expression_value_type.png
   :alt: table that shows expressions and their value, and type.

Si le pide a Python que ``imprima`` una expresión, el intérprete **evalúa** la expresión y muestra el resultado.

.. activecode:: ac2_10_1
    :nocanvas:

    print(1 + 1 + (2 * 3))
    print(len("hello"))

En este ejemplo, ``len`` es una función de Python incorporada que devuelve el número de caracteres en una cadena.

La *evaluación de una expresión* produce un valor, por lo que las expresiones pueden aparecer en la mano derecha
lado de las sentencias de asignación. Un literal en sí mismo es una expresión simple, y también lo es una variable.

.. activecode:: ac2_10_2
    :nocanvas:

    y = 3.14
    x = len("Hola")
    print(x)
    print(y)


En un programa, en cualquier lugar donde un valor literal (una cadena o un número) sea aceptable, una expresión más complicada también es aceptable. Aquí están todos los tipos de expresiones que hemos visto hasta ahora:

literal
   e.g., "Hola" o 3.14

nombre de variable
   e.g., x o len

expresión del operador
   <expresión> operador-nombre <expresión>

expresiones de llamada a funciones
   <expresión>(<expresión separada por coma>)

Observe que las expresiones de operador (como ``+`` y ``*``) tienen subexpresiones antes y después del operador. Cada uno de estos pueden ser expresiones simples o complejas. De esa manera, puedes construir expresiones bastante complicadas.

.. activecode:: ac2_10_3
    :nocanvas:

    print(2 * len("Hola") + len("Adiós"))

De manera similar, cuando se llama a una función, en lugar de poner un literal dentro de los paréntesis, se puede colocar una expresión compleja dentro de los paréntesis. (Nuevamente, proporcionamos un código oculto que define las funciones ``square`` y ``sub``).

.. activecode:: ac2_10_4
   :nocanvas:
   :hidecode:

   def square(x):
      return x * x

   def sub(x, y):
      return x - y

.. activecode:: ac2_10_5
   :nocanvas:
   :include: ac2_10_4
   
   x = 2
   y = 1
   print(square(y + 3))
   print(square(y + square(x)))
   print(sub(square(y), square(x)))
   
Con una llamada a función, incluso es posible tener una expresión compleja antes del paréntesis izquierdo, siempre que esa expresión se evalúe como un objeto de función. Por ahora, sin embargo, solo usaremos nombres de variables (como square, sub y len) que estén directamente vinculados a objetos de función.

Es importante comenzar a aprender a leer el código que contiene expresiones complejas. El intérprete de Python examina
cualquier línea de código y *la analiza* en componentes. Por ejemplo, si ve un símbolo ``=``, intentará tratar la línea
completa como una sentencia de asignación. Esperará ver un nombre de variable válido a la izquierda de =, y analizará todo
a la derecha de = como una expresión. Intentará determinar si el lado derecho es un literal, un nombre de variable,
una expresión de operador o una expresión de llamada de función. Si se trata de una expresión de operador, intentará analizar
 las subexpresiones antes y después del operador. Y así. Debería aprender a analizar líneas de código de la misma manera.

Para evaluar una expresión de operador, el intérprete de Python primero evalúa completamente la expresión antes del operador,
luego la siguiente, luego combina los dos valores resultantes usando el operador. Para evaluar una expresión de llamada
de función, el intérprete evalúa la expresión antes de los paréntesis (es decir, busca el nombre de la función). Luego
trata de evaluar cada una de las expresiones dentro de los paréntesis. Puede haber más de uno, separados por comas.
Los valores de esas expresiones se pasan como entradas a la función cuando se llama a la función.

Si una expresión de llamada de función es una subexpresión de una expresión más complicada, ya que ``square(x)`` es
en ``sub(square(y), square(x))``, entonces el valor de retorno de ``square(x)`` se pasa como una entrada a la función
``sub``. Esta es una de las cosas difíciles a las que tendrá que acostumbrarse a hacer ejercicio cuando lea (o escriba)
el código. En este ejemplo, se llama a la función ``square`` (dos veces) antes de que se llame a la función ``sub``,
aunque la función ``sub`` viene primero cuando se lee el código de izquierda a derecha.

.. showeval:: eval2_10_1
    :trace_mode: true

    x = 5
    y = 7
    add(square(y), square(x))
    ~~~~
    {{add}}{{add}}(square(y), square(x)) ## add es una función, así que evalúa sus argumentos
    add({{square}}{{square}}(y), square(x)) ## square es una función, así que evalúa sus argumentos
    add(square({{y}}{{7}}), square(x)) 
    add({{square(7)}}{{49}}, square(x))
    add(49, {{square}}{{square}}(x)) ## square es una función, así que evalúa sus argumentos
    add(49, square({{x}}{{5}}))
    add(49, {{square(5)}}{{25}})
    {{add(49, 25)}}{{74}}

Para comenzar a darle algo de práctica para leer y comprender expresiones complicadas, intente resolver el problema de
Parsons a continuación. Tenga cuidado de no poner sangrías en ninguna de las líneas de código; eso es algo que vendrá más adelante en el curso.


.. parsonsprob:: pp2_10_1

   Ordene los fragmentos de código en el orden en que el intérprete de Python los evaluaría. x es 2 e y es 3. Ahora el intérprete está ejecutando `square(x + sub(square(y), 2 *x))`.

   -----
   busque la variable square para obtener el objeto de función
   =====
   busque la variable x para obtener 2
   =====
   busque la variable sub para obtener el objeto de función
   =====
   busque la variable square, nuevamente, para obtener el objeto de función
   =====
   busque la variable y para obtener 3
   =====
   ejecute la función square en la entrada 3, devolviendo el valor 9
   =====
   busque la variable x, nuevamente, para obtener 2
   =====
   multiplique 2 * 2 para obtener 4
   =====
   ejecute la subfunción, pasando las entradas 9 y 4, devolviendo el valor 5
   =====
   sume 2 y 5 para obtener 7
   =====
   ejecute la función square, nuevamente, en la entrada 7, devolviendo el valor 49
