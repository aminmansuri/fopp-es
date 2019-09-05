..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: modules-2-
   :start: 1

El Módulo ``Random``
--------------------


A menudo queremos usar **números aleatorios** en los programas. Aquí hay algunos usos típicos:

* Para jugar un juego de azar donde la computadora necesita lanzar algunos dados, elegir un
  número o lanzar una moneda,
* Para barajar una baraja de cartas al azar
* Para permitir que una nueva nave espacial enemiga aparezca y te dispare al azar,
* Para simular posibles lluvias cuando hacemos un modelo computarizado para
  estimar el impacto ambiental de construir una presa,
* Para encriptar su sesión bancaria en Internet.

Python proporciona un módulo ``aleatorio`` que ayuda con tareas como esta. Puedes echarle un vistazo en la documentación.
Aquí están las cosas clave que podemos hacer con él.

.. activecode:: ac13_2_1

    import random

    prob = random.random()
    print(prob)

    diceThrow = random.randrange(1,7) # devuelve un int, uno de 1,2,3,4,5,6
    print(diceThrow)

Presione el boton Ejecutar varias veces. Tenga en cuenta que los valores cambian cada vez. Estos son números aleatorios.


La función "randrange" genera un número entero entre su argumento inferior y superior donde se incluye el límite inferior, pero se excluye el límite superior. Entonces, "randrange(1,7)" incluirá numeros del 1 al 6. Si omite el primer parametro, se supone que es 0, por lo que "randrange(10)" le dara números del 0-9. Todos los valores tienen la misma probabilidad.
de ocurrir (es decir, los resultados estan *uniformemente* distribuidos).

La función ``random()`` devuelve un número de coma flotante en el rango [0.0, 1.0) --- el corchete significa "intervalo
cerrado a la izquierda "y el paréntesis redondo significa" intervalo abierto a la derecha ". En otras palabras, 0.0 es posible,
pero todos los números devueltos serán estrictamente inferiores a 1.0. Es habitual *escalar* los resultados después de llamar a este método,
para ponerlos en un rango adecuado para su aplicación.

En el caso que se muestra a continuación, hemos convertido el resultado de la llamada al método en un número en el rango [0.0, 5.0). Una vez más,
estos son números distribuidos uniformemente --- los números cercanos a 0 tienen la misma probabilidad de ocurrir que los números cercanos a 3, o
números cercanos a 5. Si continúa presionando el botón de ejecución, verá valores aleatorios entre 0.0 y hasta, pero no
incluyendo 5.0.


.. activecode:: ac13_2_2

    import random

    prob = random.random()
    result = prob * 5
    print(result)

.. index:: algoritmo determinista, algoritmo; determinista, pruebas unitarias

Es importante tener en cuenta que los generadores de números aleatorios se basan en un algoritmo **determinista** --- repetible y
previsible. Entonces se llaman generadores **pseudoaleatorios** --- no son realmente aleatorios. Comienzan con un valor *semilla*.
Cada vez que solicite otro número aleatorio, obtendrá uno basado en el atributo semilla actual y el estado
de la semilla (que es uno de los atributos del generador) se actualizará. La buena noticia es que cada vez que corre
en su programa, es probable que el valor inicial sea diferente, lo que significa que a pesar de que se están creando los números aleatorios
algorítmicamente, es probable que obtenga un comportamiento aleatorio cada vez que se ejecute.

**Revisa tu entendimiento**

.. mchoice:: question13_2_1
   :answer_a: prob = random.randrange(1, 101)
   :answer_b: prob = random.randrange(1, 100)
   :answer_c: prob = random.randrange(0, 101)
   :answer_d: prob = random.randrange(0, 100)
   :correct: a
   :feedback_a: Esto generará un número entre 1 y 101, pero no incluye 101.
   :feedback_b: Esto generará un número entre 1 y 100, pero no incluye 100. El valor más alto generado será 99.
   :feedback_c: Esto generará un número entre 0 y 100. El valor más bajo generado es 0. El valor más alto generado será 100.
   :feedback_d: Esto generará un número entre 0 y 100, pero no incluye 100. El valor más bajo generado es 0 y el valor más alto generado será 99.
   :practice: T

   El código correcto para generar un número aleatorio entre 1 y 100 (inclusive) es:

.. mchoice:: question13_2_2
   :answer_a: No hay computadora en el escenario para sacar los números.
   :answer_b: Debido a que las computadoras realmente no generan números aleatorios, generan números pseudoaleatorios.
   :answer_c: Simplemente generarían los mismos números una y otra vez.
   :answer_d: La computadora no puede decir qué valores ya se seleccionaron, por lo que podría generar cinco números 5 en lugar de 5 números únicos.
   :correct: b
   :feedback_a: Podrían poner fácilmente uno allí.
   :feedback_b: Las computadoras generan números aleatorios usando un algoritmo determinista. Esto significa que si alguien alguna vez descubriera el algoritmo, podría predecir con precisión el siguiente valor a generar y siempre ganaría la lotería.
   :feedback_c: Esto podría suceder si se usara el mismo valor inicial una y otra vez, pero podrían asegurarse de que este no fuera el caso.
   :feedback_d: Si bien un programador necesitaría asegurarse de que la computadora no seleccionó el mismo número más de una vez, es fácil asegurarlo.

   Una razón por la cual las loterías no usan computadoras para generar números aleatorios es:

