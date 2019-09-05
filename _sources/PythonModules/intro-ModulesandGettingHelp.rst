..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: modules-1-
   :start: 1

.. index:: documentation online, Global Module Index
   module; standard, namespace

Módulos
=======

.. youtube:: GCLHuPBtLdQ
    :divid: vid_modules
    :height: 315
    :width: 560
    :align: left

Un **módulo** es un archivo que contiene definiciones y sentencias de Python destinadas a
usar en otros programas de Python. Hay muchos módulos de Python que vienen con
Python como parte de la **biblioteca estándar**. Proporcionar funcionalidad adicional a través de módulos le permite usar solo la funcionalidad que necesita cuando la necesita, y mantiene su código más limpio.

Las funciones importadas como parte de un módulo viven en su propio **espacio de nombres**. Un espacio de nombres es simplemente un espacio dentro del cual todos los nombres son distintos entre sí. El mismo nombre se puede reutilizar en diferentes espacios de nombres, pero dos objetos no pueden tener el mismo nombre dentro de un solo espacio de nombres. Un ejemplo de un espacio de nombres es el conjunto de nombres de calles dentro de una sola ciudad. Muchas ciudades tienen una calle llamada "Calle principal", ¡pero es muy confuso si dos calles de la misma ciudad tienen ese nombre! Otro ejemplo es la organización de carpetas de los sistemas de archivos. Puede tener un archivo llamado todo en su carpeta de trabajo, así como en su carpeta personal, pero sabe cuál es cuál debido a la carpeta en la que se encuentra; cada carpeta tiene su propio espacio de nombres para archivos. Tenga en cuenta que los nombres humanos no son parte de un espacio de nombres que impone la unicidad; Es por eso que los gobiernos han inventado identificadores únicos para asignar a las personas, como los números de pasaporte.

El  sitio de  `documentación de Python <https://docs.python.org/3.6/>`_ para la versión de Python
3.6 es una referencia extremadamente útil de todos los aspectos de Python. El sitio
contiene una lista de todos los módulos estándar que están disponibles con Python
(mire `Global Module Index <https://docs.python.org/3.6/py-modindex.html>`_). También
verá que hay una
`Referencia de Librería Estándar <https://docs.python.org/3.6/library/index.html>`_
y un `Tutorial <https://docs.python.org/3.6/tutorial/index.html>`_ tanto como
instrucciones de instalación, instrucciones y preguntas frecuentes. Nosotros
le recomendamos que se familiarice con este sitio y que lo use con frecuencia.

Si aún no lo ha hecho, eche un vistazo al Índice del módulo global. aquí
verá una lista alfabética de todos los módulos que están disponibles como
parte de la biblioteca estándar. Encuentre el módulo de turtle.

Importando Módulos
------------------

Para usar los módulos de Python, debe **importarlos** a un programa de Python. Eso pasa con una importación
sentencia: la palabra ``import`` y luego el *nombre del módulo*. El nombre distingue entre mayúsculas y minúsculas. En palabras más sencillas,
una sentencia de importación dice "hay algún código en otro archivo; por favor haga sus funciones y variables
disponible en este archivo ". Más técnicamente, una sentencia de importación hace que se ejecute todo el código en otro archivo. Cualquiera
de las variables que están vinculadas durante esa ejecución (incluidas las funciones que están definidas) pueden referirse de alguna manera
(para ser tratadas) en el archivo actual.

Por convención, todos los comandos de ``import`` se colocan en la parte superior de su archivo. Se pueden poner en otro lugar, pero eso puede
conducir a algunas confusiones, por lo que es mejor seguir la convención.

¿De dónde vienen estos otros archivos que puede importar? Podría ser un archivo de código que usted mismo escribió, o podría
sea el código que alguien más escribió y que copió en su computadora.

Por ejemplo, si tiene un archivo ``myprog.py`` en el directorio ``~/Desktop/mycode/``, y myprog.py contiene una línea de
código ``import morecode``, entonces el intérprete de Python buscará un archivo llamado ``morecode.py``, ejecutará su código,
y hará que sus enlaces de objetos estén disponibles para referencia en el resto del código en myprog.py.

Tenga en cuenta que es ``import morecode``, no ``import morecode.py``, pero el otro archivo debe llamarse ``morecode.py``.

Las pruebas que ve en sus conjuntos de problemas también utilizan un módulo Python que se encuentra en la biblioteca estándar, llamado
``unittest``. En este momento, no puede ver el código que hace que se ejecuten esas pruebas, porque se lo hemos ocultado,
pero más adelante en el curso, aprenderá cómo escribir sus propios Unit Tests y para hacerlo, necesitará
escribir una sentencia de importación al comienzo de sus programas. Incluso antes de aprender a escribir sus propios exámenes, usted
verá el código para Unit Test en los archivos de conjunto de problemas.

.. admonition:: ¡No sobrescriba los módulos de biblioteca estándar!

    Dado el orden de búsqueda de módulos externos de Python que se describe en la lista anterior, es posible
    sobrescribir una biblioteca estándar. Por ejemplo, si crea un archivo ``random.py`` en el mismo directorio donde
    ``myprog.py`` vive, y luego myprog.py invoca ``import random``, importará *su* archivo en lugar de
    Módulo de biblioteca estándar. Por lo general, eso no es lo que quieres, ¡así que ten cuidado con cómo nombras tus archivos de Python!


Sintaxis para Importar Módulos y Funcionalidad
----------------------------------------------

Cuando ve módulos importados en un programa Python, hay algunas variaciones que tienen consecuencias ligeramente diferentes.

1. El más común es ``import morecode``. Eso importa todo en morecode.py. Para invocar una función f1 que se define en morecode.py, escribiría ``morecode.f1()``. Tenga en cuenta que debe mencionar explícitamente morecode nuevamente, para especificar que desea la función f1 del espacio de nombres morecode. Si solo escribe ``f1()``, python buscará un f1 que se definió en el archivo actual, en lugar de en morecode.py.

2. También puede asignar un alias al módulo importado (un nombre diferente, solo para cuando lo usa en su programa). Por ejemplo, después de ejecutar ``import morecode as mc``, invocaría ``f1`` como ``mc.f1()``. Ahora le ha dado al módulo ``morecode`` el alias ``mc``. Los programadores a menudo hacen esto para hacer que el código sea más fácil de escribir.

3. Una tercera posibilidad de importación se produce cuando solo desea importar ALGUNAS de las funciones de un módulo y desea que esos objetos formen parte del espacio de nombres del módulo actual. Por ejemplo, podría escribir ``from morecode import f1``. Entonces podría invocar f1 sin hacer referencia a morecode nuevamente: ``f1()``.


.. admonition:: Nota: módulos de Python y limitaciones con active code

   A lo largo de los capítulos de este libro, las ventanas de active code le permiten practicar el Python que está aprendiendo.
   Mencionamos en el primer capítulo que la programación normalmente se realiza utilizando algún tipo de ambiente de desarrollo.
   (IDE) y que el
   active code utilizado aquí fue estrictamente creado para ayudarnos a aprender. No es la forma en que escribimos programas de producción.

   Para ello, es necesario mencionar que muchos de los módulos disponibles en Python estándar
   **no** funcionarán en el entorno de active code. De hecho, solo ``turtle``, ``math``, ``random`` y un par más han sido
   portados en este punto. Si desea explorar algunos
   módulos adicionales, deberá ejecutarlos desde el intérprete de python nativo en su computadora.

**Revisa tu entendimiento**

.. mchoice:: question13_1_1
   :answer_a: Un archivo que contiene definiciones y sentencias de Python destinadas a su uso en otros programas de Python.
   :answer_b: Un bloque de código separado dentro de un programa.
   :answer_c: Una línea de código en un programa.
   :answer_d: un archivo que contiene documentación sobre funciones en Python.
   :correct: a
   :feedback_a: un módulo se puede reutilizar en diferentes programas.
   :feedback_b: Si bien un módulo es un bloque de código separado, está separado de un programa.
   :feedback_c: la llamada a una función dentro de un módulo puede ser una línea de código, pero los módulos suelen ser varias líneas de código separadas del programa.
   :feedback_d: cada módulo tiene su propia documentación, pero el módulo en sí es más que solo documentación.

   En Python un módulo es:

.. mchoice:: question13_1_2
   :answer_a: Ir al sitio de documentación de Python.
   :answer_b: Mirar las sentencias de importación del programa con el que está trabajando o escribiendo.
   :answer_c: Preguntar al Profesor.
   :answer_d: Mirar en este libro.
   :correct: a
   :feedback_a: El sitio contiene una lista de todos los módulos estándar que están disponibles con Python.
   :feedback_b: Las sentencias de importación solo le dicen qué módulos se están utilizando actualmente en el programa, no cómo usarlos o qué contienen.
   :feedback_c: Si bien el profesor conoce un subconjunto de los módulos disponibles en Python, es probable que el profesor tenga que buscar los módulos disponibles como lo haría usted.
   :feedback_d: Este libro solo explica una parte de los módulos disponibles. Para obtener una lista completa, debe buscar en otro lado.

   Para obtener información sobre los módulos estándar disponibles con Python, debe:

.. mchoice:: question13_1_3
   :answer_a: Verdadero
   :answer_b: Falso
   :correct: b
   :feedback_a: Solo algunos módulos se han portado para trabajar en código activo en este momento.
   :feedback_b: Solo algunos módulos se han portado para trabajar en código activo en este momento.

   Verdadero/Falso: Todos los módulos estándar en Python funcionarán en active code.

