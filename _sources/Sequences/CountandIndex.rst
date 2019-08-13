..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: sequences-8-
   :start: 1

Count e Index
===============

A medida que crea programas más complejos, encontrará que algunas tareas se realizan comúnmente. Python tiene algunas
funciones y métodos integrados para ayudarlo con estas tareas. Esta página cubrirá dos métodos útiles,
tanto para cadenas como para listas: count e index.

Aprendiste sobre métodos antes cuando dibujaste con el módulo de tortuga. Ahí solías usar
``.forward(50)`` y ``.color("purple")`` para completar acciones. Nos referimos al avance y al color como métodos
de la clase de tortuga. Los objetos como cadenas y listas también tienen métodos que podemos usar.

Count
-----

El primer método del que hablaremos se llama ``count``. Requiere que proporciones un argumento, que
es lo que te gustaría contar. El método luego devuelve el número de veces que ocurrió el argumento
en la cadena/lista en la que se utilizó el método. Hay algunas diferencias entre el recuento de cadenas y
cuenta para las listas. Cuando usa count en una cadena, el argumento solo puede ser una cadena. No puedes contar cómo
muchas veces el entero 2 aparece en una cadena, aunque puede contar cuántas veces aparece la cadena "2"
en una cuerda para las listas, el argumento no se limita a solo cadenas.

.. activecode:: ac5_8_1
   
   a = "¡He tenido una manzana en mi escritorio antes!"
   print(a.count("e"))
   print(a.count("ha"))

La ventana de código activo anterior muestra el uso de count en una cadena. Al igual que con el módulo de tortuga
cuando tuvimos que especificar qué tortuga estaba cambiando de color o moviéndose, tenemos que especificar de qué cadena somos
usando count.

.. activecode:: ac5_8_2
   
   z = ['atoms', 4, 'neutron', 6, 'proton', 4, 'electron', 4, 'electron', 'atoms']
   print(z.count("4"))
   print(z.count(4))
   print(z.count("a"))
   print(z.count("electron"))

Cuando ejecute la ventana de código activo anterior, verá cómo funciona contar con una lista. Observe cómo "4" tiene un
cuenta de cero pero 4 tiene una cuenta de tres? Esto se debe a que la lista ``z`` solo contiene el número entero 4.
Nunca hay cadenas que sean 4. Además, cuando verificamos el recuento de "a", vemos que el
programa devuelve cero. Aunque algunas de las palabras en la lista contienen la letra "a", el programa es
buscando elementos en la lista que son *solo* la letra "a".

Index
-----

El otro método que puede ser útil tanto para las cadenas como para las listas es el método ``index``. El ``index``
es un que método requiere un argumento y, al igual que el método ``count``, solo toma cadenas cuando se usa el índice
en cadenas y cualquier tipo cuando se usa en listas. Para ambas cadenas y listas, ``index`` devuelve el
índice más a la izquierda donde se encuentra el argumento. Si no puede encontrar el argumento en la cadena o lista,
entonces se producirá un error.

.. activecode:: ac5_8_3

   music = "Pull out your music and dancing can begin"
   bio = ["Metatarsal", "Metatarsal", "Fibula", [], "Tibia", "Tibia", 43, "Femur", "Occipital", "Metatarsal"]

   print(music.index("m"))
   print(music.index("your"))

   print(bio.index("Metatarsal"))
   print(bio.index([]))
   print(bio.index(43))

Todos los ejemplos anteriores funcionan, pero ¿te sorprendió alguno de los valores de retorno? Recuérdalo
``index`` devolverá el índice más a la izquierda del argumento. A pesar de que "Metatarsal" ocurre muchas veces
en ``bio``, el método solo devolverá la ubicación de uno de ellos.

Aquí hay otro ejemplo.

.. activecode:: ac5_8_4

   seasons = ["winter", "spring", "summer", "fall"]

   print(seasons.index("autumn"))  #Error! 

En la ventana de código activo de arriba, estamos tratando de ver dónde está "otoño" en la lista de estaciones. Sin embargo,
no hay una cadena llamada otoño (aunque hay una cadena llamada "otoño", que probablemente sea lo que el programa
está buscando). Recuerde que se produce un error si el argumento no está en la cadena o lista.

**Revisa tu entendimiento**

.. mchoice:: question5_8_1
   :answer_a: 5
   :answer_b: 6
   :answer_c: 13
   :answer_d: 14
   :answer_e: Hay un error.
   :correct: a
   :feedback_a: Sí, cuando obtenemos el índice de una cadena que tiene más de un carácter, obtenemos el índice del primer carácter de la cadena.
   :feedback_b: Cuando obtenemos el índice de una cadena que tiene más de un carácter, obtenemos el índice del primer carácter de la cadena.
   :feedback_c: Recuerde que el índice devuelve la ocurrencia más a la izquierda del argumento.
   :feedback_d: Recuerde que el índice devuelve la ocurrencia más a la izquierda del argumento.
   :feedback_e: Hay al menos un 'nosotros' en la cadena asignada a qu.
   :practice: T

   ¿Qué se almacenará en la variable ty a continuación?

   .. sourcecode:: python

      qu = "wow, welcome week!"
      ty = qu.index("we")

.. mchoice:: question5_8_2
   :answer_a: 0
   :answer_b: 2
   :answer_c: 3
   :answer_d: Hay un error.
   :correct: b
   :feedback_a: No, hay al menos una e en la cadena.
   :feedback_b: Sí, hay una diferencia entre "nosotros" y "Nosotros", lo que significa que solo hay dos en la cadena.
   :feedback_c: Hay una diferencia entre "nosotros" y "nosotros".
   :feedback_d: No hay error en el código.
   :practice: T

   ¿Qué se almacenará en la variable ty a continuación?

   .. sourcecode:: python

      qu = "wow, welcome week! Were you wanting to go?"
      ty = qu.count("we")

.. mchoice:: question5_8_3
   :answer_a: 0
   :answer_b: -1
   :answer_c: Hay un error.
   :correct: c
   :feedback_a: No, el primer elemento es 'baño', no 'jardín'.
   :feedback_b: Aunque no hay un 'jardín' en la lista, no recuperamos -1 cuando usamos index. En cambio, recibimos un error.
   :feedback_c: Sí, no hay 'jardín' en la lista, por lo que recibimos un error.
   :practice: T

   ¿Qué se almacenará en la variable ht a continuación?

   .. sourcecode:: python

      rooms = ['bathroom', 'kitchen', 'living room', 'bedroom', 'closet', "foyer"]
      ht = rooms.index("garden")
