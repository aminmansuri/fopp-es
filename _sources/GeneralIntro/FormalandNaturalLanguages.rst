..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: intro-6-
   :start: 1

Lenguajes formales y naturales
------------------------------

**Los idiomas naturales** son los idiomas que las personas hablan, como el Inglés,
Español, coreano, chino mandarín, etc. No fueron diseñados por personas (aunque las personas intentan
imponerles un orden); evolucionaron naturalmente.

**Los idiomas formales** son idiomas diseñados por personas para
aplicaciones. Por ejemplo, la notación que usan los matemáticos es lenguaje
formal que es particularmente bueno para denotar relaciones entre números y
símbolos. Los químicos usan un lenguaje formal para representar la estructura química de
moléculas. Y más importante:

    *Los lenguajes de programación son lenguajes formales diseñados para
    cálculos expresos.*

Los lenguajes formales tienden a tener reglas estrictas sobre la sintaxis. Por ejemplo, ``3+3=6``
es una afirmación matemática sintácticamente correcta, pero ``3=+6$`` no lo es.
H\ :sub:`2`\ O es un nombre químico sintácticamente correcto, pero :sub:`2`\ Zz
no.

Las reglas de sintaxis vienen en dos sabores, pertenecientes a **tokens** y estructura.
Los tokens son los elementos básicos del lenguaje, como palabras, números y
elementos químicos. Uno de los problemas con ``3=+6$`` es que ``$`` no es un
ficha legal en matemáticas (al menos hasta donde sabemos). Similar,
:sub:`2`\ Zz no es legal porque no hay ningún elemento con la abreviatura
``Zz``.

El segundo tipo de regla de sintaxis se refiere a la **estructura** de una declaración ---
es decir, la forma en que se organizan los tokens. La declaración ``3=+6$`` es
estructuralmente ilegal porque no puede colocar un signo más inmediatamente después de un
signo igual. Del mismo modo, las fórmulas moleculares deben tener subíndices después del
nombre del elemento, no antes.

Cuando lee una oración en inglés o una declaración en un idioma formal, usted
tiene que averiguar cuál es la estructura de la oración (aunque forma en lenguaje
natural es que haces esto inconscientemente). Este proceso se llama **análisis**.

Por ejemplo, cuando escucha la oración "Se cayó el otro zapato", entiende
que el otro zapato es el sujeto y cayó el verbo. Una vez que haya analizado
una oración, puede descubrir lo que significa, o la **semántica** de la oración.
Asumiendo que sabe lo que es un zapato y lo que significa caerse, podrá
comprender la implicación general de esta oración.

Aunque los lenguajes formales y naturales tienen muchas características en común: tokens,
estructura, sintaxis y semántica --- hay muchas diferencias:

.. glossary::

    ambigüedad
        Los lenguajes naturales están llenos de ambigüedad, que las personas tratan
        utilizando pistas contextuales y otra información. Los idiomas formales son
        diseñados para ser casi o completamente inequívoco, lo que significa que cualquier
        declaración tiene exactamente un significado, independientemente del contexto.

    redundancia
        Para compensar la ambigüedad y reducir los malentendidos,
        los idiomas naturales emplean mucha redundancia. Como resultado, a menudo son
        verbosos. Los lenguajes formales son menos redundantes y más concisos.

    literalidad
        Los idiomas formales significan exactamente lo que dicen. Por otra parte,
        los lenguajes naturales están llenos de modismos y metáforas. Si alguien dice: "El
        otro zapato cayó", probablemente no hay zapato y nada cae.

        .. tip::

            Necesitará encontrar el chiste original para entender el significado
            idiomático del otro zapato cayendo. *Yahoo! Respuestas* lo
            sabe!

Las personas que crecen hablando un idioma natural, es decir, todos, a menudo tienen dificultades
en el tiempo de adaptación a los idiomas formales. De alguna manera, la diferencia entre natural y formal
en el lenguaje es como la diferencia entre poesía y prosa, pero más complicado,
así que:

.. glossary::

    poesía
        Las palabras se usan para sus sonidos, así como para su significado, y
        todo el poema junto crea un efecto o respuesta emocional. La Ambigüedad
        no solo es común sino a menudo deliberado.

    prosa
        El significado literal de las palabras es más importante, y la estructura
        aporta más significado. La prosa es más susceptible al análisis que la
        poesía pero aún a menudo ambigua.

    programa
        El significado de un programa de computadora es inequívoco y literal, y puede
        entenderse completamente por el análisis de los tokens y la estructura.

Aquí hay algunas sugerencias para leer programas (y otros idiomas formales).
Primero, recuerde que los idiomas formales son mucho más densos que los idiomas
naturales, por lo que lleva más tiempo leerlos. Además, la estructura es muy
importante, por lo que generalmente no es una buena idea leer de arriba a abajo, de izquierda a
derecha. En cambio, aprenda a analizar el programa en su cabeza, identificando los tokens
e interpretando la estructura. Finalmente, los detalles importan. Cosas Pequeñas
como errores de ortografía y mala puntuación pueden salirse con la suya en
nos lenguajes naturales pero pueden marcar una gran diferencia en un lenguaje formal.

**Revisa tu entendimiento**

.. mchoice:: question1_6_1
    :answer_a: Los lenguajes naturales se pueden analizar mientras que los lenguajes formales no.
    :answer_b: Ambigüedad, redundancia y literalidad.
    :answer_c: No hay diferencias entre los lenguajes naturales y formales.
    :answer_d: Tokens, estructura, sintaxis y semántica.
    :correct: b
    :feedback_a: En realidad, ambos lenguajes se pueden analizar (determinando la estructura de la oración), pero los lenguajes formales se pueden analizar más fácilmente en el software.
    :feedback_b: Todos estos pueden estar presentes en lenguajes naturales, pero no pueden existir en lenguajes formales.
    :feedback_c: Hay varias diferencias entre los dos, pero también son similares.
    :feedback_d: Estas son las similitudes entre los dos.

    Las diferencias entre los idiomas naturales y formales incluyen:

.. mchoice:: question1_6_2
    :answer_a: Verdadero
    :answer_b: Falso
    :correct: b
    :feedback_a: Por lo general, lleva más tiempo leer un programa porque la estructura es tan importante como el contenido y debe interpretarse en partes más pequeñas para su comprensión.
    :feedback_b: Por lo general, lleva más tiempo leer un programa porque la estructura es tan importante como el contenido y debe interpretarse en partes más pequeñas para su comprensión.

    Verdadero o falso: leer un programa es como leer otros tipos de texto.