..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: progdev-1-
   :start: 1

👩‍💻 Desarrollo del programa
------------------------------------

En este punto, debería poder ver las funciones completas y decir qué
ellas hacen. Además, si ha estado haciendo los ejercicios, ha escrito algunas
pequeñas funciones. A medida que escribe funciones más grandes, puede comenzar a tener más
dificultad, especialmente con tiempo de ejecución y errores semánticos.

Para tratar con programas cada vez más complejos, vamos a sugerir una técnica
llamado **desarrollo incremental**. El objetivo del desarrollo incremental es que
evite largas sesiones de depuración agregando y probando solo una pequeña cantidad de código
a la vez

Si escribe pruebas unitarias antes de realizar el desarrollo incremental, podrá seguir su progreso a medida que el código pase más y más pruebas. Alternativamente, puede escribir pruebas adicionales en cada etapa del desarrollo incremental.
Luego podrá verificar si cualquier cambio de código que realice en una etapa posterior del desarrollo hace que una de las pruebas anteriores, que solía pasar, ya no pasara.

Como ejemplo, suponga que desea encontrar la distancia entre dos puntos, dado
por las coordenadas (x\ :sub:`1`\ , y\ :sub:`1`\ ) y
(x\ :sub:`2`\ , y\ :sub:`2`\ ). Según el teorema de Pitágoras, la distancia es:

.. image:: Figures/distance_formula.png
   :alt: Fórmula de distancia

El primer paso es considerar cómo debería ser una función de ``distance`` en
Python. En otras palabras, ¿cuáles son las entradas (parámetros) y cuál es la salida?
(valor de retorno)?

En este caso, los dos puntos son las entradas, que podemos representar usando cuatro
parámetros. El valor de retorno es la distancia, que es un valor de coma flotante.

Ya podemos escribir un resumen de la función que captura nuestro pensamiento hasta ahora.

.. sourcecode:: python
    
    def distance(x1, y1, x2, y2):
        return None

Obviamente, esta versión de la función no calcula distancias; siempre
devuelve None. Pero es sintácticamente correcto y se ejecutará, lo que significa
que podemos probarlo antes de hacerlo más complicado.

Importamos el módulo de prueba para permitirnos escribir una prueba unitaria para la función. La distancia entre cualquier punto y sí mismo debe ser 0.

.. activecode:: ac400_1_1
    
    import test
    def distance(x1, y1, x2, y2):
        return None

    test.testEqual(distance(1, 2, 1, 2), 0)

La función ``testEqual`` del módulo de prueba llama a la función de distancia con entradas de muestra: (1,2, 1,2).
Los primeros 1,2 son las coordenadas del primer punto y los segundos 1,2 son las coordenadas del segundo punto.
¿Cuál es la distancia entre estos dos puntos? Cero. ``testEqual`` compara lo que devuelve la función de distancia
y el None que se devuelve.

No está devolviendo la respuesta correcta, por lo que no aprobamos la prueba. Vamos a arreglar eso.

.. activecode:: ac400_1_2

    import test
    def distance(x1, y1, x2, y2):
        return 0.0

    test.testEqual(distance(1, 2, 1, 2), 0)

Ahora pasamos la prueba. Pero realmente, esa no es una prueba suficiente.

.. admonition:: Ampliar el programa ...

   En la línea 6, escriba otra prueba unitaria. Use (1,2, 4,6) como los parámetros para la función de distancia. ¿Qué tan separados están estos dos puntos? Use ese valor (en lugar de 0) como la respuesta correcta para esta prueba unitaria.

   En la línea 7, escriba otra prueba unitaria. Use (0,0, 1,1) como los parámetros para la función de distancia. ¿Qué tan separados están estos dos puntos? Use ese valor como la respuesta correcta para esta prueba unitaria.

   ¿Hay otros casos límite que crees que deberías considerar? ¿Quizás puntos con números negativos para valores x o valores y?


**Al probar una función, es esencial saber la respuesta correcta.**

Para la segunda prueba, la distancia horizontal es igual a 3 y la distancia vertical es igual a 4; de esa manera, el resultado es
5 (la hipotenusa de un triángulo 3-4-5). Para la tercera prueba, tenemos un triángulo 1-1-sqrt(2).

.. activecode:: ac400_1_3

    import test
    def distance(x1, y1, x2, y2):
        return 0

    test.testEqual(distance(1,2, 1,2), 0)
    test.testEqual(distance(1,2, 4,6), 5)
    test.testEqual(distance(0,0, 1,1), 2**0.5)



La primera prueba pasa pero las otras fallan ya que la función de distancia aún no contiene todos los pasos necesarios.

En este punto, hemos confirmado que la función es sintácticamente correcta y podemos comenzar a agregar líneas de código.
Después de cada cambio incremental, probamos la función nuevamente. Si se produce un error en algún momento, sabemos dónde debe estar
--- en la última línea que agregamos.

Un primer paso lógico en el cálculo es encontrar las diferencias x\ :sub:`2`\ - x\ :sub:`1`\ e y\ :sub:`2`\ - y\ :sub:`1`\ .
Almacenaremos esos valores en variables temporales llamadas ``dx`` y ``dy``.

.. sourcecode:: python
    
    def distance(x1, y1, x2, y2):
        dx = x2 - x1
        dy = y2 - y1
        return 0.0

Luego calculamos la suma de los cuadrados de ``dx`` y ``dy``.

.. sourcecode:: python
    
    def distance(x1, y1, x2, y2):
        dx = x2 - x1
        dy = y2 - y1
        dsquared = dx**2 + dy**2
        return 0.0

De nuevo, podríamos ejecutar el programa en esta etapa y verificar el valor de ``dsquared`` (que
debería ser 25).

Finalmente, usando el exponente fraccional ``0.5`` para encontrar la raíz cuadrada,
calculamos y devolvemos el resultado.

.. index:: testing, unit test

.. activecode:: ac400_1_4
    
    import test
    def distance(x1, y1, x2, y2):
        dx = x2 - x1
        dy = y2 - y1
        dsquared = dx**2 + dy**2
        result = dsquared**0.5
        return result

    test.testEqual(distance(1,2, 1,2), 0)
    test.testEqual(distance(1,2, 4,6), 5)
    test.testEqual(distance(0,0, 1,1), 2**0.5)


..     test.testEqual(distance(0,0, 1,1), 1.41)

.. .. admonition Fix the error ...

..    Dos de las pruebas pasan pero la última falla. ¿Sigue habiendo un error en la función?

.. Frecuentemente descubrimos errores en las funciones que estamos escribiendo. Sin embargo, es posible que haya un error en una prueba. Aquí el error está en la precisión de la respuesta correcta.

.. La tercera prueba falla porque por defecto testEqual verifica 5 dígitos a la derecha del punto decimal.

..    - Cambie ``1.41`` a ``1.41421`` y ejecútelo. La prueba pasará.

.. Hay circunstancias en las que 2 dígitos a la derecha del punto decimal son lo suficientemente precisos.

..    - Copie la línea 11 en la línea 12. En la línea 12, cambie ``1.41421`` a ``1.41``. Ejecutar. La prueba falla.

..    - Escriba ``, 2`` después de 1.41. (El 2 representa la precisión de la prueba: cuántos dígitos a la derecha del decimal deben ser correctos). Ejecutar.

..    Ahora pasan las cuatro pruebas. ¡Maravilloso! Sin embargo, es posible que aún necesite realizar pruebas adicionales.

Cuando comienzas, puedes agregar solo una o dos líneas de código a la vez. A medida que ganes más experiencia, podría encontrar
usted mismo escribiendo y depurando fragmentos conceptuales más grandes. A medida que mejore sus habilidades de programación, debería
gestionar trozos cada vez más grandes: esto es muy similar a la forma en que aprendimos a leer letras, sílabas, palabras, frases,
oraciones, párrafos, etc., o la forma en que aprendemos a tocar música --- desde notas individuales hasta acordes, compases, frases, etc.

Los aspectos clave del proceso son:

#. Asegúrese de saber lo que está tratando de lograr. Entonces puedes escribir pruebas unitarias apropiadas.
#. Comience con un programa de esqueleto funcional y realice pequeños cambios incrementales. A cualquier
   punto, si hay un error, sabrá exactamente dónde está.
#. Use variables temporales para mantener valores intermedios para que pueda inspeccionar fácilmente
   y verifíquelos.
#. Una vez que el programa está funcionando, es posible que desee consolidar varias declaraciones
   en expresiones compuestas,
   pero solo haga esto si no hace que el programa sea más difícil de leer.
