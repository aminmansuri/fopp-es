..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: sequences-1-
   :start: 1

Introducción: Secuencias
========================

En el mundo real, la mayoría de los datos que nos interesan no existen por sí solos. Por lo general, los datos tienen la forma de algún tipo de colección o secuencia. Por ejemplo, una lista de compras nos ayuda a realizar un seguimiento de los alimentos individuales que necesitamos comprar, y nuestra lista de tareas organiza las cosas que debemos hacer cada día. Tenga en cuenta que tanto la lista de la compra como la lista de tareas pendientes no se preocupan tanto por los números como por las palabras. Esto es cierto en gran parte de nuestra vida diaria, por lo que Python nos proporciona muchas funciones para trabajar con listas de todo tipo de objetos (números, palabras, etc.), así como un tipo especial de secuencia, la cadena de caracteres, que puede Piense como una secuencia de letras individuales.

Hasta ahora hemos visto tipos incorporados como: ``int``, ``float`` y ``str``.
``int`` y ``float`` se consideran tipos de datos simples o primitivos o atómicos porque
los valores no están compuestos de partes más pequeñas. No se pueden desglosar.

Por otro lado, las cadenas y las listas son diferentes de las demás porque
Se componen de piezas más pequeñas. En el caso de las cuerdas, están formadas por pequeños
cadenas cada una con un **caracter**.

Los tipos que se componen de piezas más pequeñas se denominan **tipos de datos de recopilación**.
Dependiendo de lo que estemos haciendo, es posible que queramos tratar un tipo de datos de recopilación como
entidad individual (el todo), o podemos querer acceder a sus partes. Esta ambigüedad es útil.

En este capítulo examinaremos las operaciones que se pueden realizar en secuencias, como seleccionar
a cabo elementos o subsecuencias individuales (llamados cortes) o calcular su longitud. Además, lo haremos
examinar algunas funciones especiales que se definen solo para cadenas, y descubriremos una importancia
diferencia entre cadenas y listas, que las listas se pueden cambiar (o mutar) mientras las cadenas son
inmutable.

Metas de aprendizaje
---------------------

* Para comprender las diferentes operaciones que se pueden realizar en cadenas, listas y tuplas
* Distinguir entre diferentes usos de [] en Python

Objetivos
----------

* Predecir la salida de las operaciones de división y unión
* Leer y escribir expresiones que usan cortes
* Leer y escribir expresiones que usan concatenación y repetición

