..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: seqmut-6-
   :start: 1

Métodos Mutantes
=================

Ya has visto algunos métodos, como los métodos ``count`` e ``index``. Los métodos son
mutantes o no mutantes. Los métodos mutantes son aquellos que cambian el objeto después de que el método ha sido
usado. Los métodos no mutantes no cambian el objeto una vez que se ha utilizado el método.

Los métodos ``count`` e ``index`` no son mutantes. Count devuelve el número de ocurrencias del
argumento dado pero no cambia la cadena o lista original. Del mismo modo, el índice devuelve la
ocurrencia más a la izquierda del argumento pero no cambia la cadena o lista original. A continuación hablaremos
acerca de los métodos de list en general. ¡Esté atento a los métodos que están mutando!

Métodos de List
-----------------

El operador de puntos también se puede utilizar para acceder a métodos integrados de objetos de list.
``append`` es un método de list que agrega el argumento que se le pasa al final de
la lista. Continuando con este ejemplo, mostramos varios otros métodos de list. Muchos de ellos son
fáciles de entender.

.. activecode:: ac8_6_1

    mylist = []
    mylist.append(5)
    mylist.append(27)
    mylist.append(3)
    mylist.append(12)
    print(mylist)

    mylist.insert(1, 12)
    print(mylist)
    print(mylist.count(12))

    print(mylist.index(3))
    print(mylist.count(5))

    mylist.reverse()
    print(mylist)

    mylist.sort()
    print(mylist)

    mylist.remove(5)
    print(mylist)

    lastitem = mylist.pop()
    print(lastitem)
    print(mylist)

Hay dos formas de usar el método ``pop``. El primero, sin parámetro, eliminará y devolverá el
Último elemento de la lista. Si proporciona un parámetro para la posición, ``pop`` eliminará y devolverá el
artículo en esa posición. De cualquier manera, la lista cambia.

La siguiente tabla proporciona un resumen de los métodos de lista que se muestran arriba. La columna etiquetada como
``resultado`` da una explicación de cuál es el valor de retorno en relación con el nuevo valor de la lista.
La palabra **mutator** significa que el método cambia la lista pero no se devuelve nada (en realidad se devuelve
``None``). Un método **hybrid** es uno que no solo cambia la lista sino que también devuelve un
valor como resultado. Finalmente, si el resultado es simplemente un retorno, entonces la lista no fue cambiada por el
método.

Asegúrese de experimentar con estos métodos para comprender mejor lo que hacen.



==========  ==============  ============  ================================================
Método      Parámetros       Resultado    Description
==========  ==============  ============  ================================================
append      item            mutator       Agrega un nuevo elemento al final de una lista
insert      position, item  mutator       Inserta un nuevo elemento en la posición dada
pop         none            hybrid        Elimina y devuelve el último artículo.
pop         position        hybrid        Elimina y devuelve el artículo en su posición.
sort        none            mutator       Modifica una lista para ordenarla
reverse     none            mutator       Modifica una lista para estar en orden inverso
index       item            return idx    Devuelve la posición de la primera aparición del artículo.
count       item            return ct     Devuelve el número de ocurrencias del artículo.
remove      item            mutator       Elimina la primera aparición del artículo.
==========  ==============  ============  ================================================


Los detalles para estos y otros se pueden encontrar en el
`Python Documentation <http://docs.python.org/py3k/library/stdtypes.html#sequence-types-str-bytes-bytearray-list-tuple-range>`_.

Es importante recordar que métodos como ``append``, ``sort`` y ``reverse`` devuelven todos
``None``. Cambian la lista; No producen una nueva lista. Entonces, mientras realizamos la reasignación
para incrementar un número, como en ``x = x + 1``, haciendo lo análogo con estas operaciones perderá
todo el contenido de la lista (ver la línea 8 a continuación).

.. activecode:: ac8_6_2

    mylist = []
    mylist.append(5)
    mylist.append(27)
    mylist.append(3)
    mylist.append(12)
    print(mylist)

    mylist = mylist.sort()   #probably an error
    print(mylist)

**Revisa tu entendimiento**

.. mchoice:: question8_6_1
   :answer_a: [4,2,8,6,5,False,True]
   :answer_b: [4,2,8,6,5,True,False]
   :answer_c: [True,False,4,2,8,6,5]
   :correct: b
   :feedback_a: Primero se agregó True, luego se agregó False al final.
   :feedback_b: Sí, cada elemento se agrega al final de la lista.
   :feedback_c: append agrega al final, no al principio.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?
   
   .. code-block:: python

     alist = [4,2,8,6,5]
     alist.append(True)
     alist.append(False)
     print(alist)
