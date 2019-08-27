..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: intro-3-
   :start: 1

El lenguaje de programación Python
----------------------------------

El lenguaje de programación que aprenderás es Python. Python es un ejemplo
de un **lenguaje de alto nivel**; otros idiomas de alto nivel que quizás haya escuchado
de ellos son C ++, PHP y Java.

Como se puede deducir del nombre de lenguaje de alto nivel, también hay
**lenguajes de bajo nivel**, a veces denominados lenguajes de máquina o ensamblador.
Hablando en términos generales, las computadoras solo pueden ejecutar programas escritos en
idiomas de bajo nivel. Por lo tanto, los programas escritos en un lenguaje de alto nivel tienen que ser
procesados antes de que puedan ejecutarse. Este procesamiento adicional lleva algún tiempo, que es
una pequeña desventaja de los idiomas de alto nivel.
Sin embargo, las ventajas de los lenguajes de alto nivel son enormes.

Primero, es mucho más fácil programar en un
lenguaje de alto nivel. Los programas escritos en un lenguaje de alto nivel toman menos tiempo
para escribir, son más cortos y fáciles de leer, y es más probable que sean
correctos. Segundo, los lenguajes de alto nivel son **portátiles**, lo que significa que pueden
ejecutarse en diferentes tipos de computadoras con pocas o ninguna modificación. El Nivel bajo
en los programas puede ejecutarse en un solo tipo de computadora y debe reescribirse para ejecutarse
en otro.

Debido a estas ventajas, casi todos los programas están escritos en idiomas de alto nivel.
Los idiomas de bajo nivel se usan solo para unas pocas
aplicaciones.

Dos tipos de programas procesan idiomas de alto nivel en idiomas de bajo nivel:
**intérpretes** y **compiladores**. Un intérprete lee un programa de alto nivel
y lo ejecuta, lo que significa que hace lo que dice el programa. Procesa el
programa un poco a la vez, alternativamente lee líneas y realiza
cálculos

.. image:: Figures/interpret.png
    :alt: Interpretar ilustración

Un compilador lee el programa y lo traduce completamente antes que el programa
comienza a correr. En este caso, el programa de alto nivel se llama **código fuente**, y el programa traducido se llama **object code** o el
**ejecutable**. Una vez que se compila un programa, puede ejecutarlo repetidamente,
sin más traducción.

.. image:: Figures/compile.png
    :alt: Compilar ilustración

Muchos lenguajes modernos usan ambos procesos. Primero se compilan en un lenguaje de nivel
inferior, llamado **byte code**, y luego interpretado por un programa llamado
**máquina virtual**. Python usa ambos procesos, pero por la forma en que
los programadores interactúan con él, generalmente se considera un lenguaje interpretado.

Para el material principal de este libro, no necesitará instalar
o ejecutar python de forma nativa en su computadora. En cambio, estará escribiendo simples
programas y ejecutándolos directamente en su navegador.

En algún momento, le resultará útil tener un entorno completo de Python, en lugar del entorno limitado.
disponible en este libro de texto en línea. Para hacer eso, o bien
instale python en su computadora para que pueda ejecutarse de forma nativa, o use un servidor remoto que proporcione
línea de comando shell o un entorno de jupyter notebook.

**Revisa tu entendimiento**

.. mchoice:: question1_3_1
    :answer_a: Las instrucciones en un programa, escrito en un lenguaje de alto nivel.
    :answer_b: El lenguaje en el que está programando (por ejemplo, Python).
    :answer_c: El entorno/herramienta en la que está programando.
    :answer_d: El número (o "código") que debe ingresar en la parte superior de cada programa para indicarle a la computadora cómo ejecutar su programa.
    :correct: a
    :feedback_a: Ei las instrucciones se almacenan en un archivo, se llama archivo de código fuente.
    :feedback_b: Este lenguaje simplemente se llama lenguaje de programación, o simplemente el lenguaje. Los programas están escritos en este idioma.
    :feedback_c: El entorno puede llamarse IDE o entorno de desarrollo integrado, aunque no siempre.
    :feedback_d: No hay tal número que debe escribir al comienzo de su programa.

    El código fuente es otro nombre para:

.. mchoice:: question1_3_2
    :answer_a: Es de alto nivel si estás de pie y de bajo nivel si estás sentado.
    :answer_b: Es de alto nivel si está programando para una computadora y de bajo nivel si está programando para un teléfono o dispositivo móvil.
    :answer_c: Es de alto nivel si el programa debe procesarse antes de que pueda ejecutarse, y de bajo nivel si la computadora puede ejecutarlo sin procesamiento adicional.
    :answer_d: Es de alto nivel si es fácil de programar y es muy corto; es de bajo nivel si es realmente difícil de programar y los programas son realmente largos.
    :correct: c
    :feedback_a: En este caso, los valores altos y bajos no tienen nada que ver con la altitud.
    :feedback_b: High y low no tienen nada que ver con el tipo de dispositivo para el que está programando. En cambio, mira lo que se necesita para ejecutar el programa escrito en el lenguaje.
    :feedback_c: Python es un lenguaje de alto nivel, pero debe interpretarse en código de máquina (binario) antes de que pueda ejecutarse.
    :feedback_d: Si bien es cierto que generalmente es más fácil programar en un hola

¿Cuál es la diferencia entre un lenguaje de programación de alto nivel y un lenguaje de programación de bajo nivel?

.. mchoice:: question1_3_3
    :answer_a: 1 = Un proceso, 2 = una función
    :answer_b: 1 = Traducir un libro completo, 2 = traducir una línea a la vez
    :answer_c: 1 = Software, 2 = hardware
    :answer_d: 1 = Código de objeto, 2 = código de byte
    :correct: b
    :feedback_a: Compilar es un proceso de software y ejecutar el intérprete es invocar una función, pero ¿en qué se diferencia un proceso de una función?
    :feedback_b: Los compiladores toman el código fuente completo y producen código objeto o el ejecutable y los intérpretes ejecutan el código línea por línea.
    :feedback_c: Tanto los compiladores como los intérpretes son software.
    :feedback_d: Los compiladores pueden producir código objeto o código de bytes dependiendo del idioma. Un intérprete no produce ninguno.

    Elija los mejores reemplazos para 1 y 2 en la siguiente oración: Al comparar compiladores e intérpretes, un compilador es como 1 mientras que un intérprete es como 2.