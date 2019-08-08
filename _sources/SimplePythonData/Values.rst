..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-2-
   :start: 1

Valores y tipos de datos
---------------------------

Un **valor** es una de las cosas fundamentales --- como una palabra o un número --- que manipula un programa.
Algunos valores son ``5`` (el resultado cuando agregamos ``2 + 3``) y ``"¡Hola, mundo!"``. Estos objetos se clasifican en
diferentes clases o tipos de datos: 4 es un número entero y "¡Hola, mundo!" es una cadena, llamada así porque contiene una
cadena o secuencia de letras. Usted (y el intérprete) pueden identificar cadenas porque están entre comillas.

Podemos especificar valores directamente en los programas que escribimos. Por ejemplo, podemos especificar un número como **literal** simplemente (literalmente) escribiéndolo directamente en el programa (por ejemplo, ``5`` o ``4.32``). En un programa, especificamos una palabra, o más generalmente una cadena de caracteres, encerrando los caracteres entre comillas (por ejemplo, ``"¡Hola, Mundo!"``).

Durante la ejecución de un programa, el intérprete de Python crea una representación interna de literales que se especifican en un programa. Luego puede manipularlos, por ejemplo, multiplicando dos números. Llamamos a las representaciones internas **objetos** o simplemente **valores**.

No se pueden ver directamente las representaciones internas de los valores. Sin embargo, puede usar la función ``print`` para ver una representación impresa en la ventana de salida.

La representación impresa de un número utiliza la representación decimal familiar (leer `Roman Numerals <http://en.wikipedia.org/wiki/Roman_numerals>`__ es un desafío divertido en los museos, pero gracias a Dios que el intérprete de Python no presenta el número 2014 como MMXIV en la ventana de resultados). Por lo tanto, la representación impresa de un número que se muestra en la ventana de salida es la misma que el literal que especifica en un programa.

Sin embargo, la representación impresa de una cadena de caracteres no es exactamente la misma que el literal utiliza para especificar la cadena en un programa. Para el literal en un programa, encierra la cadena entre comillas. La representación impresa, en la ventana de salida, omite las comillas.

.. activecode:: ac2_2_1
    :nocanvas:

    print(3.2)
    print("Hola, Mundo!")

.. note::
   Los **Literal** aparecen en los programas. El intérprete de Python convierte los literales en **valores**, que tienen representaciones internas que las personas nunca pueden ver directamente. **Outputs** son representaciones externas de valores que aparecen en la ventana de salida. Cuando tengamos cuidado, usaremos los términos de esta manera. A veces, sin embargo, nos volveremos un poco descuidados y nos referiremos a literales o representaciones externas como valores.

Los números con un punto decimal pertenecen a una clase
llamada **float**, porque estos números se representan en un formato llamado
*punto flotante*. En esta etapa, puede tratar las palabras *class* y *type*
indistintamente. Volveremos a una comprensión más profunda de lo que es una clase
está en capítulos posteriores.

Pronto encontrará también otros tipos de objetos, como listas y diccionarios. Cada uno de estos tiene su propia representación especial para especificar un objeto como literal en un programa y para mostrar un objeto cuando lo imprime. Por ejemplo, el contenido de la lista está encerrado entre corchetes ``[]``. También encontrará que algunos objetos más complicados no tienen representaciones impresas muy bonitas: imprimirlos no será muy útil.

**Revisa tu entendimiento**

.. mchoice:: question2_2_1
   :answer_a: No se imprime nada. Genera un error de tiempo de ejecución.
   :answer_b: "¡Hola Mundo!"
   :answer_c: ¡Hola Mundo!
   :correct: c
   :feedback_a: "¡Hola Mundo!" tiene una representación impresa, por lo que no habrá un error.
   :feedback_b: El literal en el programa incluye las comillas, pero la representación impresa las omite.
   :feedback_c: La representación impresa omite las comillas que se incluyen en la cadena literal.
   :practice: T

   ¿Qué aparece en la ventana de salida cuando se ejecuta la siguiente instrucción?

   .. code-block:: python

      print("¡Hola Mundo!")