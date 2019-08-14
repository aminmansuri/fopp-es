..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: seqmut-3-
   :start: 1

.. index:: aliases

Objectos y Referencias
-----------------------

Si ejecutamos estas declaraciones de asignación,

.. sourcecode:: python
    
    a = "banana"
    b = "banana"

sabemos que ``a`` y ``b`` se referirán a una cadena con las letras
``"banana"``. Pero aún no sabemos si apuntan a la *misma* cadena.

Hay dos formas posibles en que el intérprete de Python podría organizar sus estados internos:

.. image:: Figures/refdiag1.png
   :alt: List illustration 

o

.. image:: Figures/refdiag2.png
   :alt: List illustration

En un caso, ``a`` y ``b`` se refieren a dos objetos strings diferentes que tienen el mismo
valor. En el segundo caso, se refieren al mismo objeto. Recuerde que un objeto es algo a lo que una variable puede
referirse.

Podemos probar si dos nombres se refieren al mismo objeto usando *is*
operador. El operador *is* devolverá verdadero si las dos referencias son al mismo objeto. En otras palabras, las referencias son las mismas. Pruebe nuestro ejemplo de arriba.

.. activecode:: ac8_3_1

    a = "banana"
    b = "banana"

    print(a is b)

La respuesta es ``True``. Esto nos dice que tanto ``a`` como ``b`` se refieren al mismo objeto, y que es el segundo
de los dos diagramas de referencia que describen la relación. Python asigna a cada objeto una identificación única y cuando
pregunte ``a is b`` lo que realmente está haciendo Python es verificar si se cumple que id(a) == id(b).

.. activecode:: ac8_3_2

    a = "banana"
    b = "banana"

    print(id(a))
    print(id(b))

Como las cadenas son *inmutables*, el intérprete de Python a menudo optimiza los recursos al hacer que dos nombres que se refieren al mismo valor de String
se referiran al mismo objeto. No debe contar con esto (es decir, use ``==`` para comparar cadenas, no ``is``), pero no se sorprenda si encuentra que dos variables, cada una unida a la cadena "banana", tiene la misma identificación ..

Este no es el caso con las listas, que nunca comparten una identificación solo porque tienen el mismo contenido. Considere el siguiente ejemplo. Aquí, ``a`` y ``b`` se refieren a dos listas diferentes,
cada uno de los cuales tiene los mismos valores de elementos. Necesitan tener identificadores diferentes para que las mutaciones de la lista ``a`` no afecten a la lista ``b``.

.. activecode:: ac8_3_3
    
    a = [81,82,83]
    b = [81,82,83]

    print(a is b)

    print(a == b)

    print(id(a))
    print(id(b))

El diagrama de referencia para este ejemplo se ve así:

.. image:: Figures/refdiag3.png
   :alt: Reference diagram for equal different lists 

``a`` y ``b`` tienen valores equivalentes pero no se refieren al mismo objeto. Como sus contenidos son equivalentes, `a==b` se evalúa como Verdadero; porque no son el mismo objeto, `a es b` se evalúa como Falso.
