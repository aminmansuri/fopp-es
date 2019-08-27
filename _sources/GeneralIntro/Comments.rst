..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: intro-10-
   :start: 1

Comentarios
-----------

A medida que los programas se hacen más grandes y más complicados, se vuelven más difíciles de leer.
Los lenguajes formales son densos y, a menudo, es difícil observar un fragmento de
código y descifrar lo que está haciendo o por qué.
Por esta razón, es una buena idea agregar notas a sus programas para explicar en
lenguaje natural lo que está haciendo el programa. Estas notas se llaman comentarios.

Un **comentario** en un programa de computadora es texto que está destinado solo para lectores humanos: el intérprete lo ignora por completo.
En Python, el símbolo ``#`` comienza un comentario. El resto de la línea se ignora.
Aquí hay una nueva versión de *Hello, World!*.

.. activecode:: ac1_8_1

    #---------------------------------------------------------
    # Este programa de prueba muestra cuán elegante es Python!
    # Escrito por Joe Soap, Diciembre 2010.
    # Cualquiera puede copiar o modificar este programa libremente.
    #---------------------------------------------------------

    print("Hello, World!")     # No es facil!

Tenga en cuenta que cuando ejecuta este programa, solo imprime la frase Hello, World! Ninguno de los comentarios aparece.
También notará que hemos dejado una línea en blanco en el programa. Las líneas en blanco también son ignoradas por el intérprete,
pero los comentarios y las líneas en blanco pueden hacer de sus programas mucho más fáciles de analizar para los humanos. ¡Úsalos generosamente!

**Revisa tu entendimiento**

.. mchoice:: question1_8_1
   :answer_a: Para decirle a la computadora lo que quiere decir en su programa.
   :answer_b: Para que las personas que leen su código sepan, en lenguaje natural, qué está haciendo el programa.
   :answer_c: Nada, son información extraña que no es necesaria.
   :answer_d: Nada en un programa corto. Solo son necesarios para programas realmente grandes.
   :correct: b
   :feedback_a: La computadora ignora los comentarios.
   :feedback_b: La computadora ignora los comentarios. Es para los humanos que "consumirán" su programa.
   :feedback_c: Los comentarios pueden proporcionar información muy necesaria para cualquiera que lea el programa.
   :feedback_d: Incluso los programas pequeños se benefician de los comentarios.

   ¿Para qué son los comentarios?

