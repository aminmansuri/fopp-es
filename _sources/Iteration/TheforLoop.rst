..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: iter-2-
   :start: 1

.. index:: for loop, iteration, body 
   loop; for

El bucle **for**
----------------

.. video:: forloopvid
   :controls:
   :thumb: ../_static/for_loop.png

   http://media.interactivepython.org/thinkcsVideos/for_loop.mov
   http://media.interactivepython.org/thinkcsVideos/for_loop.webm


Cuando dibujamos las imágenes con tortuga, podría ser bastante tedioso. Si quisiéramos dibujar un cuadrado
luego tuvimos que movernos, girar, mover, girar, etc., etc. cuatro veces. Si estuviéramos dibujando un hexágono,
o un octágono, o un polígono con 42 lados, habría sido una pesadilla duplicar todo ese código.

Un componente básico de todos los programas es poder repetir un código una y otra vez. Nosotros
refiérase a esta idea repetitiva como **iteración**. En esta sección, exploraremos algunos mecanismos para
iteración básica

En Python, la declaración **for** nos permite escribir programas que implementan iteración. Como un simple
ejemplo, digamos que tenemos algunos amigos, y nos gustaría enviarles un correo electrónico invitándolos a
nuestra fiesta. Todavía no sabemos cómo enviar un correo electrónico, así que por el momento solo imprimiremos un mensaje
para cada amigo

.. activecode:: ac6_2_1
    :nocanvas:
    :tour_1: "Overall Tour"; 1-2: Example04_Tour01_Line01; 2: Example04_Tour01_Line02; 1: Example04_Tour01_Line03;

    for name in ["Joe", "Amy", "Brad", "Angelina", "Zuki", "Thandi", "Paris"]:
        print("Hi", name, "Please come to my party on Saturday!")


Eche un vistazo a la salida producida cuando presiona el botón ``run``. Hay una línea impresa para
cada amigo Así es como funciona:


* **name** en esta declaración ``for`` se llama **variable de bucle** o, como alternativa, **variable iteradora**.
* La lista de nombres entre corchetes es la secuencia sobre la cual iteraremos.
* La línea 2 es el **cuerpo del bucle**. El cuerpo del bucle siempre está
  identado. La identación determina exactamente qué declaraciones están "dentro del bucle". El cuerpo del loop
  se realiza una vez para cada nombre en la lista.
  * En cada *iteración* o *vuelta* del bucle, primero se realiza una comprobación para ver si
  Todavía hay más elementos para procesar. Si no queda ninguno (esto es
  llamada la **condición de terminación** del bucle), el bucle ha terminado.
  La ejecución del programa continúa en la siguiente declaración después del cuerpo del bucle.
* Si todavía hay elementos por procesar, la variable de bucle se actualiza a
  consulte el siguiente elemento de la lista. Esto significa, en este caso, que el bucle
  El cuerpo se ejecuta aquí 7 veces, y cada vez que ``nombre`` se referirá a un nombre diferente amigo.
* Al final de cada ejecución del cuerpo del bucle, Python regresa
  a la declaración ``para``, para ver si hay más elementos para manejar.


La sintaxis general es ``for <variable_iteradora> in <secuencia>:``

* Entre las palabras for y in, debe haber un nombre de variable para la variable de bucle. No puedes poner una expresión completa allí.
* Se requieren dos puntos al final de la línea
* Después de la palabra dentro y antes de los dos puntos es una expresión que debe evaluarse en una secuencia (por ejemplo, una cadena o una lista o una tupla). Podría ser un literal, o un nombre de variable, o una expresión más compleja.