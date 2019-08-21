..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: test-2-
   :start: 1

Escribir casos de prueba para funciones
=======================================

Es una buena idea escribir uno o más casos de prueba para cada función que defina.

Una función define una operación que se puede realizar. Si la función toma uno o más parámetros, se supone que debe
funcionar correctamente en una variedad de posibles entradas. Cada caso de prueba verificará si la función funciona correctamente en
**un conjunto de entradas posibles**.

Una función útil hará una combinación de tres cosas, dados sus parámetros de entrada:

* Devuelve un valor. Para estos, escribirá **pruebas de valor de retorno**.
* Modifica el contenido de algún objeto mutable, como una lista o diccionario. Para estos, escribirá **pruebas de efectos secundarios**.
* Imprime algo o escribe algo en un archivo. Las pruebas de si una función genera el resultado impreso correcto están más allá del alcance de este marco de prueba; No escribirás estas pruebas.

Pruebas de valor de retorno
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Probar si una función devuelve el valor correcto es el caso de prueba más fácil de definir. Simplemente verifica si el
resultado de invocar la función en una entrada particular produce la salida particular que espera. Si ``f`` es tu
y cree que debería transformar las entradas ``x`` e ``y`` en la salida ``z``, entonces podría escribir una prueba como
``test.testEqual(f(x, y), z)``. O, para dar un ejemplo más concreto, si tiene una función ``square``, podría tener
un caso de prueba ``test.testEqual(square(3), 9)``. Llame a esto una **prueba de valor de retorno**.

Como cada prueba verifica si una función funciona correctamente en entradas específicas, los casos de prueba nunca estarán completos: en
principio, una función podría funcionar correctamente en todas las entradas que se prueban en los casos de prueba, pero aún no funciona
correctamente en algunas otras entradas. Ahí es donde entra el arte de definir casos de prueba: intenta encontrar entradas específicas que
son representativos de todos los tipos importantes de entradas que podrían pasar a la función.

El primer caso de prueba que defina para una función debe ser un caso "fácil", prototipo de los tipos de
entradas que se supone que maneja la función. Los casos de prueba adicionales deben manejar entradas "extremas" o inusuales, a veces
llamado **casos de borde**. Por ejemplo, si está definiendo la función "square", el primer caso fácil podría ser una entrada
como 3. Las entradas extremas o inusuales adicionales alrededor de las cuales crea casos de prueba pueden ser un número negativo, 0 y un
número de coma flotante

Una forma de pensar sobre cómo generar casos extremos es pensar en términos de **clases de equivalencia** de los diferentes tipos de entradas que podría obtener la función. Por ejemplo, la entrada a la función ``square`` podría ser positiva o negativa. Luego elegimos una entrada de cada una de estas clases.
**Es importante tener al menos una prueba para cada clase de equivalencia de entradas.**

Los errores semánticos a menudo son causados por el manejo inadecuado de los límites entre las clases de equivalencia. El límite para
el problema es cero. **Es importante tener una prueba en cada límite.**

Otra forma de pensar sobre casos extremos es imaginar cosas que podrían salir mal en la implementación. Por ejemplo, en la función cuadrada podríamos usar por error la suma en lugar de la multiplicación. Por lo tanto, no deberíamos confiar en una prueba que use 2 como entrada, pero podríamos engañarnos al pensar que estaba funcionando cuando producía una salida de 4, cuando realmente se duplicaba en lugar de cuadrar.

Intente agregar uno o dos casos de prueba más para la función cuadrada en el código a continuación, según las sugerencias para los casos límite.

.. activecode:: ac19_2_1

    def square(x):
        return x*x

    import test

    test.testEqual(square(3), 9)


Pruebas de efectos secundarios
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Para probar si una función realiza los cambios correctos en un objeto mutable, necesitará más de una línea de código. Vas a
primero establezca el objeto mutable en algún valor, luego ejecute la función, luego verifique si el objeto tiene el valor esperado.
Llame a esto una **prueba de efectos secundarios** porque está verificando si la invocación de la función ha tenido el lado correcto
efecto sobre el objeto mutable.

A continuación, se muestra un ejemplo que prueba la función ``update_counts`` (que se implementa de manera deliberada de manera incorrecta ...). Esta
función toma un string llamado ``letters`` y actualiza los recuentos en ``counts_diction`` que están asociados con cada
personaje en el string. Para hacer una prueba de efectos secundarios, primero creamos un diccionario con recuentos iniciales para algunas letras.
Luego invocamos la función. Luego probamos que el diccionario tiene los recuentos correctos para algunas letras (las correctas).
Los recuentos se calculan manualmente cuando escribimos la prueba. Tenemos que saber cuál debería ser la respuesta correcta para escribir
una prueba). Puede pensarlo como escribir un pequeño examen para su código; no le daríamos un examen sin conocer el
nos responde a nosotros mismos.

.. activecode:: ac19_2_2

    def update_counts(letters, counts_d):
        for c in letters:
            counts_d[c] = 1
            if c in counts_d:
                counts_d[c] = counts_d[c] + 1

    import test

    counts = {'a': 3, 'b': 2}
    update_counts("aaab", counts)
    # 3 ocurrencias más de a, entonces 6 en total
    test.testEqual(counts['a'], 6)
    # 1 ocurrencia más de a, entonces 3 en total
    test.testEqual(counts['b'], 3)


Prueba de condicionales y bucles
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Si el código tiene una ejecución condicional o un bucle for, entonces querrá incluir casos de prueba que ejerzan diferentes
posibles caminos a través del código. Por ejemplo, si hay un bucle for, los casos extremos incluirían la iteración a través de una
secuencia vacía o una secuencia con solo un elemento. Con un condicional, desearía diferentes entradas que causen el if y else
cláusulas para ejecutar.

Si estaba escribiendo pruebas en una función que toma cualquier lista como entrada y devuelve un valor que es un cálculo en ese
lista de entrada, puede probar el valor de retorno de la función cuando se invoca en una lista vacía, una lista con un solo valor, un
lista con un elemento que es una lista en sí, una lista que tiene muchos elementos ...

Intente agregar algunas de esas pruebas en la ventana de código anterior, para la función update_counts. ¿Qué pasa si comienzas con un
diccionario de recuentos vacíos? ¿Qué pasa si la cadena pasada a update_counts está vacía? ¿Qué pasa si la cadena incluye letras que
¿Todavía no estás en el diccionario?

Prueba de parámetros opcionales
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Si una función toma un parámetro opcional, uno de los casos límite para probar es cuando no se proporciona ningún valor de parámetro
durante la ejecución. A continuación se presentan algunas pruebas para la función ordenada incorporada.

.. activecode:: ac19_2_3

    import test

    test.testEqual(sorted([1, 7, 4]), [1, 4, 7])
    test.testEqual(sorted([1, 7, 4], reverse=True), [7, 4, 1])


.. mchoice:: question19_2_1
   :answer_a: True
   :answer_b: False
   :correct: b
   :feedback_a: No importa cuántas pruebas escriba, puede haber alguna entrada que no haya probado, y la función podría hacer lo incorrecto en esa entrada.
   :feedback_b: Las pruebas deben cubrir tantos casos extremos como se te ocurran, pero siempre existe la posibilidad de que la función funcione mal en alguna entrada que no incluiste como caso de prueba.

   Si escribe un conjunto completo de pruebas y una función pasa todas las pruebas, puede estar seguro de que funciona correctamente.
