..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-17-
   :start: 1

Glosario
---------

.. glossary::

    sentencia de asignación
        Una declaración que asigna un valor a un nombre (variable). A la izquierda de
        el operador de asignación, ``=``, es un nombre, a la derecha del
        token de asignación es una expresión que es evaluada porel intérprete de
        Python y luego asignado al nombre. Las diferencias entre
        los lados izquierdo y derecho de la declaración de asignación son a menudo
        confuso para los nuevos programadores. En la siguiente tarea:

        .. sourcecode:: python

             n = n + 1

        ``n`` juega un papel muy diferente en cada lado del ``=``. En el
        lado derecho es un *valor* y forma parte de la *expresión* que
        será evaluada por el intérprete de Python antes de asignarlo al nombre
        a la izquierda.

    símbolo de asignación
        ``=`` es el token *ficha* de asignación de Python, que no debe confundirse
        con el operador de comparación matemática usando el mismo símbolo.

    expresión booleana
        Una expresión que es verdadera o falsa.

    valor booleano
        Hay exactamente dos valores booleanos: ``Verdadero`` y ``Falso``.
        Los valores  Booleanos resultan cuando el intérprete de Python
        evalúa una expresión booleana. Tienen el tipo ``bool``.

    clase
        ver **tipo de dato** a continuación

    comentarios
        Información en un programa destinado a otros programadores (o cualquier persona
        leer el código fuente) y no tiene ningún efecto en la ejecución del
        programa.

    Tipo de dato
        Un conjunto de valores. El tipo de un valor determina cómo se puede usar en
        expresiones. Hasta ahora, los tipos que hemos visto son enteros (``int``),
        números de punto flotante (``float``) y cadenas (``str``).

    decremento
        Disminuir en 1.

    evaluar
        Para simplificar una expresión realizando las operaciones para
        rendir un solo valor.

    expresión
        Una combinación de operadores y operandos (variables y valores) que representa un
        valor de resultado único. Las expresiones se evalúan para dar ese resultado.

    float
        Un tipo de datos de Python que almacena números *de punto flotante*.
        Los números de coma flotante se almacenan internamente en dos partes: una *base* y
        un *exponente*. Cuando se imprimen en el formato estándar, se ven como
        numeros decimales. Tenga cuidado con los errores de redondeo cuando usa ``float``,
        y recuerda que son solo valores aproximados.

    incrementar
        Tanto como sustantivo como como verbo, incremento significa aumentar en 1.

    inicialización (of a variable)
        Inicializar una variable es darle un valor inicial.
        Dado que en Python las variables no existen
        hasta que se les asignen valores, se inicializan cuando son
        creados. En otros lenguajes de programación este no es el caso, y
        las variables se pueden crear sin inicializarse, en cuyo caso
        tener valores predeterminados o *basura*.

    int
        Un tipo de datos de Python que contiene números positivos y negativos **enteros**.

    división entera
        Una operación que divide un número entero por otro y produce un número entero.
        La división entera produce solo el número entero de veces que
        el numerador es divisible por el denominador y descarta cualquier resto.

    palabra clave
        Una palabra reservada que utiliza el compilador para analizar el programa; tú
        no puedes usar palabras clave como ``if``, ``def`` y ``while`` como nombres de
        variables

    literal
        Un número o cadena que se escribe directamente en un programa. A veces, estos también se conocen como valores literales, o simplemente valores, pero tenga cuidado de no confundir un valor literal como está escrito en un programa con un valor interno mantenido por el intérprete de Python durante la ejecución de un programa.
        
    operador lógico
        Uno de los operadores que combina expresiones booleanas: ``and``,
        ``or``, y ``not``.

    operador módulo
        Un operador, denotado con un signo de porcentaje (``%``), que funciona en
        enteros y produce el resto cuando un número se divide por otro.

    objeto
        También conocido como un objeto de datos (o valor de datos). Las cosas fundamentales que los programas están diseñados para
        manipular (o que los programadores pidan hacer cosas por ellos).

    operando
        Uno de los valores en los que opera un operador.

    operador
        Un símbolo especial que representa un cálculo simple como la suma,
        multiplicación o concatenación de cuerdas.

    prompt string
        Se usa durante la entrada interactiva para proporcionar al uso pistas sobre qué tipo de valor ingresar.

    diagrama de referencia
        Una imagen que muestra una variable con una flecha apuntando al valor (objeto) al que se refiere la variable. Ver también **instantánea de estado**.

    reglas de precedencia
        El conjunto de reglas que rigen el orden en que las expresiones que involucran
        Se evalúan múltiples operadores y operandos.

    instantánea del estado
        Una representación gráfica de un conjunto de variables y los valores para
        que refieren, tomadas en un instante particular durante el programaejecución.

    declaración
        Una instrucción que el intérprete de Python puede ejecutar. Hasta ahora tenemos
        solo vi la declaración de asignación, pero pronto conoceremos el
        declaración ``import`` y la declaración ``for``.

    str
        Un tipo de datos de Python que contiene una cadena de caracteres.

    función de conversión de tipo
        Una función que puede convertir un valor de datos de un tipo a otro.

    valor
        Un número o cadena (u otras cosas que se nombrarán más adelante) que pueden ser
        almacenado en una variable o calculado en una expresión.

    variable
        Un nombre que se refiere a un valor.

    nombre de variable
        Un nombre dado a una variable. Los nombres de variables en Python consisten en un
        secuencia de letras (a..z, A..Z y _) y dígitos (0..9) que comienza
        con una carta en la mejor práctica de programación, los nombres de las variables deben ser
        elegidos para que describan su uso en el programa, haciendo que el programa esté *autodocumentado*.



