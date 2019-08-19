..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. _optional_params_chap:

.. qnum::
   :prefix: advfuncs-1-
   :start: 1

Introducción: parámetros opcionales
====================================

En el tratamiento de funciones hasta ahora, cada definición de función especifica cero o más parámetros formales
y cada invocación de función proporciona exactamente esa cantidad de valores. A veces es conveniente tener
**parámetros opcionales** que pueden especificarse u omitirse. Cuando se omite un parámetro opcional de una invocación de función,
el parámetro formal está vinculado a un **valor predeterminado**. Cuando se incluye el parámetro opcional, entonces
El parámetro formal está vinculado al valor proporcionado. Los parámetros opcionales son convenientes cuando una función
casi siempre se usa de manera simple, pero es bueno permitir que se use de una manera más compleja, con valores no predeterminados
valores especificados para los parámetros opcionales.

Considere, por ejemplo, la función ``int``, que ha utilizado anteriormente. Su primer parámetro,
que es obligatorio, especifica el objeto que desea convertir a un entero. Por ejemplo, si tu
llamar en una cadena, ``int("100")``, el valor de retorno será el entero 100.

Esa es la forma más común en que los programadores quieren convertir cadenas en enteros. A veces, sin embargo, ellos
están trabajando con números en alguna otra "base" en lugar de la base 10. Por ejemplo, en la base 8, la más a la derecha
el dígito son unos, el siguiente dígito a la izquierda es 8s, y el que está a la izquierda es el lugar 64s (8**2).

La función int proporciona un parámetro opcional para la base. Cuando no se especifica, el número es
convertido a un entero suponiendo que el número original estaba en la base 10. Decimos que 10 es el valor predeterminado.
Entonces ``int("100")`` es lo mismo que invocar ``int("100", 10)``. Podemos anular el valor predeterminado de 10 por
suministrando un valor diferente.

.. activecode:: ac15_1_1

    print(int("100"))
    print(int("100", 10))   # same thing, 10 is the default value for the base
    print(int("100", 8))     # now the base is 8, so the result is 1*64 = 64

.. note:: La Nueva Matemática de Tom Lehrer's

    Algunos educadores de matemáticas creen que los estudiantes de primaria obtendrán una comprensión mucho más profunda
    del sistema de valor posicional, y establecerán una base para aprender álgebra más adelante, si aprenden a hacer
    aritmética no solo en base 10 sino también en base 8 y otras bases. Esto era parte de un movimiento.
    llamado "The New Math", aunque no es tan nuevo ahora (¡lo tenía cuando estaba en la escuela primaria!) Tom
    Lehrer hizo una canción realmente divertida al respecto, y está ambientada con imágenes en varias versiones en YouTube.
    Mira esta versión `lip-sync <http://www.youtube.com/watch?v=DfCJgC2zezw>`_.
    
Al definir una función, puede especificar un valor predeterminado para un parámetro. Ese parámetro se convierte en un
parámetro opcional cuando se llama a la función. La forma de especificar un valor predeterminado es con una asignación
declaración dentro de la lista de parámetros. Considere el siguiente código, por ejemplo.

.. codelens:: clens15_1_1
    :python: py3

    initial = 7
    def f(x, y =3, z=initial):
        print("x, y, z, are: " + str(x) + ", " + str(y) + ", " + str(z))
        
    f(2)
    f(2, 5)
    f(2, 5, 8)
    
Observe las diferentes vinculaciones de x, y & z en las tres invocaciones de f. La primera vez, y & z tienen
sus valores predeterminados, 3 y 7. La segunda vez, y obtiene el valor 5 que se pasa, pero z aún obtiene el
valor predeterminado de 7. La última vez, z obtiene el valor 8 que se pasa.

Si desea proporcionar un valor no predeterminado para el tercer parámetro (z), también debe proporcionar un valor
para el segundo elemento (y). Veremos en la siguiente sección un mecanismo llamado parámetros de palabras clave que le permite
especifique un valor para z sin especificar un valor para y.

.. note::

   Este es un segundo uso relacionado, pero ligeramente diferente de = del que hemos visto anteriormente. En una declaración de asignación independiente, que no forma parte de una definición de función, ``x=3`` asigna 3 a la variable x. Como parte de la especificación de los parámetros en una definición de función, ``x=3`` dice que 3 es el *valor predeterminado* para x, que se usa *solo cuando* no se proporciona ningún valor durante la invocación de la función.

Hay dos cosas difíciles que pueden confundirte con los valores predeterminados. El primero es que el valor predeterminado
se determina en el momento en que se define la función, no en el momento en que se invoca. Asi que
en el ejemplo anterior, si quisiéramos invocar la función f con un valor de 10 para z, no podemos simplemente
establecer initial = 10 justo antes de invocar f. Vea lo que sucede en el código a continuación, donde z todavía obtiene el
valor 7 cuando se invoca f sin especificar un valor para z.

.. codelens:: clens15_1_2
    :python: py3

    initial = 7
    def f(x, y =3, z=initial):
        print("x, y, z, are: " + str(x) + ", " + str(y) + ", " + str(z))
        
    initial = 10
    f(2)
 
La segunda cosa difícil es que si el valor predeterminado se establece en un objeto mutable, como una lista o un diccionario,
ese objeto se compartirá en todas las invocaciones de la función. Esto puede ser muy confuso, así que le sugiero que
nunca establezca un valor predeterminado que sea un objeto mutable. Por ejemplo, siga la ejecución de este cuidadosamente.

.. codelens:: opt_params_4
    :python: py3

    def f(a, L=[]):
        L.append(a)
        return L
    
    print(f(1))
    print(f(2))
    print(f(3))
    print(f(4, ["Hello"]))
    print(f(5, ["Hello"]))
    
Cuando se usa el valor predeterminado, se comparte la misma lista. Pero en las líneas 8 y 9 dos copias diferentes de la lista
["Hello"] son proporcionados , por lo que el 4 que se adjunta no está presente en la lista que se imprime en la línea 9.

**Check your understanding**

.. mchoice:: question15_1_1
   :answer_a: 0
   :answer_b: 1
   :answer_c: None
   :answer_d: Error de tiempo de ejecución ya que no se pasan parámetros en la llamada a f.
   :correct: a
   :feedback_a: Como no se especifican parámetros, x es 0 e y es 1, por lo que se devuelve 0.
   :feedback_b: 0 * 1 es 0.
   :feedback_c: La función devuelve un valor.
   :feedback_d: Como ambos parámetros tienen valores predeterminados especificados en la definición, ambos son opcionales.
   :practice: T

   ¿Qué imprimirá el siguiente código?
   
   .. code-block:: python 

       def f(x = 0, y = 1):
           return x * y
           
       print(f())

.. mchoice:: question15_1_2
   :answer_a: 0
   :answer_b: 1
   :answer_c: None
   :answer_d: Error de tiempo de ejecución ya que falta el segundo valor del parámetro.
   :correct: b
   :feedback_a: Como se especifica un valor de parámetro, está vinculado a x; y obtiene el valor predeterminado de 1.
   :feedback_b: Como se especifica un valor de parámetro, está vinculado a x; y obtiene el valor predeterminado de 1.
   :feedback_c: La función devuelve un valor.
   :feedback_d: Como ambos parámetros tienen valores predeterminados especificados en la definición, ambos son opcionales.
   :practice: T

   ¿Qué imprimirá el siguiente código?
   
   .. code-block:: python 

       def f(x = 0, y = 1):
           return x * y
           
       print(f(1))

.. activecode:: ac15_1_2
   :language: python
   :autograde: unittest
   :practice: T

   **3.** Escriba una función llamada ``str_mult`` que tome un parámetro de cadena requerido y un parámetro entero opcional. El valor predeterminado para el parámetro entero debe ser 3. La función debe devolver la cadena multiplicada por el parámetro entero.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(str_mult("ha"), "hahaha", "Testing that str_mult('ha') returns 'hahaha'")
         self.assertEqual(str_mult("ha", 10), "hahahahahahahahahaha", "Testing that str_mult('ha') returns 'hahahahahahahahahaha'")
         self.assertEqual(str_mult("ha", 0), "", "Testing that str_mult('ha', 0) returns ''")

   myTests().main()
