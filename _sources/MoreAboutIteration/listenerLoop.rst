..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: moreiter-3-
   :start: 1

.. index::
    single: sentinel value
    single: value; sentinel
    single: validation
    single: input; validating

El Bucle Listener
==================

Al final de la sección anterior, recomendamos utilizar un bucle for siempre que se conozca el comienzo del
proceso de iteración, cuántas veces se debe ejecutar el bloque de código. Por lo general, en Python, usará un bucle for
en lugar de un bucle while. ¿Cuándo *no* se conoce al comienzo de la iteración ni cuántas veces necesita el bloque de código
ser ejecutado? La respuesta es, cuando depende de algo que sucede durante la ejecución.

Un patrón muy común se llama **listener loop**. Dentro del ciclo while hay una llamada a la función para obtener la entrada del usuario.
El bucle se repite indefinidamente, hasta que se recibe una entrada particular.

.. activecode:: ac14_3_1

   theSum = 0
   x = -1
   while (x != 0):
       x = int(input("siguiente número a sumar (ingrese 0 si no hay más números): "))
       theSum = theSum + x

   print(theSum)
   
Este es solo nuestro viejo amigo, el patrón de acumulación, que agrega cada salida adicional a la suma hasta ahora, que se almacena
en una variable llamada theSum y reasignada a esa variable en cada iteración. Observe que theSum se inicializa en 0.
Observe también que tuvimos que inicializar x, nuestra variable que almacena cada entrada que el usuario escribe, antes del ciclo while.
Esto es típico con los bucles while, y los hace un poco difíciles de leer y escribir. Tuvimos que inicializarlo porque
La condición ``x != 0`` se verifica al principio, antes de que se ejecute el bloque de código. En este caso, elegimos
un valor inicial que sabíamos que haría que la condición sea verdadera, para garantizar que el bloque de código del bucle while se ejecute al
menos una vez.

Si no está seguro de cómo funciona ese código, intente agregar declaraciones de impresión dentro del ciclo while que imprima el
valores de x y theSum.

Otros usos de ``while``
------------------------------

Valores Centinela
~~~~~~~~~~~~~~~~~~~

Los bucles indefinidos son mucho más comunes en el mundo real que los bucles definidos.

* Si está vendiendo entradas para un evento, no sabe de antemano cuantos
  boletos venderás. Sigues vendiendo boletos mientras la gente venga
  a la puerta y hay espacio en el pasillo.
* Cuando la tripulación de equipaje descarga un avión, no saben de antemano cuántas
  maletas hay. Siguen descargándose mientras quedan bolsas en el
  bodega de carga. (¿Por qué *su* maleta siempre es la última? Es un problema completamente diferente).
* Cuando pasas por la línea de pago en el supermercado, los empleados no
  saben de antemano cuántos elementos hay. Siguen sonando artículos
  siempre que haya más en la cinta transportadora.

Implementemos el último de estos en Python, preguntando al usuario por los precios y
mantenemiendo un total acumulado y un recuento de artículos. Cuando se ingresa el último elemento,
el programa proporciona el total general, el número de artículos y el precio promedio.
Necesitaremos estas variables:

* ``total`` - esto comenzará en cero
* ``count`` - el número de elementos, que también comienza en cero
* ``moreItems`` - un boolean que nos dice si hay más artículos esperando; esto comienza como cierto

El pseudocódigo (código escrito mitad en inglés, mitad en Python) para el cuerpo del bucle
se parece a esto ::

    while moreItems
        preguntar precio
        agregar precio al total
        agregue uno para contar

Este pseudocódigo no tiene opción para establecer ``moreItems`` en ``False``, por lo que se ejecutará para siempre.
En una tienda de comestibles, hay una pequeña
barra de plástico que colocas después de tu último artículo para separar tus alimentos de
los de la persona detrás de ti; así es como el empleado sabe que no tiene más artículos.
No tenemos un tipo de datos de "pequeña barra de plástico" en Python, por lo que haremos la siguiente mejor opción:
usará un ``price`` de cero para significar "este es mi último artículo". En este programa
cero es un **valor centinela**, un valor utilizado para señalar el final del bucle. Aquí está el código:

.. activecode:: ac14_3_2
    :timelimit: 60000

    def checkout():
        total = 0
        count = 0
        moreItems = True
        while moreItems:
            price = float(input('Ingrese el precio del artículo (0 when done): '))
            if price != 0:
                count = count + 1
                total = total + price
                print('Subtotal: $', total)
            else:
                moreItems = False
        average = total / count
        print('Total items:', count)
        print('Total $', total)
        print('Precio promedio por artículo: $', average)

    checkout()

Todavía hay algunos problemas con este programa.

* Si ingresa un número negativo, se agregará al total y contará. Modifica el código
  para que los números negativos den un mensaje de error (pero no terminen el ciclo). Sugerencia: ``elif`` es
  tu amigo.
* Si ingresa cero la primera vez que se le solicita un precio, el ciclo finalizará y el programa
  intentará dividir por cero. Use una declaración ``if``/``else`` fuera del ciclo para evitar
  división por cero y decirle al usuario que no puede calcular un promedio sin datos.
* Este programa no muestra las cantidades con dos decimales. Se te presentará eso en otro
  capítulo.

Entrada de validación
~~~~~~~~~~~~~~~~~~~~~~~~~

También puede usar un bucle ``while`` cuando desee **validar** la entrada; cuando quiera hacer esto,
asegúrese de que el usuario haya ingresado una entrada válida para una solicitud. Digamos que quiere que una función
haga una pregunta de sí o no. En este caso, desea asegurarse de que la persona que usa
su programa ingresa una S para sí o una N para no (en mayúsculas o minúsculas).
Aquí hay un programa que usa un ciclo ``while`` para seguir preguntando hasta que reciba una respuesta válida.
Como anticipo de las próximas atracciones, utiliza
el método ``upper()`` que se describe en Métodos de string para convertir un string en mayúsculas.
Cuando ejecute el siguiente código, intente escribir algo distinto de Y o N para ver cómo reacciona el código:

.. activecode:: ac14_3_3
    :timelimit: 60000

    def get_yes_or_no(message):
        valid_input = False
        while not valid_input:
            answer = input(message)
            answer = answer.upper() # convertir a mayúsculas
            if answer == 'Y' or answer == 'N':
                valid_input = True
            else:
                print('Ingrese S para sí o N para no.')
        return answer

    response = get_yes_or_no('¿Te gustan las habas? Y)es or N)o: ')
    if response == 'Y':
        print('¡Excelente! Son muy saludables')
    else:
        print('Demasiado. Si se cocinan bien, son bastante sabrosos.')
