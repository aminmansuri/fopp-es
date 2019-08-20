..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: moreiter-5-
   :start: 1

Break y Continue
------------------

Python nos proporciona formas de controlar el flujo de iteración con dos palabras clave: break y continue.

``break`` permite que el programa salga inmediatamente del bucle, independientemente de la estructura condicional del bucle.
Esto significa que el programa saltará el resto de la iteración, sin volver a verificar la condición, y simplemente continuará
al siguiente código desactualizado que existe después del ciclo while completo.

.. image:: Figures/while_and_break.png
   :alt: imagen que muestra un rectángulo con "bloque de código" escrito en la parte superior. Luego, texto que dice "while {condition}": seguido de un bloque sangrado con "..." escrito en él. luego se escribe break y se coloca otro bloque sangrado después de la frase break, que tiene escrito "... (skipped)". Finalmente, un bloque sin sangría que pertenece al código fuera del ciclo while está en la parte inferior. Dice "code block". Una flecha apunta desde el salto de palabra al bloque no indentado en la parte inferior y se escribe la frase "break out of the loop".

.. activecode:: ac14_5_1
    
    while True:
        print("Esta frase siempre se imprimirá")
        break
        print("¿Se imprime esta frase?")

    print("Hemos terminado con el bucle while.")

Podemos ver aquí cómo no se ejecuta la declaración de impresión justo después de ``break``. De hecho, sin usar break, no tenemos
manera de detener el ciclo while porque la condición siempre se establece en True!

``continue`` es la otra palabra clave que puede controlar el flujo de iteración. El uso de ``continue`` permite al programa
inmediatamente "continuar" con la siguiente iteración. El programa omitirá el resto de la iteración, volverá a verificar la condición,
y tal vez haga otra iteración dependiendo de la condición establecida para el ciclo while.

.. image:: Figures/while_and_continue.png
   :alt: imagen que muestra un rectángulo con "bloque de código" escrito en la parte superior. Luego, texto que dice "while {condition}": seguido de un bloque sangrado con "..." escrito en él. se escribe continue y se coloca otro bloque sangrado después de la frase continue, que tiene escrito "... (omitido)". Finalmente, un bloque sin sangría que pertenece al código fuera del ciclo while está en la parte inferior. Dice "bloque de código". Los puntos de flecha de la palabra continúan hasta la instrucción condicional while en la parte superior del ciclo while. Se escribe la frase "continue at the start of the loop".

.. activecode:: ac14_5_2

    x = 0 
    while x < 10:
        print("estamos incrementando x")
        if x % 2 == 0:
            x += 3
            continue
        if x % 3 == 0:
            x += 5
        x += 1
    print("Hecho con nuestro bucle! X tiene el valor: " + str(x))

Intente recorrer el código anterior en codelens para ver el orden en que se ejecuta el código. Observe en la primer
iteración de cómo el programa no se mueve para evaluar el divisible por 3 o agregar 1 a x. En cambio, continúa con
la siguiente iteración.
