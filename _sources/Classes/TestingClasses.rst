..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: test-3-
   :start: 1

Clases de prueba
------------------

.. note::

    Esta página depende del uso del módulo de prueba, que se presenta en:ref:`the testing chapter <test_cases_chap>`. Si aún no ha cubierto ese capítulo, querrá retrasar la lectura de esta página hasta que lo haga.

Para probar una clase definida por el usuario, creará casos de prueba que verifiquen si las instancias se crean correctamente, y
crear casos de prueba para cada uno de los métodos como funciones, invocandolos en instancias particulares y viendo si
producen los valores de retorno correctos y los efectos secundarios, especialmente los efectos secundarios que cambian los datos almacenados en la ivariable de
nstancia. Para ilustrar, usaremos la clase Point que se usó en la introducción a las clases.

Para probar si el método del constructor de clases (el ``__init__``) funciona correctamente, cree una instancia y luego haga la
prueba para ver si sus variables de instancia están establecidas correctamente. Tenga en cuenta que esta es una prueba de efectos secundarios: el constructor.
El trabajo del método es establecer variables de instancia, que es un efecto secundario. Su valor de retorno no importa.

Un método como ``distanceFromOrigin`` en la clase ``Point`` hace su trabajo calculando un valor de retorno, por lo que
necesita ser probado con una prueba de valor de retorno. Un método como ``move`` en la clase ``Turtle`` hace su trabajo cambiando el
contenido de un objeto mutable (la instancia de punto tiene su variable de instancia modificada) por lo que debe probarse con un lado
prueba de efecto.

Intente agregar algunas pruebas más en el código a continuación, una vez que comprenda lo que hay allí.

.. activecode:: ac19_3_1

    class Point:
        """ Clase de punto para representar y manipular coordenadas x, y. """
   
        def __init__(self, initX, initY):
   
            self.x = initX
            self.y = initY
   
        def distanceFromOrigin(self):
            return ((self.x ** 2) + (self.y ** 2)) ** 0.5
   
        def move(self, dx, dy):
            self.x = self.x + dx
            self.y = self.y + dy

    import test

    #constructor de clase de prueba (__init__ method)
    p = Point(3, 4)
    test.testEqual(p.y, 4)
    test.testEqual(p.x, 3)

    #probando el método de distancia
    p = Point(3, 4)
    test.testEqual(p.distanceFromOrigin(), 5.0)

    #probar el método de movimiento
    p = Point(3, 4)
    p.move(-2, 3)
    test.testEqual(p.x, 1)
    test.testEqual(p.y, 7)

**Revisa tu entendimiento**

.. mchoice:: question19_3_1
   :practice: T
   :answer_a: True
   :answer_b: False
   :correct: b
   :feedback_a: Cada caso de prueba verifica si la función funciona correctamente en una entrada. Es una buena idea verificar varias entradas diferentes, incluidos algunos casos extremos.
   :feedback_b: Es una buena idea verificar algunos casos extremos, así como los casos típicos.

   Para cada función, debe crear exactamente un caso de prueba.
 
.. mchoice:: question19_3_2
   :practice: T
   :answer_a: Prueba de valor de retorno
   :answer_b: prueba de efectos secundarios
   :correct: b
   :feedback_a: El método puede devolver el valor correcto pero no cambiar adecuadamente los valores de las variables de instancia. Vea el método de movimiento de la clase Point arriba.
   :feedback_b: El método de movimiento de la clase Point anterior es un buen ejemplo.

   Para probar un método que cambia el valor de una variable de instancia, ¿qué tipo de caso de prueba debe escribir?

.. mchoice:: question19_3_3
   :practice: T
   :answer_a: Prueba de valor de retorno
   :answer_b: Prueba de efectos secundarios
   :correct: a
   :feedback_a: Desea verificar si maxabs devuelve el valor correcto para alguna entrada.
   :feedback_b: La función no tiene efectos secundarios; aunque toma una lista L como parámetro, no altera su contenido.

   Para probar la función maxabs, ¿qué tipo de caso de prueba debería escribir?

   .. sourcecode:: python
   
      def maxabs(L):
         """L should be a list of numbers (ints or floats). The return value should be the maximum absolute value of the numbers in L."""
         return max(L, key=abs)

.. mchoice:: question19_3_4
   :practice: T
   :answer_a: Prueba de valor de retorno
   :answer_b: Prueba de efectos secundarios
   :correct: b
   :feedback_a: El método de clasificación siempre devuelve None, por lo que no hay nada que verificar si está devolviendo el valor correcto.
   :feedback_b: Desea verificar si tiene el efecto secundario correcto, si muta correctamente la lista.

   Por lo general, hemos utilizado la función ``sorted``, que toma una lista como entrada y devuelve una nueva lista que contiene los mismos elementos, posiblemente en un orden diferente. También hay un método llamado ``sort`` para las listas (por ejemplo, ``[1,6,2,4].sort()``). Cambia el orden de los elementos en la lista y devuelve el valor ``None``. ¿Qué tipo de caso de prueba usarías en el método de clasificación?
