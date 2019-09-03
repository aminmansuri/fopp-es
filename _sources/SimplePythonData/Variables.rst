..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-7-
   :start: 1

.. _variables:

Variables
---------

.. youtube:: TrrzfHUtyVw
    :divid: assignvid
    :height: 315
    :width: 560
    :align: left

Una de las características más poderosas de un lenguaje de programación es la capacidad de
manipular **variables**. Una variable es un nombre que se refiere a un valor.

**Las declaraciones de asignación** crean nuevas variables y también les dan valores para consultar.

.. sourcecode:: python

    message = "¿Qué hay de nuevo viejo?"
    n = 17
    pi = 3.14159

Este ejemplo hace tres asignaciones. El primero asigna el valor de la cadena
``"¿Qué hay de nuevo viejo?"`` a una nueva variable llamada ``message``. El segundo asigna el
entero ``17`` a ``n``, y el tercero asigna el número de coma flotante
``3.14159``  a una variable llamada ``pi``.

El **símbolo de asignación**, ``=`, no debe confundirse con *igualdad* (veremos más adelante que la igualdad usa el símbolo
``==``). La instrucción de asignación enlaza un *nombre*, a la izquierda
del operador, con un *valor*, en el lado derecho. Es por eso que
obtendrá un error si ingresa:

.. sourcecode:: python

    17 = n

.. tip::

   Al leer o escribir código, dígase "n se le asigna 17" o "n obtiene
   el valor 17"o"n es una referencia al objeto 17"o"n se refiere al objeto 17".  **No digas"n es igual a 17"**.

Una forma común de representar variables en papel es escribir el nombre con una flecha
apuntando al valor de la variable. Este tipo de figura, conocida como **diagrama de referencia**, a menudo se denomina **estado
instantáneo** porque muestra en qué estado se encuentra cada una de las variables en un
instante particular en el tiempo. (Piense en ello como el estado mental de la variable).
Este diagrama muestra el resultado de ejecutar las instrucciones de asignación que se muestran arriba.

.. image:: Figures/refdiagram1.png
   :alt: Reference Diagram

Si su programa incluye una variable en cualquier expresión, cada vez que se ejecute esa expresión producirá el valor
que está vinculado a la variable en el momento de la ejecución. En otras palabras, evaluar una variable busca su valor.

.. activecode:: ac2_7_1
    :nocanvas:

    message = "¿Qué hay de nuevo viejo?"
    n = 17
    pi = 3.14159

    print(message)
    print(n)
    print(pi)

En cada caso, el resultado es el valor de la variable.
Para ver esto con aún más detalle, podemos ejecutar el programa usando codelens.

.. codelens:: clens2_7_1
    :python: py3
    :showoutput:

    message = "¿Qué hay de nuevo viejo?"
    n = 17
    pi = 3.14159

    print(message)
    print(n)
    print(pi)
    
Ahora, a medida que avanza por las declaraciones, puede ver que
las variables y los valores a los que hacen referencia como esas referencias son
creados.

Usamos variables en un programa para "recordar" cosas, como el puntaje actual en
el partido de fútbol. Pero las variables son *variables*. Esto significa que pueden cambiar
con el tiempo, al igual que el marcador en un partido de fútbol. Puedes asignar un valor
a una variable y luego asignar un valor diferente a la misma variable.

.. note::

    Esto es diferente al de las matemáticas. En álgebra, si le das a ``x`` el valor 3,
    no puede cambiar para referirse a un valor diferente a la mitad de sus
    cálculos!

Para ver esto, lea y luego ejecute el siguiente programa.
Notarás que cambiamos el valor de ``día`` tres veces, y en el tercero
asignación incluso le damos un valor que es de un tipo diferente.

.. codelens:: clens2_7_2
    :python: py3
    :showoutput:

    day = "Jueves"
    print(day)
    day = "Viernes"
    print(day)
    day = 21
    print(day)

Una gran cantidad de programación se trata de que la computadora recuerde cosas. Por ejemplo, podríamos querer mantener
realizar un seguimiento de la cantidad de llamadas perdidas en su teléfono. Cada vez que se pierda otra llamada, organizaremos la actualización,
o cambie la variable para que siempre refleje el valor correcto.

Cualquier lugar en un programa de Python donde se espera un número o cadena, puede poner un nombre de variable en su lugar. El intérprete de Python sustituirá el valor del nombre de la variable.

Por ejemplo, podemos averiguar el tipo de datos del valor actual de una variable colocando el nombre de la variable dentro de los paréntesis después del nombre de la función ``tipo``.

.. activecode:: ac2_7_2
    :nocanvas:

    message = "¿Qué hay de nuevo viejo?"
    n = 17
    pi = 3.14159

    print(type(message))
    print(type(n))
    print(type(pi))

.. note::
   Si ha programado en otro lenguaje como Java o C++, puede estar acostumbrado a la idea de que *las variables* tienen tipos que se declaran cuando el nombre de la variable se introduce por primera vez en un programa. Python no hace eso. Las variables no tienen tipos en Python; *valores* do. Eso significa que es aceptable en Python que un nombre de variable se refiera a un número entero y luego que el mismo nombre de variable se refiera a una cadena. Esto casi nunca es una buena idea, porque confundirá a los lectores humanos (incluido usted), pero el intérprete de Python no se quejará.

**Revisa tu entendimiento**

.. mchoice:: question2_7_1
   :answer_a: No se imprime nada. Se produce un error de tiempo de ejecución.
   :answer_b: Jueves
   :answer_c: 32.5
   :answer_d: 19
   :correct: d
   :feedback_a: Es legal cambiar el tipo de datos que contiene una variable en Python.
   :feedback_b: Este es el primer valor asignado al día variable, pero las siguientes declaraciones reasignan esa variable a nuevos valores.
   :feedback_c: Este es el segundo valor asignado a la variable day, pero la siguiente instrucción reasigna esa variable a un nuevo valor.
   :feedback_d: La variable day contendrá el último valor asignado cuando se imprima.
   :practice: T

   ¿Qué se imprime cuando se ejecutan las siguientes declaraciones?

   .. code-block:: python

     day = "Jueves"
     day = 32.5
     day = 19
     print(day)
