..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: seqmut-1-
   :start: 1

Introducción: Transformando Secuencias
=======================================

Las secuencias que hemos usado hasta ahora han sido estáticas: una lista de colores que no cambia o los caracteres en una cadena que permanece igual.
El mundo real es más complicado que eso. Una lista de usuarios para su red social puede necesitar crecer para acomodar a nuevos usuarios (o reducirse cuando los usuarios dejan su servicio). Es posible que las letras de una cadena deban modificarse para personalizar un mensaje ("Bienvenido a Wonderland, <su nombre>") o para codificar un mensaje secreto.

El siguiente capítulo detallará más de los métodos que se pueden usar para transformar listas y cadenas. Generalmente, los dos métodos que se pueden usar están cambiando el objeto de la lista, en su lugar, al mutarlo; o construyendo un nuevo objeto de cadena usando una operación de copiar con cambio.


Metas de aprendizaje
---------------------

* Comprender los conceptos de tipos de datos mutables e inmutables.
* Para comprender que los métodos en cadenas dejan solo la cadena original pero devuelven una nueva cadena
* Entender que las listas son tipos de datos mutables y que los métodos de mutación en las listas devuelven Ninguno

Objectivos
----------

Demostrar el uso correcto de:

* concatenación
* operador index
* subcadenas (slice)
* búsquedas - contains in / not in and index
* método find
* append
* join
* split
* método string format