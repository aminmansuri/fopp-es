..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: func-12-
   :start: 1

Pasando objetos mutables
------------------------

Como ha visto, cuando se invoca una función (o método) y se proporciona un valor de parámetro, se genera un nuevo marco de pila
creado, y el nombre del parámetro está vinculado al valor del parámetro. Lo que sucede cuando el valor que se proporciona es un
objeto mutable, ¿como una lista o diccionario? ¿El nombre del parámetro está vinculado a una *copia* del objeto original, o lo hace
convertirse en un alias para exactamente ese objeto? En python, la respuesta es que se convierte en un alias para el objeto original.
Esta respuesta es importante cuando el bloque de código dentro de la definición de la función hace que se realicen algunos cambios en el objeto
(por ejemplo, agregar un par clave-valor a un diccionario o agregar a una lista).

Esto arroja una luz un poco diferente sobre la idea de que los parámetros sean  *locales*. Son *locales* en el sentido de que si usted
tiene un parámetro x dentro de una función y hay una variable global x, cualquier referencia a x dentro de la función te lleva
a el valor de la variable local x, no la global. Si establece ``x = 3``, cambia el valor de la variable local x,
pero cuando la función termina de ejecutarse, esa x local desaparece, y también el valor 3.

Si, por otro lado, la variable local x apunta a una lista ``[1, 3, 7]``, al establecer ``x[2] = 0``, x sigue apuntando
a la misma lista, pero cambia el contenido de la lista a ``[1, 3, 0]``. La variable local x se descarta cuando la función
completa la ejecución, pero la mutación en la lista sigue viva si hay alguna otra variable fuera de la función que
también es un alias para la misma lista.

Considere el siguiente ejemplo.

.. activecode:: ac11_12_1
   
   def double(y):
       y = 2 * y
   
   def changeit(lst):
       lst[0] = "Michigan"
       lst[1] = "Wolverines"

   y = 5
   double(y)
   print(y)
      
   mylst = ['our', 'students', 'are', 'awesome']
   changeit(mylst)
   print(mylst)

Intenta ejecutarlo. Similar a los ejemplos que hemos visto antes, ejecutar ``double`` no cambia la y global. Pero corriendo
``changeit`` cambia ``mylst``. La explicación es anterior, sobre el intercambio de objetos mutables. Intente recorrerlo en codelens para ver la diferencia.

.. codelens:: clens11_12_1
   :python: py3

   def double(n):
       n = 2 * n
   
   def changeit(lst):
       lst[0] = "Michigan"
       lst[1] = "Wolverines"

   y = 5
   double(y)
   print(y)
      
   mylst = ['106', 'students', 'are', 'awesome']
   changeit(mylst)
   print(mylst)
