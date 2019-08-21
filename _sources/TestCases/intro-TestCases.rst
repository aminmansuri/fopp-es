..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: test-1-
   :start: 1

.. _test_cases_chap:

Introducción: casos de prueba
=============================

Un **caso de prueba** expresa los requisitos para un programa, de una manera que puede verificarse automáticamente. Específicamente, una prueba
afirma algo sobre el estado del programa en un punto particular de su ejecución.

Anteriormente hemos sugerido que es una buena idea escribir primero los comentarios sobre lo que se supone que debe hacer su código,
antes de escribir el código. Es una idea aún mejor escribir algunos casos de prueba antes de escribir un programa, por
ejemplo, antes de escribir una función, escriba algunos casos de prueba que verifiquen que devuelva un objeto del tipo correcto y
que devuelve los valores correctos cuando se invoca en entradas particulares.

Hay varias razones por las cuales es un buen hábito escribir casos de prueba.

* Antes de escribir el código, tenemos en mente lo que *debería* hacer, pero esos pensamientos pueden ser un poco vagos. Escribir casos de prueba nos obliga a ser más concretos sobre lo que debería suceder.
* Mientras escribimos el código, los casos de prueba pueden proporcionar comentarios automáticos. De hecho, usted se ha beneficiado de tales comentarios automáticos a través de casos de prueba a lo largo de este libro en algunas de las ventanas de código activo y en casi todos los ejercicios. Escribimos el código para esos casos de prueba, pero lo mantuvimos oculto para no confundirlo y también para evitar dar las respuestas. Puede obtener algunos de los mismos beneficios escribiendo sus propios casos de prueba.
* En proyectos de software más grandes, el conjunto de casos de prueba, llamados pruebas unitarias, se puede ejecutar cada vez que se realiza un cambio en la base del código. Esto puede ayudar a identificar situaciones en las que un cambio de código en un lugar interrumpe el funcionamiento correcto de otro código. No veremos esa ventaja de los casos de prueba en este libro de texto, pero tenga en cuenta que esta introducción a los casos de prueba está preparando el escenario para una práctica esencial de ingeniería de software si participa en un proyecto de desarrollo de software más grande.

Ahora es el momento de aprender a escribir código para casos de prueba, o **pruebas unitarias**. Para escribir uno, debemos saber qué *esperamos*, que algún valor tenga en un punto particular de la ejecución del programa. Por ejemplo, necesitamos especificar cuál sería el resultado correcto al llamar a la función con una entrada específica.

.. activecode:: ac19_1_1

    def square(x):
        '''elevar x a la segunda potencia'''
        return x * x
    
    import test
    print('prueba de función square')
    test.testEqual(square(10), 100)


``testEqual`` (del módulo ``test``) es una función que nos permite realizar una prueba unitaria. Se necesitan dos parámetros. En el ejemplo anterior, el primero es una llamada a la función que queremos probar (``square`` en este ejemplo) con una entrada particular (10 en este ejemplo). El segundo es el resultado correcto que debe producirse (100 en este ejemplo). ``test.testEqual`` compara los dos valores y muestra un mensaje sobre si la prueba de la unidad pasa o no: pasa si los dos valores son iguales, falla si no.

.. admonition:: Extiende el programa ...

   En la línea 8, escriba otra prueba unitaria (que debería pasar) para la función ``square``.

.. note::
   El módulo ``test`` no es un módulo estándar de Python. En cambio, hay otros módulos más potentes y más modernos, como uno llamado ``unittest`` que se enseñará en cursos más avanzados. Sin embargo, el módulo ``test`` ofrece una introducción simple a las pruebas que es apropiada en esta etapa del texto interactivo.

**Revisa tu Entendimiento**

.. mchoice:: question19_1_1
   :answer_a: True
   :answer_b: False
   :answer_c: Depende
   :correct: b
   :feedback_a: Se imprime un mensaje, pero el programa no deja de ejecutarse
   :feedback_b: Se imprime un mensaje, pero el programa no deja de ejecutarse
   :feedback_c: Se imprime un mensaje, pero el programa no deja de ejecutarse
   :practice: T

   Cuando ``test.testEqual()`` pasa dos valores que no son iguales, genera un error y detiene la ejecución del programa.
 
.. mchoice:: question19_1_2
   :answer_a: True
   :answer_b: False
   :correct: b
   :feedback_a: Es posible que no note el error, si el código solo produce una salida incorrecta en lugar de generar un error. Y puede ser difícil descubrir la causa original de un error cuando se obtiene uno.
   :feedback_b: Los casos de prueba le permiten probar algunos fragmentos de código a medida que los escribe, en lugar de esperar a que los problemas se muestren más tarde.
   :practice: T

   Los casos de prueba son una pérdida de tiempo, porque el intérprete de Python dará un error
   mensaje cuando el programa se ejecuta incorrectamente, y eso es todo lo que necesita para la depuración.

.. mchoice:: question19_1_3
    :answer_a: test.testEqual(blanked('under', 'du', 'u_d__'))
    :answer_b: test.testEqual(blanked('under', 'u_d__'), 'du')
    :answer_c: test.testEqual(blanked('under', 'du'), 'u_d__')
    :correct: c
    :feedback_a: blanked solo toma dos entradas; esto proporciona tres entradas a la función en blanco
    :feedback_b: El segundo argumento para la función blanked debería ser las letras que se han adivinado, no la versión blanked de la palabra
    :feedback_c: Comprueba si el valor devuelto por la función blanked es 'u_d__'.
    :practice: T

    Para la función blanked del juego del ahorcado, ¿cuál de las siguientes es la forma correcta de escribir una prueba para verificar que 'under' se ponga en blanco como ``'u_d__'`` cuando el usuario ha adivinado las letras d y u hasta ahora?

    .. code-block:: python

        def blanked(word, revealed_letters):
            return word

        import test

        test.testEqual(blanked('hello', 'elj'), "_ell_")
        test.testEqual(blanked('hello', ''), '_____')
        test.testEqual(blanked('ground', 'rn'), '_r__n_')
        test.testEqual(blanked('almost', 'vrnalmqpost'), 'almost')
