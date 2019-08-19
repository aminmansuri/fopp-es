..  Copyright (C)  Paul Rensick, Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

..  shortname:: Keyword Parameters
..  description:: Using keyword parameters when calling a function.

.. qnum::
   :prefix: advfuncs-2-
   :start: 1

Parámetros de palabras clave
============================

En la sección anterior, en :ref:`Parámetros opcionales <optional_params_chap>` aprendiste a definir valores predeterminados
para parámetros formales, que hicieron opcional proporcionar valores para esos parámetros cuando se invocan las funciones.

En este capítulo, verá una forma más de invocar funciones con parámetros opcionales, con parámetros basados en el paso​
de palabras clave. Esto es particularmente conveniente cuando hay varios parámetros opcionales y desea proporcionar un valor para
uno de los parámetros posteriores sin proporcionar un valor para los anteriores.

La documentación oficial en línea de Python incluye un tutorial sobre parámetros opcionales
que cubre bastante bien el tema. Por favor lea el contenido
allí: `Argumentos de palabras clave <http://docs.python.org/3/tutorial/controlflow.html#keyword-arguments>`_

No se preocupe por el ejemplo ``def cheeseshop(kind, *arguments, **keywords):``. Deberías poder sobrevivir sin
Comprender los ``*parámetros`` y los ``**parámetros`` en este curso. Pero asegúrate de entender lo que está por encima de eso.

La idea básica de pasar argumentos por palabra clave es muy simple. Al invocar una función, dentro de los paréntesis hay
son siempre 0 o más valores, separados por comas. Con argumentos de palabras clave, algunos de los valores pueden tener la forma
``paramname = <expr>`` en lugar de solo ``<expr>``. Tenga en cuenta que cuando tiene ``paramname = <expr>`` en una definición de
una función, es definir el valor predeterminado para un parámetro cuando no se proporciona ningún valor en la invocación; cuando tengas
``paramname = <expr>`` en la invocación, está proporcionando un valor, anulando el valor predeterminado para ese nombre de parámetro.

Para que sea más fácil seguir los detalles de los ejemplos en el tutorial oficial de Python, puede recorrerlos en CodeLens.

.. codelens:: keyword_params_1
   :python: py3

   def parrot(voltage, state='a stiff', action='voom', type='Norwegian Blue'):
       print("-- This parrot wouldn't" + action,)
       print("if you put" + str(voltage) + "volts through it.")
       print("-- Lovely plumage, the" +  type)
       print("-- It's " + state + "!")
       
   parrot(1000)                                          # 1 positional argument
   parrot(voltage=1000)                                  # 1 keyword argument
   parrot(voltage=1000000, action='VOOOOOM')             # 2 keyword arguments
   parrot(action='VOOOOOM', voltage=1000000)             # 2 keyword arguments
   parrot('a million', 'bereft of life', 'jump')         # 3 positional arguments
   parrot('a thousand', state='pushing up the daisies')  # 1 positional, 1 keyword
   
A medida que avanza, cada vez que se invoca la función, haga una predicción sobre cuál será el valor de cada uno de los
cuatro parámetros durante la ejecución de las líneas 2-5. Luego, mire la pila para ver cuáles son realmente durante el
ejecución.

.. note::

   Tenga en cuenta que tenemos otro uso ligeramente diferente del signo = aquí. Como una declaración independiente de alto nivel,
   ``x=3``, la variable x se establece en 3. Dentro de los paréntesis que invocan una función, ``x=3`` dice que 3 debería ser
   enlazado a la variable local x en el marco de la pila para la invocación de la función. Dentro de los paréntesis de una función
   definición, ``x=3`` dice que 3 debería ser el valor para x en cada invocación de la función donde no hay valor provisto explícitamente para x.


Parámetros de palabras clave con .format
------------------------------------------

Anteriormente aprendió a usar el método de ``format`` para cadenas, que le permite estructurar cadenas como
sentencias para rellenar los espacios en blanco. Ahora que ha aprendido acerca de los parámetros opcionales y de palabras clave, podemos presentar una nueva forma de
use el método de ``format``.

Esta otra opción es referirse específicamente a palabras clave para valores de interpolación, como a continuación.

.. activecode:: ac15_2_1
 
   names_scores = [("Jack",[67,89,91]),("Emily",[72,95,42]),("Taylor",[83,92,86])]
   for name, scores in names_scores:
       print("The scores {nm} got were: {s1},{s2},{s3}.".format(nm=name,s1=scores[0],s2=scores[1],s3=scores[2]))


A veces, es posible que desee utilizar el método ``.format`` para insertar el mismo valor en una cadena
varias veces. Puede hacerlo simplemente pasando la misma cadena al método de formato,
suponiendo que haya incluido ``{}`` s en la cadena en todas partes donde desee interpolarlos. Pero
¡también puede usar referencias de paso posicional para hacer esto! El orden en que pasas
los argumentos en el método ``format`` es importante: el primero es el argumento ``0``, el segundo es
argumento ``1``, y así sucesivamente.

Por ejemplo,

.. activecode:: ac15_2_2
 
   # esto funciona
   names = ["Jack","Jill","Mary"]
   for n in names:
       print("'{}!' she yelled. '{}! {}, {}!'".format(n,n,n,"say hello"))

   # pero esto también funciona!
   names = ["Jack","Jill","Mary"]
   for n in names:
       print("'{0}!' she yelled. '{0}! {0}, {1}!'".format(n,"say hello"))


**Revisa tu entendimiento**

.. mchoice:: question15_2_1
   :answer_a: 2
   :answer_b: 3
   :answer_c: 5
   :answer_d: 7
   :answer_e: Error de tiempo de ejecución ya que no se pasan suficientes valores en la llamada a f
   :correct: d
   :feedback_a: 2 está vinculado a x, no z
   :feedback_b: 3 es el valor predeterminado para y, no z
   :feedback_c: 5 está vinculado a y, no z
   :feedback_d: 2 está vinculado x, 5 a y, y z obtiene su valor predeterminado, 7
   :feedback_e: z tiene un valor predeterminado en la definición de la función, por lo que es opcional pasarle un valor.
   :practice: T

   ¿Qué valor se imprimirá para z?
   
   .. code-block:: python 

      initial = 7
      def f(x, y = 3, z = initial):
          print("x, y, z are:", x, y, z)
      
      f(2, 5) 
         
.. mchoice:: question15_2_2
   :answer_a: 2
   :answer_b: 3
   :answer_c: 5
   :answer_d: 10
   :answer_e: Error de tiempo de ejecución ya que no se proporciona ningún valor para y, que viene antes de z
   :correct: b
   :feedback_a: 2 está unido a x, no a y
   :feedback_b: 3 es el valor predeterminado para y, y no se especifica ningún valor para y,
   :feedback_c: ¿Qué dijiste?
   :feedback_d: 10 es el segundo valor pasado, pero está vinculado a z, no a y.
   :feedback_e: Esa es la belleza de pasar parámetros con palabras clave; puede omitir algunos parámetros y ellos obtienen sus valores predeterminados.
   :practice: T

   ¿Qué valor se imprimirá para y?
   
   .. code-block:: python 

      initial = 7
      def f(x, y = 3, z = initial):
          print("x, y, z are:", x, y, z)
      
      f(2, z = 10)
           
.. mchoice:: question15_2_3
   :answer_a: 2
   :answer_b: 3
   :answer_c: 5
   :answer_d: 7
   :answer_e: Error de tiempo de ejecución ya que se proporcionan dos valores diferentes para x
   :correct: e
   :feedback_a: 2 está vinculado a x ya que es el primer valor, pero también lo es 5, según la palabra clave.
   :feedback_b: 
   :feedback_c: 5 está vinculado a x por palabra clave, pero 2 también está vinculado a él en virtud de ser el valor y no tener una palabra clave. El entorno en línea, en realidad lo permite, pero no en un intérprete de Python adecuado.
   :feedback_d: 
   :feedback_e: 2 está vinculado a x ya que es el primer valor, pero también lo es 5, según la palabra clave.
   :practice: T

   ¿Qué valor se imprimirá para x?
   
   .. code-block:: python 

      initial = 7
      def f(x, y = 3, z = initial):
          print("x, y, z are:", x, y, z)
      
      f(2, x=5) 
   
.. mchoice:: question15_2_4
   :answer_a: 2
   :answer_b: 7
   :answer_c: 0
   :answer_d: Error de tiempo de ejecución ya que se proporcionan dos valores diferentes para inicial.
   :correct: b
   :feedback_a: 2 está unido a x, no z
   :feedback_b: El valor predeterminado para z se determina en el momento en que se define la función; en ese momento inicial tiene el valor 0.
   :feedback_c: El valor predeterminado para z se determina en el momento en que se define la función, no cuando se invoca.
   :feedback_d: No hay nada de malo en reasignar el valor de una variable en un momento posterior.
   :practice: T

   ¿Qué valor se imprimirá para z?
   
   .. code-block:: python 

      initial = 7
      def f(x, y = 3, z = initial):
          print "x, y, z are:", x, y, z
      initial = 0
      f(2)

.. mchoice:: question15_2_5
   :answer_a: 'first!' she yelled. 'Come here, first! f_one, f_two, and f_three are here!'
   :answer_b: 'Alexey!' she yelled. 'Come here, Alexey! Catalina, Misuki, and Pablo are here!'
   :answer_c: 'Catalina!' she yelled. 'Come here, Catalina! Alexey, Misuki, and Pablo are here!'
   :answer_d: There is an error. You cannot repeatedly use the keyword parameters.
   :correct: c
   :feedback_a: Recuerde, los valores dentro de {} son nombres de variables. Se utilizarán los valores de las variables.
   :feedback_b: Mire nuevamente qué valor se establece en la variable primero.
   :feedback_c: Sí, los parámetros de palabras clave determinarán el orden de las cadenas.
   :feedback_d: ¡Esto no es un error, puedes hacerlo en Python!
   :practice: T

   ¿Qué valor se imprimirá a continuación?
   
   .. code-block:: python 

      names = ["Alexey", "Catalina", "Mitsuki", "Pablo"]
      print("'{first}!' she yelled. 'Come here, {first}! {f_one}, {f_two}, and {f_three} are here!'".format(first = names[1], f_one = names[0], f_two = names[2], f_three = names[3]))

.. activecode:: ac15_2_3
   :language: python
   :autograde: unittest
   :practice: T

   **5.** Defina una función llamada ``multiply``. Debe tener un parámetro requerido, una cadena. También debe tener un parámetro opcional, un número entero, llamado ``mult_int``, con un valor predeterminado de 10. La función debe devolver la cadena multiplicada por el número entero. (es decir: Dadas las entradas "Hello", mult_int=3, la función debería devolver "HelloHelloHello")
   ~~~~

   def multiply():

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(multiply("Hello", mult_int = 3), "HelloHelloHello", "Testing the function multiply on inputs 'Hello', 3.")
         self.assertEqual(multiply("Goodbye"), "GoodbyeGoodbyeGoodbyeGoodbyeGoodbyeGoodbyeGoodbyeGoodbyeGoodbyeGoodbye", "Testing the function mulitply on input 'Goodbye'.")

   myTests().main()

.. activecode:: ac15_2_4
   :language: python
   :autograde: unittest
   :practice: T

   **6.** Actualmente se supone que la función debe tomar 1 parámetro requerido y 2 parámetros opcionales, sin embargo, el código no funciona. Arregle el código para que pase la prueba. Esto solo debería requerir cambiar una línea de código.
   ~~~~

   def waste(var = "Water", mar, marble = "type"):
       final_string = var + " " + marble + " " + mar
       return final_string

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(waste("Pokemon"), "Water type Pokemon", "Testing that waste returns the correct string on input 'Pokemon'")

   myTests().main()


