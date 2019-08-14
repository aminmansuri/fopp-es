..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: seqmut-7-
   :start: 1

Append versus Concatenación
----------------------------

El método ``agregar`` agrega un nuevo elemento al final de una lista. También es posible agregar un nuevo elemento al final de una lista
mediante el uso del operador de concatenación. Sin embargo, debes tener cuidado.

Considere el siguiente ejemplo. La lista original tiene 3 enteros. Queremos agregar la palabra "gato" al final de la lista.

.. activecode:: clens8_7_1

    origlist = [45,32,88]

    origlist.append("cat")

Aquí hemos usado ``append`` que simplemente modifica la lista. Para usar la concatenación, necesitamos
escribir una declaración de asignación que use accumulator pattern::

    origlist = origlist + ["cat"]

Tenga en cuenta que la palabra "gato" debe colocarse en una lista ya que el operador de concatenación necesita dos listas
para hacer su trabajo

.. codelens:: clens8_7_2
    :python: py3

    origlist = [45,32,88]

    origlist = origlist + ["cat"]

También es importante darse cuenta de que con append, la lista original simplemente se modifica. Por otra parte,
con concatenación, se crea una lista completamente nueva. Esto se puede ver en el siguiente ejemplo de codelens
donde ``nueva lista`` se refiere a una lista que es una copia de la lista original, ``origlist``, con el nuevo elemento
"gato" añadido al final. ``origlist`` todavía contiene los tres valores que tenía antes de la concatenación.
Es por eso que la operación de asignación es necesaria como parte del patrón del acumulador.

.. codelens:: clens8_7_3
    :python: py3

    origlist = [45,32,88]

    newlist = origlist + ["cat"]

Esto puede ser difícil de entender ya que estas dos listas parecen ser las mismas. En Python, cada objeto
tiene una etiqueta de identificación única. Del mismo modo, hay una función incorporada que se puede invocar en cualquier objeto para devolver
su id única La función se llama apropiadamente ``id`` y toma un solo parámetro, el objeto que te interesa conocer.
Puede ver en el siguiente ejemplo que una identificación real suele ser un valor entero muy grande
(correspondiente a una dirección en la memoria). Aunque en el libro de texto, el número probablemente será menor.

.. sourcecode:: python

    >>> alist = [4, 5, 6]
    >>> id(alist)
    4300840544
    >>> 

.. activecode:: ac8_7_1

    origlist = [45,32,88]
    print("origlist:", origlist)
    print("the identifier:", id(origlist))             #id de la lista antes de los cambios
    newlist = origlist + ['cat'] 
    print("newlist:", newlist)   
    print("the identifier:", id(newlist))              #id de la listadespués de la concatenación
    origlist.append('cat')
    print("origlist:", origlist)
    print("the identifier:", id(origlist))             #id de la lista después de que append es usado

Tenga en cuenta que, aunque ``newlist`` y ``origlist`` parecen iguales, tienen identificadores diferentes.

Anteriormente hemos descrito `x += 1` como una abreviatura de `x = x + 1`. Con las listas, `+=` es en realidad un poco diferente. En particular, `origlist += ["cat"] agrega "cat" al final del objeto de lista original. Si hay otro alias para `origlist`, esto puede marcar la diferencia, como en el siguiente código. Vea si puede seguir (o, mejor aún, predecir cambios en el diagrama de referencia).

.. codelens:: clens8_7_2a
    :python: py3

    origlist = [45,32,88]
    aliaslist = origlist
    origlist += ["cat"]
    origlist = origlist + ["cow"]


Podemos usar append o concatenar repetidamente para crear nuevos objetos. Si tuviéramos una cadena y quisiéramos hacer una nueva lista, donde cada elemento de la lista es un carácter en la cadena, ¿dónde cree que debería comenzar? En ambos casos, primero deberá crear una variable para almacenar el nuevo objeto.

.. activecode:: ac8_72

    st = "Warmth"
    a = []

Luego, carácter por carácter, puede agregar a la lista vacía. El proceso se ve diferente si concatena en comparación con el uso de append.

.. activecode:: ac8_7_3

    st = "Warmth"
    a = []
    b = a + [st[0]]
    c = b + [st[1]]
    d = c + [st[2]]
    e = d + [st[3]]
    f = e + [st[4]]
    g = f + [st[5]]
    print(g)

.. activecode:: ac8_7_4

    st = "Warmth"
    a = []
    a.append(st[0]) 
    a.append(st[1])
    a.append(st[2])
    a.append(st[3])
    a.append(st[4])
    a.append(st[5])
    print(a)

Sin embargo, esto puede volverse tedioso y difícil si la longitud de la cadena es larga.
¿Puedes pensar en una mejor manera de hacer esto?

**Revisa tu entendimiento**

.. mchoice:: question8_7_1
   :answer_a: [4,2,8,6,5,999]
   :answer_b: Error, no puede concatenar una lista con un número entero.
   :correct: b
   :feedback_a: No puede concatenar una lista con un número entero.
   :feedback_b: Sí, para realizar la concatenación necesitaría escribir una lista+[999]. Debes tener dos listas.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?
   
   .. code-block:: python

     alist = [4,2,8,6,5]
     alist = alist + 999
     print(alist)
