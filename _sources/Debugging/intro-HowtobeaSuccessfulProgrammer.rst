..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: debug-1-
   :start: 1

.. index:: boundary conditions, testing, debugging

👩‍💻 Depuración
===================

La programación es un proceso complejo. Como lo hacen los seres humanos, a menudo pueden ocurrir errores.
Los errores de programación se denominan **bugs** y el proceso
de rastrearlos y corregirlos se llama **debuggin**. Hubo reclamos de
que en 1945, una polilla muerta causó un problema en el relé número 70, panel F, de una
de las primeras computadoras en Harvard, y el término **bug** (insecto) se ha mantenido en uso.
Para más información sobre este evento histórico, vea `first bug <http://en.wikipedia.org/wiki/File:H96566k.jpg>`__.

Una de las habilidades más importantes que necesitas adquirir para completar este libro con éxito es la
capacidad de depurar tus programas. La depuración puede ser la menos apreciada y
poco enseñada habilidad en informática introductoria. Por esa razón estamos introduciendo una
serie de "interludios de depuración". La depuración es una habilidad que debes dominar con el tiempo, y
algunos de los consejos y trucos son específicos de diferentes aspectos de la programación de Python. Entonces busca
interludios adicionales de Way of the Programmer en el resto de este libro.


La programación es algo extraño en cierto sentido. Aquí está el por qué. Como programadores, pasamos el 99% de nuestro tiempo
tratando de hacer que nuestro programa funcione. Luchamos, nos estresamos, pasamos horas profundamente frustrados
tratando de hacer que nuestro programa se ejecute correctamente. Luego, cuando lo ponemos en marcha, celebramos
y pasamos a la siguiente tarea de programación. Pero aquí está el secreto,
cuando tienes éxito, eres feliz, tu cerebro libera un poco de químico que te hace
sentir bien. Necesitas organizar tu forma de programar para que tenga muchos pequeños éxitos. Eso
resulta en que a tu cerebro no le importe mucho si has escrito con éxito hola mundo,
o una rápida transformación de Fourier (confía en mí es difícil) todavía obtienes esa pequeña versión que te hace
feliz. Cuando eres feliz, quieres continuar y resolver el siguiente pequeño problema. Esencialmente,
te digo lo una vez más, comienza con algo pequeño, haz que algo pequeño funcione y luego agrégalo.

Cómo evitar la depuración
-------------------------

Quizás la lección más importante en la depuración es que es **en gran medida evitable** --
si trabajas con cuidado.

1. **Comience pequeño** Este es probablemente el consejo más importante para los programadores en
todos los niveles. Por supuesto, es tentador sentarse y poner en marcha un programa completo a la vez. Pero,
cuando el programa, inevitablemente, no funciona, entonces tienes una gran cantidad de opciones para las cosas
que podrían estar mal. ¿Donde empezar? ¿Dónde mirar primero? ¿Cómo averiguar qué salió mal?
Llegaré a eso en la siguiente sección. Entonces, comience con algo realmente pequeño. Tal vez solo dos
líneas y luego asegúrese de que funciona bien. Pulsar el botón de correr es rápido y fácil, y te da
información inmediata sobre si lo que acabas de hacer está bien o no. Otro inmediato es
el beneficio de tener algo pequeño que funciona es que tiene algo que entregar.
Un programa pequeño e incompleto, casi siempre, es mejor que nada.


2. **Manténgalo funcionando** Una vez que tenga una pequeña parte de su programa trabajando, el siguiente paso es
deicidir algo pequeño para agregarle. Si sigues agregando pequeñas piezas del programa uno
a la vez, es mucho más fácil descubrir qué salió mal, ya que lo más probable es que
el problema va a estar en el nuevo código que acaba de agregar. Menos código nuevo significa que es más fácil
averiguar dónde está el problema.

Esta noción de **Hacer que algo funcione y mantenerlo funcionando** es un mantra que puedes repetir
a lo largo de tu carrera como programador. Es una excelente manera de evitar las frustraciones mencionadas
encima. Piénsalo de esta manera. Cada vez que tienes un poco de éxito, tu cerebro libera
un poco de químico que te hace feliz. Entonces, puedes mantenerte feliz y hacer la programación
más agradable creando muchas pequeñas victorias para ti.

Ok, veamos un ejemplo. Vamos a resolver el problema planteado en la pregunta 3 al final del
capítulo simple de datos de Python. Pregunte al usuario por el tiempo ahora (en horas 0 -- 23), y solicite la
cantidad de horas para esperar. Su programa debería mostrar qué hora será en el reloj cuando
la alarma se apaga.

Entonces, ¿por dónde empezar? El problema requiere dos entradas del usuario, así que comencemos
allí y asegúrese de que podamos obtener los datos que necesitamos.

.. activecode:: db_ex3_1

   current_time = input("¿Cuál es la hora actual (en horas)?")
   wait_time = input("¿Cuántas horas quieres esperar?")

   print(current_time)
   print(wait_time)


Si aún no lo ha hecho, haga clic en Ejecutar: acostúmbrese a verificar si las cosas pequeñas funcionan
antes de continuar

Hasta ahora vamos bien. Ahora demos el siguiente paso. Tenemos que averiguar cuánto será el tiempo
esperando ``wait_time`` en número de horas. Una buena primera aproximación a eso es simplemente agregar
``wait_time`` a ``current_time`` e imprima el resultado. Entonces intentemos eso.

.. activecode:: db_ex3_2

   current_time = input("¿Cuál es la hora actual (en horas 0--23)?")
   wait_time = input("¿Cuántas horas quieres esperar?")

   print(current_time)
   print(wait_time)

   final_time = current_time + wait_time
   print(final_time)

Hmm, cuando ejecutas ese ejemplo, ves que algo extraño ha sucedido.

.. mchoice:: db_q_ex3_1
   :answer_a: Python es estúpido y no sabe cómo sumar correctamente.
   :answer_b: No hay nada malo aquí.
   :answer_c: Python está haciendo la concatenación de cadenas, no la suma de enteros.
   :feedback_a: No, Python probablemente no está equivocado.
   :feedback_b: No, intente sumar los dos números juntos, definitivamente obtendrá un resultado diferente.
   :feedback_c: ¡Sí! Recuerde que la entrada devuelve una cadena. Ahora necesitaremos convertir la cadena a un entero
   :correct: c

   ¿Cuál de las siguientes opciones describe mejor lo que está mal en el ejemplo anterior?

Este error fue probablemente bastante simple de detectar, porque imprimimos el valor de
``final_time`` y es fácil ver que los números simplemente se concatenaron juntos.
Entonces, ¿qué hacemos con el problema? Necesitaremos convertir tanto ``current_time``
y ``wait_time`` a ``int``. En esta etapa de su desarrollo de programación, puede ser una buena
idea el incluir el tipo de la variable en el nombre de la variable en sí. Así que echemos un vistazo a otra
iteración del programa que hace eso, y la conversión a entero.


.. activecode:: db_ex3_3

   current_time_str = input("¿Cuál es la hora actual (en horas 0-23)?")
   wait_time_str = input("¿Cuántas horas quieres esperar?")

   current_time_int = int(current_time_str)
   wait_time_int = int(wait_time_str)

   final_time_int = current_time_int + wait_time_int
   print(final_time_int)


Eso es mucho mejor, y de hecho, dependiendo de las horas que elija, puede ser exactamente correcto.
Si ingresó 8 para la hora actual y 5 para el tiempo de espera, entonces 13 es correcto. Pero si
ingresó 17 (5pm) para las horas y 9 para el tiempo de espera, entonces el resultado de 26 no es correcto.
Esto ilustra un aspecto importante de **prueba**, que es importante probar su
código en un rango de entradas. Es especialmente importante probar su código en **condiciones de contorno**.
En este caso, debería probar su programa durante horas, incluidos 0, 23 y algunas en el medio.
Debería probar sus tiempos de espera para 0, y algunos números realmente grandes. Qué pasa con los
¿números negativos? Los números negativos no tienen sentido, pero dado que realmente no tenemos las herramientas
para tratar de decirle al usuario cuando algo está mal, no nos preocuparemos por eso todavía.

Finalmente, tenemos que tener en cuenta esos números que son mayores que 23. Para esto necesitaremos
un último paso, utilizando el operador de módulo.

.. activecode:: db_ex3_4

   current_time_str = input("¿Cuál es la hora actual (en horas 0-23)?")
   wait_time_str = input("¿Cuántas horas quieres esperar?")

   current_time_int = int(current_time_str)
   wait_time_int = int(wait_time_str)

   final_time_int = current_time_int + wait_time_int
   
   final_answer = final_time_int % 24

   print("La hora después de esperar es:", final_answer)

Por supuesto, incluso en esta simple progresión, hay otras formas en que podría haberse confundido.
Veremos algunos de ellos y cómo los rastreará en la siguiente sección.


**Chequea tu entendimiento**

.. mchoice:: question4_1_1
   :answer_a: Rastrear errores de programación y corregirlos.
   :answer_b: Eliminar todos los errores de tu programa.
   :answer_c: Encontrar todos los errores en el programa.
   :answer_d: Arreglar los errores en el programa.
   :correct: a
   :feedback_a: Los errores de programación se denominan bugs y el proceso de encontrarlos y eliminarlos de un programa se denomina debuggin.
   :feedback_b: Tal vez, pero eso no es de lo que estamos hablando en este contexto.
   :feedback_c: Esto es parcialmente correcto. Pero, la depuración es más que solo encontrar los errores. ¿Qué necesitas hacer una vez que los encuentres?
   :feedback_d: Esto es parcialmente correcto. Pero, la depuración es más que solo solucionar los errores. ¿Qué necesita hacer antes de poder solucionarlos?

   La depuración es:
