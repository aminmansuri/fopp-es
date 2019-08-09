..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-16-
   :start: 1

.. index:: order of operations, rules of precedence

Entrada
----------

.. el video debe ir aquí, tomado del video de YouTube de Steve en impresión + entrada

Nuestros programas se vuelven más interesantes si no hacen exactamente lo mismo cada vez que se ejecutan.
Una forma de hacerlos más interesantes es obtener **entrada** del usuario. Por suerte, en Python
Hay una función incorporada para realizar esta tarea. Se llama ``input``.

.. sourcecode:: python

    n = input("Por favor, escriba su nombre:")

La función de entrada permite al programador proporcionar una **cadena de solicitud**. En el ejemplo anterior,
es "Por favor ingrese su nombre:". Cuando se evalúa la función, la solicitud es
se muestra (en el navegador, busque una ventana emergente).
El usuario del programa puede escribir texto y presionar ``return``. Cuando esto
sucede que el texto ingresado es devuelto por la función ``input``,
y en este caso asignado a la variable ``n``. Ejecute este ejemplo varias veces y
pruebe con algunos nombres diferentes en el cuadro de entrada que aparece.

.. activecode:: ac2_16_1

    n = input("Por favor, escriba su nombre: ")
    print("Hola", n)

Es muy importante tener en cuenta que la función ``input`` devuelve un valor de cadena. Incluso si tú
le pedía al usuario que ingresara su edad, obtendría una cadena como
``"17"``. Sería su trabajo, como programador, convertir esa cadena en
un int o un flotador, usando las funciones de convertidor ``int`` o ``float`` que vimos
más temprano.

.. note::

    A menudo usamos la palabra "input" (o, como sinónimo, argumento) para referirnos a los valores que se pasan a cualquier función. No confunda eso con la función `` input '', que le pide al usuario de un programa que escriba un valor. Al igual que cualquier función, `` input`` toma un argumento de entrada y produce una salida. La entrada es una cadena de caracteres que se muestra como una solicitud al usuario. La salida es cualquier cadena de caracteres que el usuario escriba.

    Esto es análogo a la posible confusión de la función "salidas" con el contenido de la ventana de salida. Cada función produce una salida, que es un valor de Python. Solo la función de impresión coloca cosas en la ventana de salida. La mayoría de las funciones toman entradas, que son valores de Python. Solo la función de entrada invita a los usuarios a escribir algo.

Aquí hay un programa que convierte una cantidad de segundos en recuentos de horas más legibles por humanos,
minutos y segundos. Una llamada a ``input ()`` le permite al usuario ingresar el número de segundos.
Luego convertimos esa cadena en un número entero. A partir de ahí usamos la división y el módulo.
operadores para calcular los resultados.

.. activecode:: ac2_16_2

    str_seconds = input("Ingrese la cantidad de segundos que desea convertir")
    total_secs = int(str_seconds)

    hours = total_secs // 3600
    secs_still_remaining = total_secs % 3600
    minutes =  secs_still_remaining // 60
    secs_finally_remaining = secs_still_remaining  % 60

    print("Hrs=", hours, "mins=", minutes, "secs=", secs_finally_remaining)


La variable ``str_seconds`` se referirá a la cadena que ingresa el usuario. Como dijimos anteriormente, aunque esta cadena puede ser ``7684``, sigue siendo una cadena y no un número. Para convertirlo en un entero, usamos la función ``int``.
El resultado es referido por ``total_secs``. Ahora, cada vez que ejecuta el programa, puede ingresar un nuevo valor para la cantidad de segundos que se convertirán.

**Revisa tu entendimiento**

.. mchoice:: question2_16_1
   :answer_a: &lt;class 'str'&gt;
   :answer_b: &lt;class 'int'&gt;
   :answer_c: &lt;class 18&gt;
   :answer_d: 18
   :correct: a
   :feedback_a: Todas las entradas de los usuarios se leen como una cadena.
   :feedback_b: Aunque el usuario escribió un número entero, no entra en el programa como un número entero.
   :feedback_c: 18 es el valor de lo que escribió el usuario, no el tipo de dato.
   :feedback_d: 18 es el valor de lo que escribió el usuario, no el tipo de dato.
   :practice: T

   ¿Qué se imprime cuando se ejecutan las siguientes declaraciones?

   .. code-block:: python

     n = input("Ingrese su edad:")
     # ingreso 18
     print(type(n))
