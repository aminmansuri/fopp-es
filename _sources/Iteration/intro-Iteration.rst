..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: iter-1-
   :start: 1

Introdución: Iteración
=======================

Un componente básico de todos los programas es poder repetir algún código una y otra vez.
Si está actualizando los saldos bancarios de millones de clientes cada noche, o enviando mensajes
de correo electrónico a miles de personas, la programación implica instruir a la computadora para
que realice muchas acciones repetitivas. En informática, nos referimos a esta ejecución repetitiva
como **iteración**. En esta sección, exploraremos algunos mecanismos para la iteración básica.

Con las colecciones (listas y cadenas), muchos cálculos implican procesar un elemento a la vez.
Para las cadenas, esto significa que nos gustaría procesar un carácter a la vez. A menudo comenzamos
desde el principio, seleccionamos cada personaje por turno, hacemos algo y continuamos hasta el final.
Por ejemplo, podríamos quitar cada carácter y sustituir el carácter a 13 caracteres del alfabeto para
crear un mensaje codificado.

Este patrón de procesamiento se denomina recorrido o iteración sobre los caracteres. Del mismo modo,
podemos procesar cada uno de los elementos de una lista, uno a la vez, iterando sobre los elementos de
la lista. Esto tiene aplicaciones en cada pieza de software que puedas imaginar:

* Visualización de una lista de amigos en SnapChat
* Actualización de la posición de cada personaje en la pantalla de un videojuego
* Visualización de las ubicaciones en las que opera Médicos sin Fronteras


.. La iteración Simplifica nuestro programa en Turtle
.. Agrega “Esto es lo que podemos hacer con la tortuga ahora, si usamos iteración”; prestado de thinkcspy


.. Para dibujar un cuadrado, nos gustaría hacer lo mismo cuatro veces: mover la tortuga hacia delante un poco y girar 90 grados. Anteriormente utilizamos 8 líneas de código Python para que alex dibujara los cuatro lados de un cuadrado. El siguiente programa hace exactamente lo mismo pero, con la ayuda de la instrucción for, usa solo tres líneas (sin incluir el código de configuración). Recuerde que la instrucción for repetirá el reenvío y la izquierda cuatro veces, una vez para cada valor de la lista.

