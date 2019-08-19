..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: func-3-
   :start: 1

Parámetros de funciones
--------------------------

Las funciones con nombre son buenas porque, una vez que están definidas y entendemos lo que hacen, podemos referirnos a ellas por nombre
y no pensar demasiado en lo que hacen. Con los parámetros, las funciones son aún más potentes, porque pueden hacer
más o menos lo mismo en cada invocación, pero no exactamente lo mismo. Los parámetros pueden hacer que hagan
algo un poco diferente.

La siguiente figura muestra esta relación. Una función necesita cierta información para hacer su trabajo. Estos valores, a menudo
llamados **argumentos** o **parámetros reales** o **valores de parámetros**, son pasados a la función por el usuario.

.. image:: Figures/blackboxproc.png

Este tipo de diagrama a menudo se llama un **diagrama de recuadro negro** porque solo establece los requisitos de la
perspectiva del usuario (bueno, el programador, pero el programador que usa la función, que puede ser diferente al
programador que creó la función). El usuario debe conocer el nombre de la función y qué argumentos deben ser
pasados. Los detalles de cómo funciona la función están ocultos dentro del "recuadro negro".

Ya ha estado haciendo invocaciones de funciones con parámetros. Por ejemplo, cuando escribe ``len("abc")`` o
``len([3, 9, "hello"])``, len es el nombre de una función y el valor que pones entre paréntesis, la cadena
"abc" o la lista [3, 9, "hello"], es un valor de parámetro.

Cuando una función tiene uno o más parámetros, los nombres de los parámetros aparecen en la definición de la función, y
los valores para asignar a esos parámetros aparecen dentro de los paréntesis de la invocación de la función. Veamos cada uno de
esos un poco más cuidadosamente.

En la definición, la lista de parámetros a veces se denomina **parámetros formales** o **nombres de parámetros**.
Estos nombres pueden ser cualquier nombre de variable válido. Si hay más de uno, están separados por comas.

En la invocación de la función, dentro de los paréntesis se debe proporcionar un valor para cada uno de los nombres de los parámetros. Estas
los valores están separados por comas. Los valores se pueden especificar directamente o mediante cualquier expresión de Python que incluya una
referencia a algún otro nombre de variable.

Eso puede ser un poco confuso, así que comencemos mirando una función con solo un parámetro. El hello revisa
la función personaliza, el saludo: la persona a saludar se especifica mediante el parámetro.

.. codelens:: clens11_3_1
   :python: py3

   def hello2(s):
      print("Hello " + s)
      print("Glad to meet you")
         
   hello2("Iman")
   hello2("Jackie")

Primero, observe que hello2 tiene un parámetro formal, s. Puedes decir eso porque
hay exactamente un nombre de variable dentro de los paréntesis en la línea 1.

Luego, observe lo que sucedió durante el Paso 2. El control pasó a la función, tal como vimos antes. Pero
además, la variable s estaba vinculada a un valor, la cadena "Iman". Cuando llegó al Paso 7, para la segunda invocación de
la función, s estaba vinculada a "Jackie".

Las invocaciones de funciones siempre funcionan de esa manera. La expresión dentro de los paréntesis en la línea que invoca la función
se evalúa antes de pasar el control a la función. El valor se asigna al parámetro formal correspondiente.
Luego, cuando el bloque de código dentro de la función se está ejecutando, puede referirse a ese parámetro formal y obtener su valor.
El valor que se 'pasó' a la función.

.. showeval:: eval11_3_1
   :trace_mode: true

   def hello2(s):
       print("Hello " + s)
       print("Glad to meet you")

   hello2("Nick")
   ~~~~
   {{hello2("Nick")}}{{def hello2(s):}}
   def hello2({{s}}{{"Nick"}}):
   {{def hello2("Nick"):}}{{print("Hello " + s)}}
   print("Hello " + {{s}}{{"Nick"}})
   {{print("Hello " + "Nick")     #imprime "hello Nick"}}{{print("Glad to meet you")   #imprime "Glad to meet you"}}
   {{print("Glad to meet you")   #imprime "Glad to meet you"}}{{# the function is finished}}

Para tener una idea de eso, invoquemos hello2 usando algunas expresiones más complicadas. Pruebe algunos de los suyos también.

.. activecode:: ac11_3_1

   def hello2(s):
       print("Hello " + s)
       print("Glad to meet you")
         
   hello2("Iman" + " and Jackie")
   hello2("Class " * 3)

Ahora consideremos una función con dos parámetros. Esta versión de hello toma
un parámetro que controla cuántas veces se imprimirá el saludo.

.. codelens:: clens11_3_2
   :python: py3

   def hello3(s, n):
      greeting = "Hello {} ".format(s)
      print(greeting*n)
         
   hello3("Wei", 4)
   hello3("", 1)
   hello3("Kitty", 11)

En el paso 3 de la ejecución, en la primera invocación de hello3, observe que la variable s está vinculada
al valor "Wei" y la variable n está vinculada al valor 4.

Así es como siempre funcionan las invocaciones de funciones. Cada una de las expresiones, separadas por comas, que están dentro de
los paréntesis se evalúan para producir valores. Entonces esos valores se corresponden posicionalmente
con los parámetros formales. El primer nombre del parámetro está vinculado al primer valor
previsto. El segundo nombre del parámetro está vinculado al segundo valor proporcionado. Y así.

**Revisa tu entendimiento**

.. mchoice:: question11_3_1
   :answer_a: def greet(t):
   :answer_b: def greet:
   :answer_c: greet(t, n):
   :answer_d: def greet(t, n)
   :correct: a
   :feedback_a: Una función puede tomar cero o más parámetros. En este caso tiene uno.
   :feedback_b: una función necesita especificar sus parámetros en su encabezado. Si no hay parámetros, ponga () después del nombre de la función.
   :feedback_c: una definición de función debe incluir la palabra clave def.
   :feedback_d: un encabezado de definición de función debe terminar en dos puntos (:).
   :practice: T

   ¿Cuál de los siguientes es un encabezado de función válido (primera línea de una definición de función)?

.. mchoice:: question11_3_2
   :answer_a: def print_many(x, y):
   :answer_b: print_many
   :answer_c: print_many(x, y)
   :answer_d: Print out string x, y times.
   :correct: b
   :feedback_a: Esta línea es el encabezado completo de la función (excepto el punto y coma) que incluye el nombre y varios otros componentes.
   :feedback_b: Sí, el nombre de la función se proporciona después de la palabra clave def y antes de la lista de parámetros.
   :feedback_c: Esto incluye el nombre de la función y sus parámetros
   :feedback_d: Este es un comentario que indica lo que hace la función.

   ¿Cuál es el nombre de la siguiente función?

   .. code-block:: python

     def print_many(x, y):
         """Imprimir cadena x, y veces."""
         for i in range(y):
             print(x)

.. mchoice:: question11_3_3
   :answer_a: i
   :answer_b: x
   :answer_c: x, y
   :answer_d: x, y, i
   :correct: c
   :feedback_a: i es una variable utilizada dentro de la función, pero no un parámetro, que se pasa a la función.
   :feedback_b: x es solo uno de los parámetros para esta función.
   :feedback_c: Sí, la función especifica dos parámetros: x e y.
   :feedback_d: los parámetros incluyen solo aquellas variables cuyos valores la función espera recibir como entrada. Se especifican en el encabezado de la función.

   ¿Cuáles son los parámetros de la siguiente función?

   .. code-block:: python

     def print_many(x, y):
         """Imprimir cadena x, y veces."""
         for i in range(y):
             print(x)

.. mchoice:: question11_3_4
   :answer_a: print_many(x, y)
   :answer_b: print_many
   :answer_c: print_many("Greetings")
   :answer_d: print_many("Greetings", 10):
   :answer_e: print_many("Greetings", z)
   :correct: e
   :feedback_a: No, x e y son los nombres de los parámetros formales de esta función. Cuando se llama a la función, requiere que se pasen los valores reales.
   :feedback_b: Una llamada de función siempre requiere paréntesis después del nombre de la función.
   :feedback_c: Esta función toma dos parámetros (argumentos)
   :feedback_d: Solo se requieren dos puntos en una definición de función. Causará un error con una llamada a la función.
   :feedback_e: Dado que z tiene el valor 3, hemos pasado dos valores correctos para esta función. Los "saludos" se imprimirán 3 veces.

   Teniendo en cuenta la siguiente función, ¿cuál de las siguientes afirmaciones invoca o invoca correctamente esta función (es decir, hace que se ejecute)?

   .. code-block:: python

      def print_many(x, y):
         """Imprimir cadena x, y veces."""
         for i in range(y):
             print(x)

      z = 3

.. mchoice:: question11_3_5
   :answer_a: True
   :answer_b: False
   :correct: a
   :feedback_a: Sí, puede llamar a una función varias veces poniendo la llamada en un bucle.
   :feedback_b: Uno de los propósitos de una función es permitirle llamarla más de una vez. Colocarlo en un bucle le permite ejecutarse varias veces a medida que el cuerpo del bucle se ejecuta varias veces.

   True o false: se puede llamar a una función varias veces colocando una llamada de función en el cuerpo de un bucle for.

.. mchoice:: question11_3_6
   :answer_a: Hello
   :answer_b: Goodbye
   :answer_c: s1
   :answer_d: s2
   :correct: b
   :feedback_a: "Hello" es más corto que "Goodbye"
   :feedback_b: "Goodbye" es más largo que "Hello"
   :feedback_c: s1 es un nombre de variable; se imprimirá su valor, no el nombre de la variable.
   :feedback_d: s2 es un nombre de variable; se imprimirá su valor, no el nombre de la variable.
   :practice: T

   ¿Qué salida producirá el siguiente código?
   
   .. code-block:: python

      def cyu(s1, s2):
         if len(s1) > len(s2):
            print(s1)
         else:
            print(s2)
            
      cyu("Hello", "Goodbye")
