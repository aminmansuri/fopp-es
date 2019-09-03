..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: intro-4-
   :start: 1

Formas especiales de ejecutar Python en este libro
--------------------------------------------------------

Este libro proporciona dos formas adicionales de ejecutar programas Python. Ambas técnicas están diseñadas para ayudarlo mientras usted
aprende el lenguaje de programación. Le ayudarán a comprender mejor cómo funcionan los programas Python.


Primero, puede escribir, modificar y ejecutar programas utilizando un exclusivo intérprete **activecode** que le permite ejecutar código Python correctamente
en el texto mismo (directamente desde el navegador web). Aunque esta no es la forma en que se escriben los programas reales, proporciona un excelente
entorno para aprender un lenguaje de programación como Python ya que puedes experimentar con el lenguaje mientras lees.

Eche un vistazo al intérprete de activecode en acción. Intente presionar el botón *Save and run* a continuación. (Si no está conectado
solo dirá *Run*.)

.. activecode:: ac1_4_1

    print("Mi primer programa agrega dos números, 2 y 3:")
    print (2 + 3)

Ahora intente modificar el programa que se muestra arriba. Primero, modifique la cadena en la
primera declaración de impresión cambiando la palabra *agrega* a la palabra *multiplica*. Ahora presiona
*Run* nuevamente. Puede ver que el resultado del programa ha cambiado. Sin embargo, todavía imprime
"5" como respuesta. Modifique la segunda declaración de impresión cambiando el símbolo de suma, el
``+``, al símbolo de multiplicación, ``*``. Presione *Run* nuevamente para ver los nuevos resultados.

Como su nombre indica, *Save and Run* también *guarda* su última versión del código,
y puede recuperarlo incluso en sesiones posteriores cuando *inició sesión*. Si *no* inició sesión,
*Run* guarda versiones *solo hasta que su navegador abandone la página web actual*,
y luego pierde todas las modificaciones.

Si ha iniciado sesión, cuando se carga una página por primera vez, cada ventana de activecode tendrá un botón *Load History*,
a la derecha del botón *Save and Run*.
Si hace clic en él o si ejecuta algún código, ese botón se convierte en un control deslizante.
Si hace clic en el cuadro de ubicación del control deslizante, puede usar su flecha izquierda y derecha
para cambiar a otras versiones que ejecutó.
Alternativamente, puede arrastrar el cuadro en el control deslizante.
Ahora mueva el control deslizante para ver una versión previamente guardada de su código. Puede editar o ejecutar cualquier versión.

Además del activecode, también puede ejecutar código Python con la ayuda de una única
herramienta de visualización. Esta herramienta, conocida como **codelens**, le permite controlar el paso por
paso de la ejecución de un programa. También le permite ver los valores de todas las variables tal como están
creadas y modificadas. En activecode, el código fuente se ejecuta de principio a fin y usted
puede ver el resultado final. En codelens puede ver y controlar el progreso paso a paso.
Tenga en cuenta que la flecha roja siempre apunta a la siguiente línea de código que se va a ejecutar.
La flecha verde clara apunta a la línea que se acaba de ejecutar. Haga clic en "Show in
Codelens" para que aparezca la ventana de codelens, y luego haga clic en el botón Resend
unas pocas veces para pasar por la ejecución.

A veces, presentaremos ejemplos de código explícitamente en una ventana de codelens en el libro de texto, como se muestra a continuación.
Cuando lo hagamos, piense en ello como un estímulo para usar las funciones de codelens para avanzar la
ejecución del programa.

.. codelens:: clens1_4_1
    :python: py3
    :showoutput:

    print("Mi primer programa agrega dos números, 2 y 3:")
    print(2 + 3)


**Revisa tu entendimiento**

.. mchoice:: question1_4_1
    :multiple_answers:
    :answer_a: Guardar programas y volver a cargar programas guardados.
    :answer_b: Escriba el código fuente de Python.
    :answer_c: Ejecuta el código Python directamente en el texto dentro del navegador web.
    :answer_d: Recibe una respuesta sí / no sobre si tu código es correcto o no.
    :correct: a,b,c
    :feedback_a: Puede (y debe) guardar el contenido de la ventana de código activo.
    :feedback_b: No está limitado a ejecutar los ejemplos que ya están allí. Intenta agregarles y crear el tuyo propio.
    :feedback_c: El intérprete de código activo le permitirá escribir código Python en el cuadro de texto y luego podrá verlo ejecutar mientras el intérprete interpreta y ejecuta el código fuente.
    :feedback_d: Aunque puede (y debe) verificar que su código sea correcto al examinar su salida, activecode no le dirá directamente si ha implementado correctamente su programa.

    El intérprete de código activo le permite (seleccionar todo lo que corresponda):

.. mchoice:: question1_4_2
    :multiple_answers:
    :answer_a: Mide la velocidad de ejecución de un programa.
    :answer_b: Controla la ejecución paso a paso de un programa.
    :answer_c: Escribe y ejecuta tu propio código Python.
    :answer_d: Ejecuta el código Python que está en codelens.
    :correct: b,d
    :feedback_a: De hecho, los pasos de codelens a través de cada línea uno por uno a medida que haces clic, que es MUCHO más lento que el intérprete de Python.
    :feedback_b: Al usar codelens, puede controlar la ejecución de un programa paso a paso. ¡Incluso puede ir hacia atrás!
    :feedback_c: Codelens funciona solo para los ejemplos preprogramados.
    :feedback_d: Al avanzar por el código de Python en codelens, está ejecutando el programa Python.

    Codelens le permite (seleccionar todas las opciones que correspondan):

.. index:: programa, algoritmo

