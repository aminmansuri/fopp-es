..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: moreiter-11-
   :start: 1

👩‍💻 Bucles infinitos
----------------------

Aunque el libro de texto tiene un límite de tiempo que impide que se ejecute una ventana de código activa
indefinidamente, aún tendrá que esperar un poco si su programa tiene un bucle infinito. Si
accidentalmente crea uno fuera del libro de texto, no tendrá la misma protección.

Entonces, ¿cómo puedes reconocer cuando estás en peligro de hacer un bucle infinito?

En primer lugar, si la variable que está utilizando para determinar si el ciclo while debe continuar
nunca se reasigna dentro del ciclo while, entonces su código tendrá un ciclo infinito. (A menos que, por supuesto, use ``break`` para
salir del bucle.)

Además, si la condición while es ``while True:`` y no hay interrupción, ¡ese es otro caso de un bucle infinito!

.. sourcecode:: python

    while True:
        print("¿Esto se detendrá?")

    print("Hemos escapado.")

Otro caso en el que es probable que ocurra un bucle infinito es cuando ha reasignado el valor de la variable utilizada en la instrucción while de una manera que impide que el bucle se complete. Este es un ejemplo a continuación (si toma demasiado tiempo, intente volver a cargar la página y siga este ejemplo en codelens):

.. activecode:: ac14_11_1

    b = 15

    while b < 60:
        b = 5
        print("Bugs")
        b = b + 7

Observe cómo, en este caso, b se establece inicialmente en 15 fuera del bucle while y luego se reasigna
el valor de 5 en el interior, en la línea 4. Para cuando se haya agregado 7 a b en la línea 6, entonces tenemos que
verificar si b es menor que 60. Debido a que no es así, nuevamente ejecutamos la línea 4 y establecemos el valor de b en 5
otra vez. No hay forma de salir de este bucle.

A veces, los programas pueden tardar un tiempo en ejecutarse, entonces, ¿cómo puede determinar si su código solo habla un rato o si está atascado dentro de un bucle infinito?. Las declaraciones impresas son para las personas, ¡así que aprovéchalas!. Puede agregar declaraciones de impresión para realizar un seguimiento de cómo están cambiando sus variables a medida que el programa procesa las instrucciones que se les dan. A continuación se muestra un ejemplo de un bucle infinito. Intente agregar declaraciones impresas para ver de dónde viene. Cuando haya terminado, consulte la respuesta para ver cuál fue nuestra solución.

#.

   .. tabbed:: q1

        .. tab:: Question

            .. actex:: ac14_11_2

                d = {'x': []}

                while len(d.keys()) <= 2:
                    print('Diccionarios')
                    d['x'].append('d')


        .. tab:: Answer

            .. actex:: ac14_11_3

                d = {'x': []}
                print("comenzando el ciclo while")
                while len(d.keys()) <= 2:
                    print("número de claves en d:", len(d.keys()))
                    print('Diccionarios')
                    d['x'].append('d')
                    print("número de claves en d después de agregar:", len(d.keys()))
                print("final del ciclo while")
