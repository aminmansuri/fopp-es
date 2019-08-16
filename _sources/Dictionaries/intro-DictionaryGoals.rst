..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. index:: dictionary, mapping type, key-value pair
   single: [ ]; dictionary access
   value; dictionary

.. qnum::
   :prefix: dictionaries-1-
   :start: 1

Introducción: Diccionarios
===========================

Los tipos de datos compuestos que hemos estudiado en detalle hasta ahora (cadenas y listas) son colecciones secuenciales. Esto significa que los elementos de la colección están ordenados de izquierda a derecha y usan números enteros como índices para acceder a los valores que contienen. Esto también significa que buscar un valor particular requiere escanear los muchos elementos de la lista hasta que encuentre el valor deseado.

Los datos a veces se pueden organizar de manera más útil asociando una clave con el valor que estamos buscando. Por ejemplo, si se le solicita el número de página para el comienzo del capítulo 5 en un libro de texto grande, puede hojear el libro buscando el título del capítulo 5. Si el número de capítulo aparece en el encabezado o pie de página de cada página, es posible que pueda encontrar el número de página con bastante rapidez, pero generalmente es más fácil y rápido ir a la página de índice y ver que el capítulo 5 comienza en la página 78.

Este tipo de búsqueda directa de un valor en Python se realiza con un objeto llamado Diccionario. Los diccionarios son un tipo diferente de colección. Son el tipo **mapping** incorporado de Python. Un mapa es una colección asociativa no ordenada. La asociación, o mapeo, es de una **clave**, que puede ser de cualquier tipo inmutable (por ejemplo, el nombre y número del capítulo en la analogía anterior), a un **valor** (el número de la página de inicio), que puede ser cualquier objeto de datos de Python. Aprenderá a usar estas colecciones en el siguiente capítulo.


Metas de Aprendizaje
---------------------

* Introducir la idea de pares clave, valor
* Introducir la idea de una secuencia desordenada
* Comprender el uso de la construcción paralela en listas
* Para comprender el beneficio de rendimiento y la simplicidad de un diccionario en listas paralelas
* Para comprender que la iteración del diccionario itera sobre las teclas

Objectivos
----------

Para utilizar correctamente lo siguiente:

* El operador index para agregar un par clave-valor a un diccionario
* El operador del para eliminar una entrada
* operador de index -  recuperación por clave
* search - contiene in / not in
* items
* claves
* valores
* get - con un valor predeterminado
