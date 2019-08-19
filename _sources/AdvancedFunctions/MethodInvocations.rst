..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: func-6-
   :start: 1

Invocaciones de métodos
------------------------

.. note::

   Esta sección es una revisión del material que ya ha visto, pero puede ser útil volver a verlo ahora que se está centrando en las funciones y las llamadas a funciones.

Existe otro tipo especial de función llamada **método**, que se invoca de manera ligeramente diferente. Algunos
Los tipos de objeto tienen métodos definidos para ellos. Ya ha visto algunos métodos que operan en cadenas (por ejemplo,
``find``, ``index``, ``split``, ``join``) y en las listas (por ejemplo, ``append``, ``pop``).

No aprenderemos sobre cómo definir métodos hasta más adelante en el curso, cuando cubramos las clases. Pero vale la pena conseguir
una comprensión básica ahora de cómo se invocan los métodos. Para invocar un método, la sintaxis es
``<expr>.<nombre del método> (<valores de parámetros adicionales>)``.

La expresión a la izquierda del punto debe evaluar a un objeto del tipo correcto, un objeto para el cual <nombredelmétodo>
se define. El método se aplicará a ese objeto (ese objeto será un valor de parámetro pasado a la
función/método.) Si el método toma parámetros adicionales (algunos sí, otros no), expresiones adicionales que evalúan
los valores a se incluyen dentro de los paréntesis.

Por ejemplo, veamos una invocación del método de división.

.. activecode:: ac11_6_1

   y = "This is a sentence"
   z = y.split()
   print(type(z))
   print(len(z))
   print(z)
   for w in z:
       print(w)
      
El método de división opera en una cadena. Debido a que es un método en lugar de una función regular, la cadena en la que opera
aparece a la izquierda del punto, en lugar de dentro del paréntesis. El método de división siempre devuelve una lista. En línea
2, ese valor devuelto se asigna a la variable z.

El método de división en realidad toma un parámetro adicional opcional. Si no se proporciona ningún valor dentro de los paréntesis,
El método split corta la lista cada vez que encuentra un espacio en blanco (un espacio, una pestaña o una nueva línea). Pero puedes especificar un
carácter o cadena de caracteres para dividir. Intente poner "s" dentro de los paréntesis en la línea 2 de arriba, haga una predicción
sobre cuál será el resultado y luego verifíquelo. Pruebe otras cosas dentro de los paréntesis.

Tenga en cuenta que lo que está a la izquierda del punto puede ser cualquier expresión, no solo un nombre de variable. Incluso puede ser un regreso
valor de alguna otra llamada a función o invocación de método. Por ejemplo, si queremos eliminar los caracteres s y t de
una cadena, podemos hacerlo todo en una línea como se muestra a continuación.

.. activecode:: ac11_6_2

   print("This is a sentence".replace("s", "").replace("t", ""))
 
¿Que esta pasando ahí? Comienza a leer de izquierda a derecha. "This is a sentence" es una cadena y se invoca el método replace
en ella. Se proporcionan dos valores de parámetros adicionales, "s", y una cadena vacía. Entonces, en la oración, todas las ocurrencias de
"s" se reemplazan con la cadena vacía. Se devuelve una nueva cadena, "Thi i a entence". Hay otro período seguido
por la palabra reemplazar, por lo que el método de reemplazo se llama nuevamente en esa cadena, devolviendo la cadena más corta, que es
impreso.
