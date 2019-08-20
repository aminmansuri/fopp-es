..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: moreiter-1-
   :start: 1

.. index:: for loop
    iteration, assignment, assignment statement, reassignment
    single: statement; assignment

Introducción
============

Las computadoras a menudo se usan para automatizar tareas repetitivas. Repetir tareas idénticas o similares sin cometer
errores, es algo que las computadoras hacen bien y las personas hacen mal.

La ejecución repetida de una secuencia de declaraciones se llama **iteración**. Debido a que la iteración es tan común, Python
proporciona varias funciones de lenguaje para que sea más fácil. Ya hemos visto la declaración ``for`` en un capítulo anterior.
Esta es una forma muy común de iteración en Python. En este capítulo vamos a ver la declaración ``while``  ---
otra forma de hacer que su programa haga iteraciones.


Metas de aprendizaje
--------------------

* Comprender la iteración indefinida
* Resolver problemas de convergencia

Objetivos
----------

* Aplicar el ciclo while para iteración indefinida
* Poder identificar bucles while que probablemente sean bucles infinitos