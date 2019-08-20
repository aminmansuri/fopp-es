..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: nested-1-
   :start: 1

.. _nested_chap:

Introducción: Datos Anidados e Iteraciones Anidadas
====================================================

Listas con elementos complejos
-------------------------------

Las listas que hemos visto hasta ahora tienen números o cadenas como elementos. Nos hemos metido en algunos elementos más complejos, pero sin
discutiendo explícitamente lo que significaba tener elementos más complejos.

De hecho, los elementos en una lista pueden ser cualquier tipo de objeto python. Por ejemplo, podemos tener una lista de listas.

.. activecode:: ac17_1_1

    nested1 = [['a', 'b', 'c'],['d', 'e'],['f', 'g', 'h']]
    print(nested1[0])
    print(len(nested1))
    nested1.append(['i'])
    print("-------")
    for L in nested1:
        print(L)

La línea 2 imprime el primer elemento de la lista a la que está vinculado ``nested1``. Ese elemento es en sí mismo una lista, por lo que se imprime
con corchetes. Tiene una longitud 3, que se imprime en la línea 3. La línea 4 agrega un nuevo elemento a ``nested1``. Es una lista con
un elemento, 'i' (es una lista con un elemento, no es solo la cadena 'i').

Codelens le ofrece un diagrama de referencia, una visualización del contenido de nested1.

.. codelens:: clens_1_1
    :python: py3

    nested1 = [['a', 'b', 'c'],['d', 'e'],['f', 'g', 'h']]
    print(nested1[0])
    print(len(nested1))
    nested1.append(['i'])
    for L in nested1:
        print(L)


Cuando llegue al paso 4 de la ejecución, eche un vistazo al objeto al que apunta la variable nested1. Es una lista de tres
elementos, numerados 0, 1 y 2. El elemento en la ranura 1 es lo suficientemente pequeño como para mostrarse allí como una
lista que contiene los elementos "d" y "e". El elemento en el espacio 0 no encajaba bien, por lo que se muestra en la figura
como un puntero a otra lista separada; Lo mismo para el elemento en el espacio 2, la lista ``['f', 'g', 'h']``.

No hay un significado especial para saber si la lista se muestra incrustada o con un puntero: eso es solo CodeLens haciendo
el mejor uso del espacio que pueda. De hecho, si continúa con el paso 5, verá que, con la adición de un cuarto elemento, la
lista ['i'], CodeLens ha elegido mostrar las cuatro listas incrustadas en la lista de nivel superior.

Con una lista anidada, puede crear expresiones complejas para obtener o establecer un valor en una sublista.

.. activecode:: ac17_1_2

    nested1 = [['a', 'b', 'c'],['d', 'e'],['f', 'g', 'h']]
    y = nested1[1]
    print(y)
    print(y[0])

    print([10, 20, 30][1])
    print(nested1[1][0])
    
Las líneas 1-4 anteriores probablemente te parezcan bastante naturales. La línea 5 ilustra el procesamiento de expresiones de izquierda a derecha. ``nested1[1]`` se evalúa en la segunda lista interna, por lo que ``nested1[1][1]`` se evalúa en su segundo elemento, ``'e'``.
La línea 6 es solo un recordatorio de que indexa en una lista literal, una que está escrita fuera, de la misma manera que puede indexar en una lista a la que hace referencia una variable. ``[10, 20, 30]`` crea una lista. ``[1]`` indexa en esa lista, sacando el segundo elemento, 20.

Al igual que con una llamada a la función donde se puede pensar que el valor de retorno reemplaza el texto de la llamada a la función en un
expresión, puede evaluar una expresión como esa en la línea 7 de izquierda a derecha. Porque el valor de ``nested1[1]`` es la
lista ``['d', 'e']``, ``nested1[1][0]`` es lo mismo que ``['d', 'e'][0]``. Entonces la línea 7 es equivalente a las líneas 2 y 4; es una forma mas simple
de sacar el primer elemento de la segunda lista.

Al principio, expresiones como esa en la línea 7 pueden parecer extrañas. Pronto se sentirán más naturales y terminarás usando
ellos mucho. Una vez que se sienta cómodo con ellos, la única vez que escribirá código como las líneas 2-4 es cuando no está del todo
Asegúrese de cuál es la estructura de sus datos, por lo que debe escribir y depurar su código de forma incremental. A menudo, lo harás
comience escribiendo código como las líneas 2-4, luego, una vez que esté seguro de que está funcionando, reemplácelo con algo como la línea 7.

Puede cambiar los valores en dichas listas de la forma habitual. Incluso puede usar expresiones complejas para cambiar valores. Considerar
el seguimiento

.. codelens:: clens_1_2
    :python: py3

    nested1 = [['a', 'b', 'c'],['d', 'e'],['f', 'g', 'h'], ['i']]
    nested1[1] = [1, 2, 3]
    nested1[1][0] = 100
    
Los elementos complejos en una lista no tienen que ser listas. Pueden ser tuplas o diccionarios. Los elementos de una lista no todos
tiene que ser al mismo tiempo, pero se volvería loco si tienes listas de objetos de diferentes tipos. Ahórrese
algunos dolores de cabeza y no hagas eso. Aquí hay una lista de diccionarios y algunas operaciones sobre ellos. Echa un vistazo a su
representación visual en codelens.

.. codelens:: clens_1_3
   :python: py3

   nested2 = [{'a': 1, 'b': 3}, {'a': 5, 'c': 90, 5: 50}, {'b': 3, 'c': "yes"}]
   
Intente practicar algunas operaciones para obtener o establecer valores en una lista de diccionarios.

.. actex:: ac17_1_3

   nested2 = [{'a': 1, 'b': 3}, {'a': 5, 'c': 90, 5: 50}, {'b': 3, 'c': "yes"}]

   #escribe el código para imprimir el valor asociado con la clave 'c' en el segundo diccionario (90)

   #escribe el código para imprimir el valor asociado con la clave 'b' en el tercer diccionario

   # agregue un cuarto diccionario al final de la lista; imprima algo para revisar su trabajo.

   #cambie el valor asociado con 'c' en el tercer diccionario de "sí" a "no"; imprima algo para revisar su trabajo

Incluso puede tener una lista de funciones (!).

.. activecode:: ac17_1_4

    def square(x):
        return x*x
        
    L = [square, abs]

    print("****names****")        
    for f in L:
        print(f)
    
    print("****call each of them****")
    for f in L:
        print(f(-2))
        
    print("****just the first one in the list****")
    print(L[0])
    print(L[0](3))
        
        
Aquí, L es una lista con tres elementos. Todos esos artículos son funciones. El primero es el cuadrado de la función que se define en
líneas 1 y 2. La segunda es la función incorporada de python abs. La tercera es una función anónima que devuelve una más.
que su entrada.

En el primer bucle for, no llamamos a las funciones, solo mostramos sus representaciones impresas. La salida
<cuadrado de función> confirma que el cuadrado realmente es un objeto de función. Por alguna razón, en nuestro entorno en línea, no es
capaz de producir una buena representación impresa de la función incorporada abs, por lo que solo muestra <unknown>

En el segundo bucle for, llamamos a cada una de las funciones, pasando el valor -2 cada vez e imprimiendo cualquier valor
La función vuelve.

Las últimas dos líneas solo enfatizan que no hay nada especial en las listas de funciones. Siguen todas las mismas reglas
sobre cómo trata Python cualquier otra lista. Debido a que L[0] selecciona el cuadrado de la función, L[0](3) llama al cuadrado de la función,
pasándole el parámetro 3.

Avance en Codelens si aún no lo tiene todo claro.

.. codelens:: clens_1_4
    :python: py3

    def square(x):
        return x*x
        
    L = [square, abs]

    print("****names****")
    for f in L:
        print(f)
    
    print("****call each of them****")
    for f in L:
        print(f(-2))
        
    print("****just the first one in the list****")
    print(L[0])
    print(L[0](3))

**Revisa tu entendimiento**

.. activecode:: ac17_1_5
   :language: python
   :autograde: unittest
   :practice: T

   **1.** A continuación, hemos proporcionado una lista de listas. Utilice la indexación para asignar el elemento 'horse' al nombre de variable ``idx1``.

   ~~~~

   animals = [['cat', 'dog', 'mouse'], ['horse', 'cow', 'goat'], ['cheetah', 'giraffe', 'rhino']]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(idx1, 'horse', "Testing that idx1 was assigned correctly.")

   myTests().main()


.. activecode:: ac17_1_6
   :language: python
   :autograde: unittest
   :practice: T

   **2.** Usando la indexación, recupere la cadena 'willow' de la lista y asígnela a la variable ``plant``.

   ~~~~

   data = ['bagel', 'cream cheese', 'breakfast', 'grits', 'eggs', 'bacon', [34, 9, 73, []], [['willow', 'birch', 'elm'], 'apple', 'peach', 'cherry']]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(plant, 'willow', "Testing that plant has the correct value.")

   myTests().main()

