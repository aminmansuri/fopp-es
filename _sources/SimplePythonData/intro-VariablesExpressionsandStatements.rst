..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. _simple_python_data:

.. qnum::
   :prefix: data-1-
   :start: 1

Introducción
============

.. index:: value, data type, string, integer, int, float, class, literal, output
    single: triple quoted string

.. _values_n_types:

.. video:: typesnconvert
    :controls:
    :thumb: ../_static/valuesNtypes.png

    http://media.interactivepython.org/thinkcsVideos/TypesNTypeConversion.mov
    http://media.interactivepython.org/thinkcsVideos/TypesNTypeConversion.webm

Este capítulo presenta varios componentes básicos de los programas Python:

- Literales, como números y cadenas de caracteres
- Operadores, como ``+`` y ``*``
- Llamadas a funciones, que toman valores como entradas y calculan nuevos valores
- Variables, que guardan valores para que puedan usarse más adelante en el programa

Estos son los componentes básicos que se ensamblan para crear programas con los que interactúa todos los días, desde el software que se ejecuta en su reloj inteligente, hasta la infraestructura detrás de los sitios web más grandes y cada aplicación que se ejecuta en su teléfono.

Metas de Aprendizaje
------------------------

* Para comprender el modelo de almacenamiento de Python
* Para resolver problemas usando el 'patrón acumulador'
* Para comprender la precedencia del operador
* Distinguir entre expresiones, valores y representaciones impresas.
* Para reconocer y explicar la codificación rígida


Objetivos
----------

* Dado un código de muestra, identifique las variables que hacen referencia a un objeto de un tipo particular
* Dada una variable de un tipo, conviértala en otra
* Simular evaluación de una expresión y declaración de asignación
* Utilice la reasignación para incrementar una variable (patrón acumulador)
* Obtenga la entrada de un usuario y convierta la entrada al tipo apropiado
* Identifique los siguientes tipos de valores: cadenas, enteros, flotantes, funciones
* Reconocer nombres de variables válidos vs inválidos
* Escribe una declaración de asignación
* Actualizar un diagrama de referencia después de la reasignación
