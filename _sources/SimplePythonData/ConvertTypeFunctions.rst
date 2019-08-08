..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-6-
   :start: 1

Funciones de conversión de tipos
-----------------------------------

A veces es necesario convertir valores de un tipo a otro. Python proporciona
algunas funciones simples que nos permitirán hacer eso. Las funciones ``int``, ``float`` y ``str``
(intentarán) convertir sus argumentos en los tipos ``int``, ``float`` y ``str``
respectivamente. Llamamos a estas funciones **conversión de tipo**.

La función ``int`` puede tomar un número de coma flotante o una cadena, y convertirlo
en un int. Para números de coma flotante, *descarta* la porción decimal de
el número: un proceso que llamamos *truncamiento hacia cero* en la recta numérica.
Veamos esto en acción:

.. activecode:: ac2_6_1
    :nocanvas:

    print(3.14, int(3.14))
    print(3.9999, int(3.9999))       # ¡Esto no se redondea al int más cercano!
    print(3.0, int(3.0))
    print(-3.999, int(-3.999))        # Tenga en cuenta que el resultado está más cerca de cero

    print("2345", int("2345"))        # analiza una cadena para producir un int
    print(17, int(17))                # int incluso funciona en enteros
    print(int("23bottles"))


El último caso muestra que una cadena debe ser un número sintácticamente legal,
de lo contrario, obtendrá uno de esos molestos errores de tiempo de ejecución. Modifique el ejemplo eliminando el
``bottles`` y vuelva a ejecutar el programa. Debería ver el número entero ``23``.

El convertidor de tipo ``float`` puede convertir un entero, un flotante o una
cadena en un float.

.. activecode:: ac2_6_2
    :nocanvas:

    print(float("123.45"))
    print(type(float("123.45")))


El convertidor de tipos ``str`` convierte su argumento en una cadena. Recuerde que cuando imprimimos una cadena,
las comillas se eliminan en la ventana de salida. Sin embargo, si imprimimos el tipo, podemos ver que definitivamente es ``str``.

.. activecode:: ac2_6_3
    :nocanvas:

    print(str(17))
    print(str(123.45))
    print(type(str(123.45)))

Una operación común en la que es posible que se deba realizar una conversión de tipo es cuando se concatenan varias cadenas juntas pero se desea incluir un valor numérico como parte de la cadena final. Como no podemos concatenar una cadena con un número entero o de coma flotante, a menudo tendremos que convertir números en cadenas antes de concatenarlos.

.. image:: Figures/type_cast.gif
   :alt: una variable almacena el valor 55. Una declaración de impresión intenta imprimir "el valor es" concatenado con el entero, pero se produce un error de tiempo de ejecución. La solución es convertir el entero en una cadena para que se pueda concatenar.

**Revisa tus conocimientos**

.. mchoice:: question2_6_1
   :answer_a: No se imprime nada. Genera un error de tiempo de ejecución.
   :answer_b: 53
   :answer_c: 54
   :answer_d: 53.785
   :correct: b
   :feedback_a: La declaración es un código Python válido. Llama a la función int en 53.785 y luego imprime el valor que se devuelve.
   :feedback_b: La función int trunca todos los valores después del decimal e imprime el valor entero.
   :feedback_c: Al convertir a un entero, la función int no se redondea.
   :feedback_d: La función int elimina la parte fraccional de 53.785 y devuelve un número entero, que luego se imprime.
   :practice: T

   ¿Qué valor se imprime cuando se ejecuta la siguiente instrucción?

   .. code-block:: python

      print(int(53.785))
