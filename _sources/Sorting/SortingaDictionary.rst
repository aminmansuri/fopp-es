..  Copyright (C)  Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. _sort_dictionaries:

.. qnum::
   :prefix: sort-4-
   :start: 1

Ordenar un diccionario
----------------------

Anteriormente, ha utilizado un diccionario para acumular recuentos, como las frecuencias de letras o palabras en un texto.
Por ejemplo, el siguiente código cuenta las frecuencias de diferentes números en la lista.

.. activecode:: ac18_4_1

    L = ['E', 'F', 'B', 'A', 'D', 'I', 'I', 'C', 'B', 'A', 'D', 'D', 'E', 'D']

    d = {}
    for x in L:
        if x in d:
            d[x] = d[x] + 1
        else:
            d[x] = 1
    for x in d.keys():
        print("{} aparece {} veces".format(x, d[x]))

Las claves del diccionario no están ordenadas en ningún orden en particular. De hecho, puede obtener un orden de salida diferente si
alguien más ejecuta el mismo código. Podemos forzar que los resultados se muestren en un orden fijo, ordenando las claves.

.. activecode:: ac18_4_2

    L = ['E', 'F', 'B', 'A', 'D', 'I', 'I', 'C', 'B', 'A', 'D', 'D', 'E', 'D']

    d = {}
    for x in L:
        if x in d:
            d[x] = d[x] + 1
        else:
            d[x] = 1
    y = sorted(d.keys())
    for k in y:
        print("{} aparece {} veces".format(k, d[k]))


Con un diccionario que mantiene recuentos o algún otro tipo de puntaje, podríamos preferir ordenar los resultados según
el recuento en lugar de basarse en los elementos. La forma estándar de hacerlo en python es ordenar en función de una propiedad de la clave, en particular su valor en el diccionario.

Aquí las cosas se vuelven un poco confusas porque tenemos dos significados diferentes de la palabra "clave". Un significado es una clave en un diccionario. El otro significado es el nombre del parámetro para la función que pasa a la función ordenada.

Recuerde que la función de tecla siempre toma como entrada un elemento de la secuencia y devuelve una propiedad del elemento. En nuestro caso, los elementos que se ordenarán son las claves del diccionario, por lo que cada elemento es una clave del diccionario. Para recordar eso, hemos nombrado el parámetro en la expresión lambda *k*. La propiedad de la clave k que se debe devolver es su valor asociado en el diccionario. Por lo tanto, tenemos la expresión lambda  ``lambda k: d[k]``.

.. activecode:: ac18_4_5

    L = ['E', 'F', 'B', 'A', 'D', 'I', 'I', 'C', 'B', 'A', 'D', 'D', 'E', 'D']
    
    d = {}
    for x in L:
        if x in d:
            d[x] = d[x] + 1
        else:
            d[x] = 1
    
    y = sorted(d.keys(), key=lambda k: d[k], reverse=True)
    for k in y:
        print("{} aparece {} veces".format(k, d[k]))

Aquí hay una versión de eso usando una función con nombre.

.. activecode:: ac18_4_6

    L = ['E', 'F', 'B', 'A', 'D', 'I', 'I', 'C', 'B', 'A', 'D', 'D', 'E', 'D']

    d = {}
    for x in L:
        if x in d:
            d[x] = d[x] + 1
        else:
            d[x] = 1
    
    def g(k):
        return d[k]

    y =(sorted(d.keys(), key=g, reverse=True))
    
    # ahora recorre las teclas
    for k in y:
        print("{} aparece {} veces".format(k, d[k]))

.. note::

   Cuando ordenamos las teclas, pasar una función con ``key=lambda x: d[x]`` no especifica que se ordenen las teclas de un
   diccionario. Las listas de claves se pasan como el primer valor de parámetro en la invocación de ordenación. El parámetro clave
   proporciona una función que dice *cómo* ordenarlos.


Un programador experimentado probablemente ni siquiera separará el paso de clasificación. Y
podrían aprovechar el hecho de que cuando pasas un diccionario a algo
eso es esperar una lista, es lo mismo que pasar la lista de claves.

.. activecode:: ac18_4_7

  L = ['E', 'F', 'B', 'A', 'D', 'I', 'I', 'C', 'B', 'A', 'D', 'D', 'E', 'D']

  d = {}
  for x in L:
      if x in d:
          d[x] = d[x] + 1
      else:
          d[x] = 1
      
  # ahora recorre las teclas ordenadas
  for k in sorted(d, key=lambda k: d[k], reverse=True):
        print("{} aparece {} veces".format(k, d[k]))

Eventualmente, podrá leer código así e inmediatamente sabrá lo que está haciendo. Por ahora, cuando venga
a través de algo confuso, como la línea 11, intente descomponerlo. Se invoca la función ``sorted``. Su primer valor en el parámetro
es un diccionario, lo que realmente significa las claves del diccionario. El tercer parámetro, la función clave, decora
la clave del diccionario con una nota post-it que contiene el valor de esa clave en el diccionario d. El último parámetro, True, dice que
ordena en orden inverso.

Hay otra forma de ordenar los diccionarios, llamando a .items () para extraer una secuencia de tuplas (clave, valor) y luego ordenando esa secuencia de tuplas. Pero es mejor aprender la forma pitónica de hacerlo, ordenando las teclas del diccionario usando una función de tecla que toma una tecla como entrada y busca el valor en el diccionario.
   
**Revisa tu entendimiento**

.. mchoice:: question18_4_1
   :multiple_answers:
   :answer_a: sorted(ks, key=g) 
   :answer_b: sorted(ks, key=lambda x: g(x, d))
   :answer_c: sorted(ks, key=lambda x: d[x])
   :correct: b,c
   :feedback_a: g es una función que toma dos parámetros. La función clave que se pasa a sorted siempre debe tomar solo un parámetro.
   :feedback_b: la función lambda toma solo un parámetro y llama a g con dos parámetros.
   :feedback_c: la función lambda busca el valor de x en d.
   :practice: T

   ¿Cuál de los siguientes ordenará las claves de d en orden ascendente de sus valores (es decir, de menor a mayor)?
   
   .. code-block:: python 

        L = [4, 5, 1, 0, 3, 8, 8, 2, 1, 0, 3, 3, 4, 3]
    
        d = {}
        for x in L:
            if x in d:
                d[x] = d[x] + 1
            else:
                d[x] = 1
        
        def g(k, d):
            return d[k]
            
        ks = d.keys()

.. activecode:: ac18_4_8
   :language: python
   :autograde: unittest
   :practice: T

   **2.** Ordene el siguiente diccionario según las claves para que se ordenen de la a a la z. Asigne el valor resultante a la variable ``sorted_keys``.
   ~~~~

   dictionary = {"Flowers": 10, 'Trees': 20, 'Chairs': 6, "Firepit": 1, 'Grill': 2, 'Lights': 14}

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(sorted_keys, sorted(dictionary), "Testing that sorted_keys has the correct value.")

   myTests().main()

.. activecode:: ac18_4_9
   :language: python
   :autograde: unittest
   :practice: T

   **3.** A continuación, proporcionamos el diccionario ``groceries``, cuyas claves son artículos de abarrotes, y los valores son el número de cada artículo que necesita comprar en la tienda. Ordene las claves del diccionario en orden alfabético y guárdelas como una lista llamada ``grocery_keys_sorted``.
   ~~~~

   groceries = {'apples': 5, 'pasta': 3, 'carrots': 12, 'orange juice': 2, 'bananas': 8, 'popcorn': 1, 'salsa': 3, 'cereal': 4, 'coffee': 5, 'granola bars': 15, 'onions': 7, 'rice': 1, 'peanut butter': 2, 'spinach': 9}

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(grocery_keys_sorted, ['apples', 'bananas', 'carrots', 'cereal', 'coffee', 'granola bars', 'onions', 'orange juice', 'pasta', 'peanut butter', 'popcorn', 'rice', 'salsa', 'spinach'], "Testing that grocery_keys_sorted was created correctly.")

   myTests().main()  

.. activecode:: ac18_4_10
   :language: python
   :autograde: unittest
   :practice: T

   **4.** Ordene las siguientes claves del diccionario según el valor de mayor a menor. Asigne el valor resultante a la variable ``sorted_values``.
   ~~~~

   dictionary = {"Flowers": 10, 'Trees': 20, 'Chairs': 6, "Firepit": 1, 'Grill': 2, 'Lights': 14}

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(sorted_values, sorted(dictionary, key=lambda x: dictionary[x], reverse = True), "Testing that sorted_values has the correct value.")

   myTests().main()
