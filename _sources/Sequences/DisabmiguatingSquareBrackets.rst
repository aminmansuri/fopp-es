..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: sequences-4-
   :start: 1

Disambiguating []: creación vs indexación
=========================================

Los corchetes ``[]`` se usan de muchas maneras en Python. Cuando esté aprendiendo cómo usarlos, puede ser
confuso, pero con práctica y repetición serán fáciles de incorporar.

Actualmente ha encontrado dos instancias en las que hemos utilizado corchetes cuadrados. Lo primero es crear listas y lo segundo
es si está indexando. A primera vista, crear e indexar son difíciles de distinguir. Sin embargo, la indexación requiere referencia
una lista ya creada mientras que simplemente crear una lista no lo hace.

.. activecode:: ac5_4_1

   new_lst = []

En el código anterior, se crea una nueva lista utilizando los corchetes vacíos. Sin embargo, como no hay nada en él, no podemos indexarlo.

.. activecode:: ac5_4_2

   new_lst = ["NFLX", "AMZN", "GOOGL", "DIS", "XOM"]
   part_of_new_lst = new_lst[0]

En el código anterior, verá cómo, ahora que tenemos elementos dentro de ``new_lst``, podemos indexarlo.
Para extraer un elemento de la lista, usamos ``[]``, pero primero tenemos que especificar qué lista estamos indexando.
Imagine si hubiera otra lista en el código activo.
¿Cómo sabría Python en qué lista queremos indexar si no lo decimos?
Además, tenemos que especificar qué elemento queremos extraer. Esto va dentro de los corchetes.

Aunque puede ser más fácil distinguir en este código activo anterior, a continuación puede ser un poco más difícil.

.. activecode:: ac5_4_3

   lst = [0]
   n_lst = lst[0]

   print(lst)
   print(n_lst)

Aquí, vemos una lista llamada ``lst`` que se asigna a una lista con un elemento, cero. Luego, vemos cómo se asigna ``n_lst``
El valor asociado con el primer elemento de lst. A pesar de los nombres de las variables, solo una de las variables anteriores es
asignada a una lista. Tenga en cuenta que en este ejemplo, lo que establece la creación aparte de la indexación es la referencia a la lista para permitir a
Python saber que se está extrayendo un elemento de otra lista.

.. mchoice:: question5_4_1
   :multiple_answers:
   :answer_a: w = [a]
   :answer_b: y = a[]
   :answer_c: x = [8]
   :answer_d: t = a[0]
   :feedback_a: No, debido a la forma en que se escribió el código, crea una lista. Esta lista tendría un elemento que es el valor asignado a la variable a.
   :feedback_b: Aunque esto intenta usar la indexación, no especifica qué elemento debe tomarse de a.
   :feedback_c: No, este es un ejemplo de creación de una lista.
   :feedback_d: Sí, esto usará la indexación para obtener el valor del primer elemento de a.
   :correct: d
   :practice: T

   ¿Cuál de los siguientes usa correctamente la indexación? Suponga que ``a`` es una lista o cadena. Selecciona todas las que apliquen.
