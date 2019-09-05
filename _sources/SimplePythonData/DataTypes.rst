..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-5-
   :start: 1

.. index:: type converter functions, int, float, str, truncation

Tipos de datos
-----------------
Si no está seguro de en qué clase (tipo de dato) cae un valor, Python tiene una función llamada
**type** que puede decirte.

.. activecode:: ac2_5_1
    :nocanvas:

    print(type("¡Hola Mundo!"))
    print(type(17))
    print("Hola, Mundo")
    print(type(3.2))


¿Qué pasa con valores como ``"17"`` y ``"3.2"``? Parecen números, pero
están entre comillas como cadenas.

.. activecode:: ac2_5_2
    :nocanvas:

    print(type("17"))
    print(type("3.2"))

¡Son cadenas  de caracteres (Srings)!

Las cadenas en Python se pueden incluir entre comillas simples (``'``) o dobles
comillas (``"``), o tres de cada (``'''`` o ``"""``)

.. activecode:: ac2_5_3
    :nocanvas:

    print(type('Esta es una cadena.'))
    print(type("Y así es esto."))
    print(type("""y esto."""))
    print(type('''e incluso esto...'''))


Las cadenas con comillas dobles pueden contener comillas simples dentro de ellas, como en ``"Bruce's beard"``,
y las cadenas entre comillas simples pueden tener comillas dobles dentro de ellas, como en
``'Los caballeros que dicen "¡Ni!"'``.
Las cadenas encerradas con tres ocurrencias de cualquier símbolo de comilla se llaman
cuerdas triples citadas. Pueden contener comillas simples o dobles:

.. activecode:: ac2_5_4
    :nocanvas:

    print('''"Oh no", exclamó, "¡La bicicleta de Ben está rota!"''')


Las cadenas entre comillas triples pueden incluso abarcar varias líneas:

.. activecode:: ac2_5_5
    :nocanvas:

    print("""Este mensaje tendrá
    varias líneas
    de texto.""")

A Python no le importa si usa comillas simples o dobles o
citas únicas para rodear tus cadenas. Una vez que ha analizado el texto de
su programa o comando, la forma en que almacena el valor es idéntica en todos los casos,
y las comillas circundantes no son parte del valor.

.. activecode:: ac2_5_6
    :nocanvas:

    print('Esto es una string.')
    print("""Y así es esto.""")

Entonces, los diseñadores de lenguaje Python generalmente eligen rodear sus cadenas
con comillas simples. ¿Qué crees que pasaría si la cadena ya contuviera
comillas simples?

Cuando escribe un número entero grande, puede sentirse tentado a usar comas entre
grupos de tres dígitos, como en ``42,000``. Este no es un entero legal en
Python, pero significa algo más, que es legal:

.. activecode:: ac2_5_7
    :nocanvas:

    print(42500)
    print(42,500)


¡Bueno, eso no es lo que esperábamos! Debido a la coma, Python eligió
trata esto como un *par* de valores. De hecho, una declaración de impresión puede imprimir cualquier cantidad de valores siempre
a medida que los separas por comas. Observe que los valores están separados por espacios cuando se muestran.

.. activecode:: ac2_5_8
    :nocanvas:

    print(42, 17, 56, 34, 11, 4.35, 32)
    print(3.4, "Hola", 45)

Recuerde no poner comas o espacios en sus enteros, no
importa cuán grandes sean. También revise lo que dijimos en el capítulo anterior:
los lenguajes formales son estrictos, la notación es concisa e incluso el más pequeño
cambio puede significar algo muy diferente de lo que pretendía.

.. note::
   Los ejemplos en este texto describen cómo funciona la impresión en Python 3. Si instala Python 2.7 en su máquina, funcionará de manera ligeramente diferente. Una diferencia es que imprimir no se llama como una función, por lo que no hay paréntesis alrededor de los valores que se imprimirán.

**Revisa tu entendimiento**

.. mchoice:: question2_5_1
   :answer_a: Imprimiendo el valor y determinando el tipo de datos en función del valor impreso.
   :answer_b: Usando la función type.
   :answer_c: Usandolo en una ecuación conocida e imprimiendo el resultado.
   :answer_d: Mirando la declaración de la variable.
   :correct: b
   :feedback_a: Es posible que pueda determinar el tipo de datos en función del valor impreso, pero también puede ser engañoso, como cuando se imprime una cadena, no hay comillas a su alrededor.
   :feedback_b: La función type le dirá a la clase a la que pertenece el valor.
   :feedback_c: Solo se pueden usar valores numéricos en las ecuaciones.
   :feedback_d: En Python las variables no se declaran. Los valores, no las variables, tienen tipos en Python. Una variable puede incluso tomar valores con diferentes tipos durante la ejecución de un programa.
   :practice: T

   ¿Cómo puedes determinar el tipo de una variable?

.. mchoice:: question2_5_2
   :answer_a: Character
   :answer_b: Integer
   :answer_c: Float
   :answer_d: String
   :correct: d
   :feedback_a: No es un solo character
   :feedback_b: El valor no es numérico.
   :feedback_c: El valor no es numérico con un punto decimal.
   :feedback_d: String se puede encerrar entre comillas simples.
   :practice: T

   ¿Cuál es el tipo de datos de 'qué tipo de datos son estos'?
