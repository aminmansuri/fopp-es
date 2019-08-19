..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: func-9-
   :start: 1

.. index::
    functional decomposition
    generalization
    abstraction
    flow of execution
    composition
    function; composition

Las funciones pueden llamar a otras funciones (Composición)
-----------------------------------------------------------

Es importante entender que cada una de las funciones que escribimos se puede usar y llamar desde otras funciones que
escribimos. Esta es una de las formas más importantes en que los programadores informáticos toman un gran problema y lo dividen en un
grupo de problemas menores. Este proceso de dividir un problema en subproblemas más pequeños se llama **descomposición funcional**.

Aquí hay un ejemplo simple de descomposición funcional usando dos funciones. La primera función llamada ``square`` simplemente
calcula el cuadrado de un número dado. La segunda función llamada ``sum_of_squares`` hace uso del cuadrado para calcular
la suma de tres números que se han elevado al cuadrado.

.. codelens:: clens11_9_1
    :python: py3

    def square(x):
        y = x * x
        return y

    def sum_of_squares(x,y,z):
        a = square(x)
        b = square(y)
        c = square(z)

        return a+b+c

    a = -5
    b = 2
    c = 10
    result = sum_of_squares(a,b,c)
    print(result)

Aunque esta es una idea bastante simple, en la práctica este ejemplo ilustra muchos conceptos muy importantes de Python,
incluyendo variables locales y globales junto con el paso de parámetros. Tenga en cuenta que el cuerpo de ``square`` no se ejecuta
hasta que se llame desde dentro de la función ``sum_of_squares`` por primera vez en la línea 6.

Observe también que cuando se llama a ``square`` (en el Paso 8, por ejemplo), hay dos grupos de variables locales, uno para
``square`` y uno para ``sum_of_squares``. Cada grupo de variables locales se llama **marco de pila**. Las variables
``x`` e ``y`` son variables locales en ambas funciones. Estas son variables completamente diferentes, aunque al
tener el mismo nombre cada invocación de función crea un nuevo marco, y las variables se buscan en ese marco. Aviso
que en el paso 9, y tiene el valor 25 es un cuadro y 2 en el otro.

¿Qué sucede cuando se refiere a la variable y en la línea 3? Python busca el valor de y en el marco de la pila para la
función ``square``. Si no lo encontraba allí, iría a buscar en el marco global.

Usemos composición para construir una función un poco más útil. Recuerde del capítulo de diccionarios que teníamos un proceso de dos pasos para encontrar la letra que aparece con mayor frecuencia en una cadena de texto:

1. Acumula un diccionario con letras como claves y cuenta como valores. Ver:ref:`example <accumulating_counts>`.
2. Encuentra la mejor clave de ese diccionario. Ver:ref:`example <accumulating_best_key>`.

Podemos hacer funciones para cada una de ellas y luego componerlas en una sola función que encuentre la letra más común.

.. activecode:: ac_11_9_1

    def most_common_letter(s):
        frequencies = count_freqs(s)
        return best_key(frequencies)

    def count_freqs(st):
        d = {}
        for c in st:
            if c not in d:
                 d[c] = 0
            d[c] = d[c] + 1
        return d

    def best_key(dictionary):
        ks = dictionary.keys()
        best_key_so_far = list(ks)[0]  # Have to turn ks into a real list before using [] to select an item
        for k in ks:
            if dictionary[k] > dictionary[best_key_so_far]:
                best_key_so_far = k
        return best_key_so_far

    print(most_common_letter("abbbbbbbbbbbccccddddd"))

**Revisa tu entendimiento**

.. activecode:: ac11_9_1
   :language: python
   :autograde: unittest
   :practice: T

   **1.** Escriba dos funciones, una llamada ``addit`` y otra llamada ``mult``. ``addit`` toma un número como entrada y agrega 5. ``mult`` toma un número como entrada, y multiplica esa entrada por lo que sea devuelto por ``addit``, y luego devuelve el resultado.
   ~~~~

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(mult(1), 6,"Testing the function mult with input 1 (should be 6)")
         self.assertEqual(mult(-2), -6, "Testing the function mult with input -2 (should be -6)")
         self.assertEqual(mult(0), 0, "Testing the function mult with input 0 (should be 0)")

      def testTwo(self):
         self.assertEqual(addit(1), 6, "Testing the function addit with input 1 (should be 6)")
         self.assertEqual(addit(-2), 3, "Testing the function addit with input -2 (should be 3)")
         self.assertEqual(addit(0), 5, "Testing the function addit with input 0 (should be 5)")

   myTests().main()
