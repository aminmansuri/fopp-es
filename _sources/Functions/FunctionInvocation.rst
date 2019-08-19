..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: func-2-
   :start: 1

Invocación de funciones
--------------------------

La definición de una nueva función no hace que la función se ejecute.
Para ejecutar la función, necesitamos una **llamada de función**. Esto también se conoce como una **invocación de función**.

.. note::

   Esta sección es una revisión de algo que aprendimos al comienzo del libro de texto.

La forma de invocar una función es referirse a ella por nombre, seguido de paréntesis. Como no hay parámetros para
la función hello, no necesitaremos poner nada dentro de los paréntesis cuando la llamemos. Una vez que hemos definido una
función, podemos llamarlo con la frecuencia que queramos y sus declaraciones se ejecutarán cada vez que lo llamemos.

.. codelens:: clens11_2_1
   :python: py3

   def hello():
      print("Hello")
      print("Glad to meet you")
   
   print(type(hello))
   print(type("hello"))
      
   hello()
   print("Hey, that just printed two lines with one line of code!")
   hello()  # do it again, just because we can...

Echemos un vistazo más de cerca a lo que sucede cuando define una función y cuando ejecuta la función.
Intenta recorrer el código anterior.

Primero, tenga en cuenta que en el Paso 1, cuando ejecuta la línea 1, *no* ejecuta las líneas 2 y 3. En cambio, como puede ver en
área azul "Variables globales", crea una variable llamada hello cuyo valor es un objeto de función python. En el
diagrama de que el objeto está etiquetado hello() con una notación por encima de que es una función.

En el Paso 2, la siguiente línea de código para ejecutar es la línea 5. Solo para enfatizar que hello es una variable como cualquier otra, y
que las funciones son objetos python como cualquier otro, solo de un tipo particular, la línea 5 imprime el tipo del objeto
referido por la variable hola. Su tipo es oficialmente 'función'.

La línea 6 está ahí para recordarle la diferencia entre referirse a el
nombre de la variable (nombre de la función) hello y haciendo referencia a la cadena "hello".

En el Paso 4 llegamos a la línea 8, que tiene una invocación de la función. La forma en que funciona la invocación de funciones es que
el bloque de código dentro de la definición de la función se ejecuta de la manera habitual, pero al final, la ejecución salta al punto
después de la invocación de la función.

Puede ver eso siguiendo los siguientes pasos. En el Paso 5, la flecha roja se movió a la línea 2, que se ejecutará
próximo. Decimos que *control ha pasado* del programa de nivel superior a la función hello. Después de imprimir los pasos 5 y 6
dos líneas, en el Paso 7, el control volverá al punto posterior al inicio de la invocación. En el Paso 8, eso
pasó.

El mismo proceso de invocación ocurre nuevamente en la línea 10, con las líneas 2 y 3 ejecutándose por segunda vez.

.. admonition:: Error común con funciones

    Es un error común para los principiantes olvidar sus paréntesis después del nombre de la función. Esto es particularmente
    común en el caso en que no se requieren parámetros. Porque la función hello definida anteriormente no
    requieren parámetros, es fácil olvidar el paréntesis. Esto es menos común, pero aún posible, cuando se intenta
    llamar a funciones que requieren parámetros.

**Revisa tu entendimiento**

.. mchoice:: question11_2_1
   :answer_a: Una secuencia nombrada de declaraciones.
   :answer_b: Cualquier secuencia de declaraciones.
   :answer_c: Una expresión matemática que calcula un valor.
   :answer_d: Una declaración de la forma x = 5 + 4.
   :correct: a
   :feedback_a: Sí, una función es una secuencia nombrada de declaraciones.
   :feedback_b: Si bien las funciones contienen secuencias de declaraciones, no todas las secuencias de declaraciones se consideran funciones.
   :feedback_c: Si bien algunas funciones calculan valores, la idea de Python de una función es ligeramente diferente de la idea matemática de una función en que no todas las funciones calculan valores. Considere, por ejemplo, las funciones de tortuga en esta sección. Hicieron que la tortuga dibujara una forma específica, en lugar de calcular un valor.
   :feedback_d: Esta declaración se llama una declaración de asignación. Asigna el valor de la derecha (9) al nombre de la izquierda (x).

   ¿Qué es una función en Python?

.. mchoice:: question11_2_2
   :answer_a: Mejorar la velocidad de ejecución.
   :answer_b: Para ayudar al programador a organizar programas en fragmentos que coincidan con cómo piensan sobre la solución del problema.
   :answer_c: Todos los programas de Python deben escribirse usando funciones
   :answer_d: Para calcular valores.
   :correct: b
   :feedback_a: Las funciones tienen poco efecto sobre qué tan rápido se ejecuta el programa.
   :feedback_b: Si bien no se requieren funciones, ayudan al programador a pensar mejor sobre la solución al organizar partes de la solución en fragmentos lógicos que pueden reutilizarse.
   :feedback_c: En los primeros capítulos, ha visto muchos ejemplos de programas Python escritos sin el uso de funciones. Si bien escribir y usar funciones es deseable y esencial para un buen estilo de programación a medida que sus programas se alargan, no es obligatorio.
   :feedback_d: No todas las funciones calculan valores.

   ¿Cuál es un propósito principal de una función?

.. mchoice:: question11_2_3
   :answer_a: 0
   :answer_b: 1
   :answer_c: 2
   :correct: a
   :feedback_a: El código solo define la función. Nada se imprime hasta que se llama a la función.
   :feedback_b: Verifique nuevamente.
   :feedback_c: Cuando se invoca la función, imprimirá dos líneas, pero solo se ha definido, no invocado.
   :practice: T

   ¿Cuántas líneas saldrán al ejecutar este código?
   
   .. code-block:: python

      def hello():
         print("Hello")
         print("Glad to meet you")

.. mchoice:: question11_2_4
   :answer_a: 0
   :answer_b: 1
   :answer_c: 3
   :answer_d: 4
   :answer_e: 7
   :correct: e
   :feedback_a: Aquí se invoca la función y también hay una declaración de impresión separada.
   :feedback_b: Solo hay una declaración de impresión fuera de la función, pero las invocaciones de saludo también hacen que se impriman líneas.
   :feedback_c: Hay tres declaraciones de impresión, pero la función se invoca más de una vez.
   :feedback_d: Cada vez que se invoca la función, imprimirá dos líneas, no una.
   :feedback_e: Tres invocaciones generan dos líneas cada una, más la línea "Funciona".
   :practice: T

   ¿Cuántas líneas saldrán al ejecutar este código?

   .. code-block:: python

      def hello():
         print("Hello")
         print("Glad to meet you")
         
      hello()
      print("It works")
      hello()
      hello()   
