..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: func-14-
   :start: 1

Glosario
--------

.. glossary::

    argumento
        Un valor proporcionado a una función cuando se llama a la función. Este valor
        se asigna al parámetro correspondiente en la función. El argumento
        puede ser el resultado de una expresión que puede involucrar operadores,
        operandos y llamadas a otras funciones fructíferas.

    cuerpo
        La segunda parte de una declaración compuesta. El cuerpo consiste en un
        secuencia de declaraciones todas sangradas la misma cantidad desde el principio
        del encabezado. La cantidad estándar de sangría utilizada dentro de
        lacomunidad de Python es de 4 espacios.

    pila de llamadas
        Una secuencia (pila) de cuadros, que muestra todas las llamadas a funciones que están en proceso
        pero aún no está completo. Cuando el código de una función invoca otra llamada de función,
        habrá más de un cuadro en la pila.

    declaración compuesta
        Una declaración que consta de dos partes:

        #. encabezado: que comienza con una palabra clave que determina la declaración
           tipo, y termina con dos puntos.
        #. cuerpo: contiene una o más declaraciones sangradas por la misma cantidad
           del encabezado

        La sintaxis de una declaración compuesta se ve así:

        .. code-block:: python

            keyword expression:
                statement
                statement 
                ...

    docstring
        Si lo primero en un cuerpo de función es un string (o, como veremos más adelante, en otras situaciones
        también) que se adjunta a la función como su atributo ``__doc__``.

    flujo de ejecución
        El orden en que se ejecutan las declaraciones durante la ejecución de un programa.

    función
        Una secuencia con nombre de declaraciones que realiza alguna operación útil.
        Las funciones pueden o no tomar parámetros y pueden o no producir un
        resultado.

    Llamada de función
        Una declaración que ejecuta una función. Consiste en el nombre de la
        función seguida de una lista de argumentos entre paréntesis.

    composición de funciones
        Usando la salida de una llamada de función como entrada a otra.

    definición de función
        Una declaración que crea una nueva función, especificando su nombre,
        parámetros y las declaraciones que ejecuta.

    función fructífera
        Una función que devuelve un valor cuando se llama.

    variable global
        Una variable definida en el nivel superior, no dentro de ninguna función.

    línea de cabecera
        La primera parte de una declaración compuesta. Una línea de encabezado comienza con una palabra clave y
        termina con dos puntos (:)

    lifetime
        Las variables y los objetos lifetimes --- se crean en algún momento durante la
        ejecución del programa, y será destruido en algún momento. En python,  los objetos
        viven mientras haya alguna variable apuntando a ella, o es parte de algún
        otro objeto compuesto, como una lista o un diccionario. En python, variables locales
        viven solo hasta que la función finalice la ejecución.

    variable local
        Una variable definida dentro de una función. Una variable local solo puede usarse
        dentro de su función. Los parámetros de una función también son especiales.
        de variable local.

    método
        Un tipo especial de función que se invoca en objetos de tipos particulares de
        objetos, utilizando la sintaxis ``<expr>.<nombre del método> (<valores de parámetros adicionales>)``

    None
        Un valor especial de Python. Un uso en Python es que se devuelve
        por funciones que no ejecutan una declaración de retorno con un argumento de retorno.

    parámetro
        Un nombre usado dentro de una función para referirse al valor que se pasó
        a eso como argumento.

    valor de retorno
        El valor proporcionado como resultado de una llamada de función.

    efecto secundario
        Algún efecto duradero de una llamada a función, que no sea su valor de retorno. Los efectos secundarios incluyen declaraciones de impresión, cambios en objetos mutables y cambios en los valores de las variables globales.

    marco de pila
        Un marco que realiza un seguimiento de los valores de las variables locales durante la ejecución de una función,
        y dónde devolver el control cuando se completa la ejecución de la función.
   