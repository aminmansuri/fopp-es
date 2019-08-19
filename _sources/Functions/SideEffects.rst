..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: func-13-
   :start: 1

Efectos secundarios
--------------------

Decimos que la función ``changeit`` tiene un **efecto secundario** en el objeto de lista que se le pasa. Las variables
Global son otra forma de tener efectos secundarios. Por ejemplo, similar a los ejemplos que ha visto anteriormente, podríamos hacer que
``double`` tenga un efecto secundario en la variable global y.

.. codelens:: clens11_13_1
   :python: py3

   def double(n):
      global y
      y = 2 * n
   
   y = 5
   double(y)
   print(y)

Los efectos secundarios a veces son convenientes. Por ejemplo, puede ser conveniente tener un solo diccionario que acumule
información y pasarla a varias funciones que podrían agregarle o modificarla.

Sin embargo, los programas que tienen efectos secundarios pueden ser muy difíciles de depurar. Cuando un objeto tiene un valor que no es lo que
esperaba, puede ser difícil rastrear exactamente en qué parte del código se configuró. Donde sea práctico hacer.
Por lo tanto, es mejor evitar los efectos secundarios. La forma de evitar el uso de efectos secundarios es usar valores de retorno en su lugar.

En lugar de modificar una variable global dentro de una función, pase el valor de la variable global como parámetro y establezca
que la variable global sea igual a un valor devuelto por la función. Por ejemplo, la siguiente es una versión mejor
del código anterior.

.. codelens:: clens11_13_2
   :python: py3

   def double(n):
      return 2 * n
   
   y = 5
   y = double(y)
   print(y)

Puede usar el mismo patrón de codificación para evitar confusos efectos secundarios al compartir objetos mutables. Para hacer eso,
explícitamente haga una copia de un objeto y pase la copia a la función. Luego devuelva la copia modificada y reasigne
a la variable original si desea guardar los cambios. La función incorporada de ``lista``, que toma una secuencia como
parámetro y devuelve una nueva lista, funciona para copiar una lista existente. Para los diccionarios, también puede llamar al ``dict``,
pasando un diccionario para recuperar una copia del diccionario como valor de retorno.

.. codelens:: clens11_13_3
   :python: py3

   def changeit(lst):
      lst[0] = "Michigan"
      lst[1] = "Wolverines"
      return lst
      
   mylst = ['106', 'students', 'are', 'awesome']
   newlst = changeit(list(mylst))
   print(mylst)
   print(newlst)

En general, cualquier efecto duradero que ocurra en una función, no a través de su valor de retorno, se denomina efecto secundario. Ahí
hay tres formas de tener efectos secundarios:

* Imprimir un valor. Esto no cambia ningún objeto o enlaces variables, pero tiene un efecto potencial duradero fuera de la ejecución de la función, porque una persona puede ver el resultado y ser influenciado por él.
* Cambiar el valor de un objeto mutable.
* Cambiar el enlace de una variable global.
