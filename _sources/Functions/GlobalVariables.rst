..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: func-8-
   :start: 1

Variables Globales
-------------------

Los nombres de variables que están en el *nivel superior*, no dentro de ninguna definición de función,
se llaman globales.

Es legal que una función acceda a una variable global. Sin embargo, esto se considera
**mala forma** por casi todos los programadores y debe evitarse. Esta subsección
incluye algunos ejemplos que ilustran las posibles interacciones de global y
variables locales. Esto te ayudará a entender exactamente cómo funciona Python. Ojalá,
también te convencerán de que las cosas pueden volverse bastante confusas cuando mezclas
variables locales y globales, y que realmente no deberías hacerlo.

Mire la siguiente variación sin sentido de la función square.

.. activecode:: ac11_8_1

    def badsquare(x):
        y = x ** power
        return y

    power = 2
    result = badsquare(10)
    print(result)

Aunque la función ``badsquare`` funciona, es tonta y está mal escrita. Lo hemos hecho aquí para ilustrar
una regla importante sobre cómo se buscan las variables en Python.
Primero, Python analiza las variables que se definen como variables locales en
la función. Llamamos a esto el **alcance local**. Si el nombre de la variable no es
encontrado en el ámbito local, luego Python mira las variables globales,
o **alcance global**. Este es exactamente el caso ilustrado en el código anterior.
``power`` no se encuentra localmente en ``badsquare`` pero existe a nivel mundial.
La forma apropiada de escribir esta función sería pasar la potencia como parámetro.
Para practicar, debe reescribir el ejemplo de badsquare para tener un segundo parámetro llamado potencia.

Hay otra variación sobre este tema de variables locales versus globales. Las declaraciones de asignación en la función local no pueden
cambiar variables definidas fuera de la función. Considera lo siguiente
codelens example:

.. codelens::  clens11_8_1
    :python: py3

    def powerof(x,p):
        power = p   # Otro error tonto
        y = x ** power
        return y

    power = 3
    result = powerof(10,2)
    print(result)

Ahora revisa el código. ¿Qué notas sobre los valores de la variable ``power``?
en el ámbito local en comparación con la variable ``power`` en el ámbito global?

El valor de ``power`` en el ámbito local era diferente del ámbito global.
Esto se debe a que en este ejemplo se usó ``power`` en el lado izquierdo del
declaración de asignación ``power = p``. Cuando se usa un nombre de variable en
lado izquierdo de una declaración de asignación Python crea una variable local.
Cuando una variable local tiene el mismo nombre que una variable global, decimos que
sombras locales lo global. Una **sombra** significa que la variable global no puede
Python acceder a ella porque la variable local se encontrará primero. Esto es
otra buena razón para no utilizar variables globales. Como puedes ver,
hace que su código sea confuso y difícil de entender.

Si realmente desea cambiar el valor de una variable global dentro de una función,
puede hacerlo declarando explícitamente que la variable es global, como en el ejemplo
abajo. Una vez más, debe *no* hacer esto en su código. El ejemplo es solo aquí
para consolidar su comprensión de cómo funciona Python.

.. codelens::  clens11_8_2
    :python: py3

    def powerof(x,p):
        global power  # una realidad...
        power = p     # ...mala idea, pero código válido
        y = x ** power
        return y

    power = 3
    result = powerof(10,2)
    print(result)
    print(power)

Para consolidar todas estas ideas aún más, veamos un ejemplo final.
Dentro de la función ``square`` vamos a hacer una asignación a el
parámetro ``x`` .No hay una buena razón para hacer esto aparte de enfatizar
el hecho de que el parámetro ``x`` es una variable local. Si entras en
el ejemplo en codelens verá que aunque ``x`` es 0 en la variable
local para ``square``, la ``x`` en el alcance global sigue siendo 2. Esto es confuso
a muchos programadores principiantes que piensan que una asignación a un
parámetro formal causará un cambio en el valor de la variable que fue
usado como el parámetro real, especialmente cuando los dos comparten el mismo nombre.
Pero este ejemplo demuestra que claramente no es así como funciona Python.

.. codelens:: clens11_8_3
    :python: py3

    def square(x):
        y = x * x
        x = 0       # asignar un nuevo valor al parámetro x
        return y

    x = 2
    z = square(x)
    print(z)

**Revisa tu entendimiento**

.. mchoice:: question11_8_1
   :answer_a: Es valor
   :answer_b: El rango de declaraciones en el código donde se puede acceder a una variable.
   :answer_c: Su nombre
   :correct: b
   :feedback_a: El valor es el contenido de la variable. El alcance se refiere a dónde se conoce la variable.
   :feedback_b: Correcto.
   :feedback_c: El nombre de una variable es solo un identificador o alias. El alcance se refiere a dónde se conoce la variable.

   ¿Cuál es el alcance de una variable?

.. mchoice:: question11_8_2
   :answer_a: Una variable temporal que solo se usa dentro de una función
   :answer_b: Lo mismo que un parámetro
   :answer_c: Otro nombre para cualquier variable
   :correct: a
   :feedback_a: Sí, una variable local es una variable temporal que solo se conoce (solo existe) en la función en la que se define.
   :feedback_b: Si bien los parámetros pueden considerarse variables locales, las funciones también pueden definir y usar variables locales adicionales.
   :feedback_c: Las variables que se usan fuera de una función no son locales, sino más bien variables globales.

   ¿Qué es una variable local?

.. mchoice:: question11_8_3
   :answer_a: Sí, y no hay razón para no hacerlo.
   :answer_b: Sí, pero se considera mala forma.
   :answer_c: No, causará un error.
   :correct: b
   :feedback_a: Si bien no hay ningún problema en lo que respecta a Python, generalmente se considera un mal estilo debido a la posibilidad de que el programador se confunda.
   :feedback_b: generalmente se considera un mal estilo debido a la posibilidad de que el programador se confunda. Si debe utilizar variables globales (también generalmente de forma incorrecta) asegúrese de que tengan nombres únicos.
   :feedback_c: Python gestiona el alcance global y local por separado y tiene reglas claras sobre cómo manejar variables con el mismo nombre en diferentes ámbitos, por lo que esto no causará un error de Python.

   ¿Se puede usar el mismo nombre para una variable local como una variable global?

.. note:: WP: Alcance

    En este punto, es posible que se pregunte cuándo debe convertir un objeto en una variable local y cuándo debe convertirlo en una variable global. En general, no recomendamos hacer variables globales. Imagine que está tratando de escribir un programa que haga un seguimiento del dinero mientras compra comestibles. Puede hacer una variable que represente cuánto dinero tiene la persona, llamada ``wallet``, también desea realizar una función llamada ``purchase``, que tomará el nombre del artículo y su precio, y luego agregará el artículo a una lista de comestibles y deducirá el precio del monto almacenado en la ``wallet``. Si inicializa la billetera antes de la función como una variable dentro del alcance global en lugar de pasarla como un tercer parámetro para ``purchase``, se producirá un error porque la billetera no se encontrará en el alcance local. Aunque hay formas de evitar esto, como se describe en esta página, si se suponía que su programa manejaría alimentos para varias personas, entonces necesitaría declarar cada billetera como una variable global en las funciones que desean usar la billetera, y eso se volvería muy confuso y tedioso de tratar.
