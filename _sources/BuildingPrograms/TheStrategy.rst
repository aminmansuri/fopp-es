..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: buildP-1-
   :start: 1

Creando un Programa: Una Estrategia
=====================================

Sobre la base de las lecciones aprendidas en el primer interludio de depuración, este capítulo ofrece una estrategia para
escribir un programa para resolver un problema como los que aparecen en los ejercicios al final de los capítulos de este libro.
(Un enfoque similar es útil para escribir programas más grandes, pero eso vendrá más adelante).

.. admonition:: Advertencia.

   Puede resultarle tentador comenzar un ejercicio copiando y pegando un fragmento de código de alguna parte del libro de texto, y esperando que una pequeña edición conduzca a una solución al problema actual. A menudo esto conducirá a la frustración y la confusión; después de probar algunas sustituciones de código que le resulten vagamente familiares, encontrará que el código parece un poco complicado y los resultados son desconcertantes.

   Copiar y editar fragmentos de código es en realidad un elemento útil de la estrategia que describimos a continuación. Pero llega un poco más tarde en el proceso, no como lo primero. Y requiere un poco de trabajo para asegurarse de que comprende el fragmento de código que ha copiado. Solo así podrá encontrar las pequeñas ediciones *correctas* en el fragmento de código para que haga lo que desea.

Hay tres pasos básicos para la estrategia que recomendamos: Esquematizar; Codificar una sección a la vez; Limpiar.

Dibuja un esquema
------------------

Le sugerimos que primero escriba todos los pasos que desea que haga el programa. Puedes hacer esto de la manera que quieras. Vamos a
mostrarle cómo esquematizar usando comentarios, pero si es más visual, es posible que desee dibujar en un papel y si es más espacial
prueba caminando por la habitación. El gran truco es entender todo lo que quieres hacer primero con tus propias palabras, para que luego estés
traduciéndolo a la computadora.

Codifica una sección a la vez
-------------------------------

Después de trazar su programa, debe escribir el código una sección a la vez y probar cuidadosamente esa sección antes de continuar. La idea aquí es asegurarse de que su programa esté haciendo lo que cree que está haciendo en cada etapa.

Traducir desde su descripción a código puede ser el paso más difícil para usted al principio de su aprendizaje sobre programación. Más tarde vendrá más naturalmente. Aquí hay una lista de preguntas que puede resultarle útil al tratar de encontrar el código de Python adecuado para expresar su idea, en función de lo que ha aprendido hasta ahora:

* ¿Esta operación extrae un elemento de una lista, cadena o diccionario? Si es así, use [] para extraer el elemento que desea.
* ¿Esta operación está transformando una cadena en otra cadena? Si es así, mira el resumen de los métodos de cadena.
* ¿Esta operación está modificando una lista? Si es así, mira el material en las listas.
* ¿La operación está haciendo algo varias veces? Si es así, querrás un bucle ``for``. Comience por hacer una versión esqueleto de un bucle for, y luego complete las partes que están entre <>

::

  for <varname> in <seq>:
                  <code block line 1>
                  <code block line 2>
                  ...

* ¿Es la operación algo que solo debería ocurrir en algunas circunstancias y no en otras? Si es así, querrás una sentencia ``if``. Comience por hacer una versión esqueleto de un fragmento de código if/then/else, y luego complete las partes que están entre <>

::

  if <boolean exp>:
    <if block here>
    ...
  else:
    <else block here>
    ...

* ¿Es este un patrón acumulador? Si es así, comience por hacer una versión esqueleto y luego complétela.

::

  #initialize accumulator
  a = <initial value>

  for <varname> in <seq>:
    <some code in for block>
    a = <new_value>
    <other code in for block>
  print(a)


Finalmente, es posible que se te recuerde un fragmento de código en algún lugar del libro de texto que hizo algo similar a lo que quieres hacer. Ahora es el momento de copiar y editar ese código. **¡Pero espera!** Antes de comenzar a editar ese fragmento de código, asegúrate de entenderlo. Vea la sección a continuación sobre la comprensión del código.

Limpia
-------

Cuando haya terminado de delinear y probar su programa, elimine cualquier sentencia de impresión de diagnóstico de su programa. Nadie realmente necesita ver las declaraciones de prueba que escribió, y dejar las declaraciones de prueba en el programa podría confundirlo si agrega más al programa.

Los comentarios adicionales ayudan a otras personas a leer su código, pero trate de dejar solo los bits que considere útiles. Hay un arte en escribir buenos comentarios informativos, y solo puedes aprender este arte leyendo los programas de otras personas y haciendo que tus compañeros lean tus programas. Como regla general para comentarios, cuando tenga dudas, guárdelo; si le preocupa que no tenga sentido para usted u otra persona más tarde, agregue más detalles.

En las próximas páginas, veremos este proceso utilizando una pregunta similar a algo que quizás ya haya visto antes.
