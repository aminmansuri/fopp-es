..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: debug-7-
   :start: 1

👩‍💻 Conozca sus mensajes de error
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Muchos problemas en su programa conducirán a un mensaje de error. Por ejemplo como estaba
escribiendo y probando este capítulo del libro escribí la siguiente versión del
programa de ejemplo en la sección anterior.

.. sourcecode:: python

   current_time_str = input("¿Cuál es la hora actual (en horas 0-23)?")
   wait_time_str = input("Cuántas horas quiere esperar")

   current_time_int = int(current_time_str)
   wait_time_int = int(wait_time_int)

   final_time_int = current_time_int + wait_time_int
   print(final_time_int)

¿Puedes ver lo que está mal simplemente mirando el código? Tal vez tal vez no. Nuestro cerebro
tiende a ver lo que creemos que hay, así que a veces es muy difícil encontrar el problema
solo mirando el código. Especialmente cuando es nuestro propio código y estamos seguros de que
¡Hemos hecho todo bien!

Intentemos el programa nuevamente, pero esta vez en un activecode:

.. activecode:: ac4_7_1

   current_time_str = input("¿Cuál es la hora actual (en horas 0-23)?")
   wait_time_str = input("Cuántas horas quiere esperar")

   current_time_int = int(current_time_str)
   wait_time_int = int(wait_time_int)

   final_time_int = current_time_int + wait_time_int
   print(final_time_int)


¡Ajá! Ahora tenemos un mensaje de error que podría ser útil. El error de nombre nos dice
que ``wait_time_int`` no está definido. También nos dice que el error está en la línea 5.
Esa es **realmente** información útil. Ahora mira la línea cinco y verás que
``wait_time_int`` se usa tanto en el lado izquierdo como en el derecho de la sentencia de asignación.

.. note::
   Las descripciones de error que ve en el activecode pueden ser diferentes (¡y más comprensibles!) que en un código regular
   con el Intérprete de Python. El intérprete en activecode está limitado de muchas maneras, pero está destinado a principiantes,
   incluyendo la redacción elegida para describir los errores.

.. mchoice:: question4_7_1
   :answer_a: No puede usar una variable en los lados izquierdo y derecho de una sentencia de asignación.
   :answer_b: wait_time_int no tiene un valor, por lo que no se puede usar en el lado derecho.
   :answer_c: Esto no es realmente un error, Python no funciona.
   :correct: b
   :feedback_a: No, puede, siempre y cuando todas las variables en el lado derecho ya tengan valores.
   :feedback_b: Sí. Las variables ya deben tener valores para poder usarse en el lado derecho.
   :feedback_c: No, No, No!
   :practice: T

   ¿Cuál de las siguientes explica por qué ``wait_time_int = int(wait_time_int)`` es un error?


Al escribir y utilizar este libro en los últimos años, hemos recopilado muchos datos
estadísticos sobre los programas en este libro. Aquí hay algunas estadísticas sobre mensajes
de error para el ejercicio que hemos estado viendo.

=================== ======= =======
Mensaje             Número  Porcentaje
=================== ======= =======
ParseError:         4999    54.74%
TypeError:          1305    14.29%
NameError:          1009    11.05%
ValueError:         893     9.78%
URIError:           334     3.66%
TokenError:         244     2.67%
SyntaxError:        227     2.49%
TimeLimitError:     44      0.48%
IndentationError:   28      0.31%
AttributeError:     27      0.30%
ImportError:        16      0.18%
IndexError:         6       0.07%
=================== ======= =======

Casi el 90% de los mensajes de error encontrados para este problema son ParseError,
TypeError, NameError o ValueError. Veremos estos errores en tres etapas:

* Primero definiremos qué significan estos cuatro mensajes de error.
* Luego, veremos algunos ejemplos que causan estos errores.
* Finalmente, veremos formas de ayudar a descubrir la causa de estos mensajes.


ParseError
^^^^^^^^^^

Los errores de análisis ocurren cuando comete un error en la sintaxis de su programa.
Los errores son como cometer errores gramaticales por escrito. Si no usas puntos y
comas en tu escritura, entonces estás dificultando que otros lectores entiendan
lo que intentas decir. Del mismo modo, Python tiene ciertas reglas gramaticales que deben
ser seguidas o Python no puede entender lo que estás tratando de decir.

Por lo general, ParseErrors se remonta a los caracteres de puntuación faltantes, como
paréntesis, comillas o comas. Recuerda que en Python las comas están acostumbradas a
parámetros separados a las funciones. Los paréntesis deben estar equilibrados, o Python piensa
que intenta incluir todo lo que sigue como parámetro para alguna función.

Aquí hay un par de ejemplos de ParseError en el programa de ejemplo que hemos estado usando.
Vea si puede descubrir qué los causó.

.. tabbed:: db_tabs1

    .. tab:: Pregunta

        Encuentra y corrige el error en el siguiente código.

        .. activecode:: ac4_7_2

           current_time_str = input("¿Cuál es la hora actual (en horas 0-23)?")
           wait_time_str = input("¿Cuántas horas quieres esperar?"

           current_time_int = int(current_time_str)
           wait_time_int = int(wait_time_str)

           final_time_int = current_time_int + wait_time_int
           print(final_time_int)

    .. tab:: Respuesta

        .. sourcecode:: python

           current_time_str = input("¿Cuál es la hora actual (en horas 0-23)?")
           wait_time_str = input("¿Cuántas horas quieres esperar?"

           current_time_int = int(current_time_str)
           wait_time_int = int(wait_time_str)

           final_time_int = current_time_int + wait_time_int
           print(final_time_int)

        Dado que el mensaje de error nos señala la línea 4, esto puede ser un poco confuso. Si
        mira la línea cuatro con cuidado, verá que no hay ningún problema con la
        sintaxis. Entonces, en este caso, el siguiente paso debería ser retroceder y mirar la
        línea anterior. En este caso, si observa cuidadosamente la línea 2, verá que
        falta un paréntesis derecho al final de la línea. Recuérdalo,
        los paréntesis deben estar equilibrados. Dado que Python permite que las sentencias continúen
        varias líneas dentro de paréntesis, python continuará escaneando posteriormente
        líneas que buscan el paréntesis de equilibrio correcto. Sin embargo en este caso
        encuentra el nombre ``current_time_int`` y querrá interpretarlo como
        otro parámetro para la función de entrada. Pero no hay una coma que
        separe la cadena anterior de la variable, en lo que respecta a Python
        el error aquí es una coma que falta. Desde tu perspectiva es que falta un
        paréntesis.

**Encontrar pistas** ¿Cómo puedes ayudarte a encontrar estos problemas? Un truco que puede ser
muy valioso en esta situación es simplemente comenzar comentando el número de línea
que está marcado que contiene el error. Si se comenta la línea cuatro, el mensaje de error
ahora cambia a punto a la línea 5. Ahora te preguntas, ¿estoy realmente tan mal que ya
tiene dos líneas seguidas que tienen errores? Tal vez, podrías llevado al extremo,
podrías comentar todas las líneas restantes en el programa. Ahora el mensaje de error
cambia a ``TokenError: EOF in multi-line statement`` (TokenError: EOF en sentencia de varias líneas)
Esta es una forma muy técnica de decir que Python llegó al final del archivo (EOF) mientras todavía estaba buscando
alguna cosa. En este caso un paréntesis derecho.



.. tabbed:: db_tabs2

    .. tab:: Pregunta

        Encuentra y corrige el error en el siguiente código.

        .. activecode:: ac4_7_3

           current_time_str = input("¿Cuál es la" hora actual "(en horas 0-23)?")
           wait_time_str = input("¿Cuántas horas quieres esperar?")

           current_time_int = int(current_time_str)
           wait_time_int = int(wait_time_str)

           final_time_int = current_time_int + wait_time_int
           print(final_time_int)

    .. tab:: Respuesta

        .. sourcecode:: python

           current_time_str = input("¿Cuál es la" hora actual "(en horas 0-23)?")
           wait_time_str = input("¿Cuántas horas quieres esperar?")

           current_time_int = int(current_time_str)
           wait_time_int = int(wait_time_str)

           final_time_int = current_time_int + wait_time_int
           print(final_time_int)

        El mensaje de error lo señala a la línea 1 y en este caso es exactamente donde
        se produce el error. En este caso, su mayor pista es notar la diferencia
        en el resalte de la línea. Observe que las palabras "hora actual" son un
        color diferente a los que las rodean. ¿Por qué es esto? Porque "hora actual"
        está entre comillas dobles dentro de otro par de comillas dobles. Python piensa que
        estás terminando una cadena, luego tienes otros nombres y finalmente
        otra cadena. Pero no ha separado estos nombres o cadenas por comas,
        y no los ha agregado junto con el operador de concatenación (+). Asi que,
        hay varias correcciones que puede hacer. Primero podrías hacer que el
        argumento para ingresar sea el siguiente: ``"¿Cuál es la 'hora actual' (en horas 0-23)?"``
        Tenga en cuenta que aquí hemos utilizado correctamente comillas simples dentro de comillas dobles.
        Otra opción es simplemente eliminar las comillas dobles adicionales. Porque estabas
        citando "hora actual" de todos modos? ``"¿Cuál es la hora actual (en horas 0-23)"``


**Encontrar pistas** Si sigue los mismos consejos para el último problema, comente la
línea uno, inmediatamente recibirá un mensaje de error diferente. Aquí es donde necesitas
tener mucho cuidado y no entrar en pánico. El mensaje de error que obtienes ahora es: ``NameError: name
'current_time_str' is not defined on line 4``. Puedes estar muy tentado a pensar
que esto está relacionado de alguna manera con el problema anterior e inmediatamente concluir que
hay algo mal con el nombre de la variable ``current_time_str`` pero si usted
reflexiona por un minuto, verá que al comentar la línea 1 ha causado un
error nuevo y no relacionado. Es decir, has comentado la creación del nombre.
``current_time_str``. Entonces, por supuesto, cuando desee convertirlo a un ``int``, lo hará
obtener el NameError. Sí, esto puede ser confuso, pero será mucho más fácil con
experiencia. También es importante mantener la calma y evaluar cada nueva pista cuidadosamente,
no pierdas el tiempo persiguiendo problemas que realmente no existen.


Elimine el comentario de la línea 1 y volverá al ParseError. Otra pista es eliminar una
posible fuente de error. En lugar de comentar toda la línea, podrías
intentar asignar ``current_time_str`` a un valor constante. Por ejemplo, podrías hacer que
la línea uno se vea así: ``current_time_str = "10"  #input("¿Cuál es el"hora
actual "(en horas 0-23)?")``. Ahora ha asignado ``current_time_str`` a la cadena
10, y comentó la sentencia input. ¡Y ahora el programa funciona! Puede llegar a la
conclusión de que el problema debe tener algo que ver con la función de entrada.


TypeError
^^^^^^^^^

Los errores de tipo se producen cuando intenta combinar dos objetos que no son compatibles. Por
ejemplo, intenta sumar un número entero y una cadena. Por lo general, los errores de tipo pueden ser
aislados a líneas que usan operadores matemáticos, y generalmente el número de línea
dado por el mensaje de error es una indicación precisa de la línea.

Aquí hay un ejemplo de un error de tipo creado por un alumno . A ver si puedes encontrar
y corregir el error.

.. activecode:: ac4_7_4

    a = input('wpisz godzine')
    x = input('wpisz liczbe godzin')
    int(x)
    int(a)
    h = x // 24
    s = x % 24
    print (h, s)
    a = a + s
    print ('godzina teraz', a)



.. reveal:: dbex4_rev
    :showtitle: Muéstrame la solución
    :hidetitle: Esconder

    .. admonition:: Solución

        Al encontrar este error, hay pocas lecciones en las que pensar. Primero, puedes
        sentir que es muy desconcertante que no puedas entender todo el programa.
        A menos que hable el alumno, esto no será un problema. Pero, aprendiendo lo que tu
        puedes ignorar, y lo que se necesita para centrarse es una parte muy importante del
        proceso de depuración. Segundo, los tipos y los buenos nombres de variables son importantes y
        pueden ser muy útiles. En este caso, a y x no son nombres particularmente útiles,
        y en particular no te ayudan a pensar en los tipos de tu
        variables, que como el mensaje de error implica, es la raíz del problema aquí.
        Al resto de las lecciones regresaremos en un minuto.

        El mensaje de error proporcionado le da una pista bastante grande.
        ``TypeError: tipos de operando no admitidos para FloorDiv: 'str' y 'number' en línea: 5``
        En la línea cinco estamos tratando de usar la división de enteros en x y 24. El error
        El mensaje le indica que está tratando de dividir una cadena por un número. En esto
        en caso de que sepa que 24 es un número, entonces x debe ser una cadena. ¿Pero cómo? Usted puede
        ver la llamada a la función en la línea 3 donde está convirtiendo x en un entero.
        ``int(x)`` o eso crees. Esta es la lección tres y es uno de los errores más comunes
        que vemos en la programación introductoria. Cuál es la diferencia entre ``int(x)`` y ``x = int(x)``

        * La expresión ``int(x)`` convierte la cadena referenciada por x en un número entero pero no la almacena en ningún lado. Es muy común suponer que ``int(x)`` de alguna manera cambia a x, ¡ya que eso es lo que pretendes!. Lo que hace que esto sea muy complicado es que ``int(x)`` es una expresión válida, por lo que no causa ningún tipo de error, sino que el error ocurre más adelante en el programa.

        * La sentencia de asignación ``x = int(x)`` es muy diferente. Nuevamente, la expresión ``int(x)`` convierte la cadena referenciada por x en un número entero, pero esta vez también cambia lo que x hace referencia para que x ahora se refiera al valor entero devuelto por la función ``int``.

        Entonces, la solución a este problema es cambiar las líneas 3 y 4 para que sean sentencias de asignación.


**Encontrar pistas** Una cosa que puede ayudarlo en esta situación es imprimir los
valores y los tipos de las variables involucradas en la sentencia que está causando el
error. Puede intentar agregar una sentencia print después de la línea 4 ``print(x, type(x))``
veremos que al menos hemos confirmado que x es de tipo cadena. Ahora necesitas
Comenzarás a trabajar hacia atrás a través del programa. Tienes que preguntarte, ¿dónde se usa x?
¿en el programa? x se usa en las líneas 2, 3 y, por supuesto, 5 y 6 (donde estamos obteniendo
un error). Entonces, tal vez mueva la sentencia print para que esté después de la línea 2 y nuevamente después de 3.
La línea 3 es donde espera que el valor de x se cambie a un entero. Podría la línea 4
estar misteriosamente cambiando x de nuevo a una cadena? No es muy probable. Entonces el valor y el tipo
de x es justo lo que esperarías después de la línea 2, pero no después de la línea 3. Esto
le ayuda a aislar el problema en la línea 3. De hecho, si emplea uno de nuestras anteriores
técnicas de comentar la línea 3, verá que esto no tiene impacto en el error,
y es una gran pista de que la línea 3 tal como está escrita actualmente es inútil.


NameError
^^^^^^^^^

Los errores de nombre casi siempre significan que ha utilizado una variable antes de que tenga un valor.
A menudo, NameErrors son simplemente causados por errores tipográficos en su código. Pueden ser difíciles de detectar si
no tienes buen ojo para detectar errores ortográficos. Otras veces puedes simplemente
recordar mal el nombre de una variable o incluso una función a la que quieres llamar. Ha
visto un ejemplo de un NameError al comienzo de esta sección. Aquí hay otro.
Vea si puede hacer que este programa se ejecute correctamente:

.. activecode:: ac4_7_5

    str_time = input("Cuál es la hora actual?")
    str_wait_time = input("Cuál es el número de horas que desea esperar?")
    time = int(str_time)
    wai_time = int(str_wait_time)

    time_when_alarm_go_off = time + wait_time
    print(time_when_alarm_go_off)

.. reveal:: db_ex5_reveal
    :showtitle: Muéstrame la solución

    .. admonition:: Solución

        En este ejemplo, el estudiante parece ser un deletreador bastante malo, ya que hay un buen
        número de errores tipográficos para corregir. El primero se identifica como wait_time no es
        definido en la línea 6. Ahora, en este ejemplo, puede ver que hay
        ``str_wait_time`` en la línea 2, y ``wai_time`` en la línea 4 y ``wait_time`` en la
        línea 6. Si no tiene ojos muy agudos, es fácil pasar por alto que hay un
        error tipográfico en la línea 4.

**Encontrar pistas** Con errores de nombre, una de las mejores cosas que puede hacer es usar el
editor o función de búsqueda del navegador. Muy a menudo si busca la palabra exacta en el
mensaje de error ocurrirá una de dos cosas:

1. La palabra que está buscando aparecerá solo una vez en su código, también es probable
que estará en el lado derecho de una sentencia de asignación, o como un parámetro para
una función. Eso debería confirmar que tienes un error tipográfico en alguna parte. Si el nombre en
la pregunta **es** lo que pensaste que debería ser, entonces probablemente tengas un error tipográfico a la izquierda
de una sentencia de asignación en una línea antes de que aparezca su mensaje de error. Comience
mirando hacia atrás en sus sentencias de asignación. En algunos casos es realmente agradable
dejar visibles todas las cadenas resaltadas de la función de búsqueda, ya que ayudarán
a encpntrar muy rápidamente una línea donde podría haber esperado que su variable fuera
resaltada.

2. Lo segundo que puede pasar es que mirarás directamente a una línea
donde esperaba que la búsqueda encontrara la cadena en cuestión, pero no será
resaltado. Muy a menudo ese será el error tipográfico allí mismo.


Aquí hay otro más para que lo intentes:

.. activecode:: ac4_7_6

    n = input("¿Qué hora es ahora (en horas)?")
    n = imt(n)
    m = input("¿Cuántas horas quieres esperar?")
    m = int(m)
    q = m % 12
    print("Ahora la hora es", q)


.. reveal:: db_ex6_reveal
    :showtitle:  Muéstrame la Solución

    .. admonition:: Solución

        Este es una vez más un error tipográfico, pero el error tipográfico no está en un nombre variable, pero
        más bien, el nombre de una función. La estrategia de búsqueda te ayudaría con esto
        fácilmente, pero también hay otra pista para ti. El editor en el
        libro de texto, así como casi todos los editores de Python en el mundo le proporcionan
        pistas de color. Observe que en la línea 2 la función ``imt`` no está resaltada en
        azul como la palabra ``int`` en la línea 4.


Y un último pedazo de código para arreglar.

.. activecode:: ac4_7_7

    present_time = input("Ingrese la hora actual en horas:")
    set_alarm = input("Establecer las horas de alarma:")
    int (present_time, set_time, alarm_time)
    alarm_time = present_time + set_alarm
    print(alarm_time)

.. reveal:: db_ex7_reveal
    :showtitle: Muéstrame la Solución

    .. admonition:: Solución

        En este ejemplo, el mensaje de error se trata de ``set_time`` no definido en la línea 3.
        En este caso, el nombre indefinido no se usa en una sentencia de asignación, pero es
        usado como parámetro (incorrectamente) para una llamada a la función. Una búsqueda en ``set_time``
        revela que, de hecho, solo se usa una vez en el programa. ¿Quiso decir el autor?
        ``set_alarm``? Si hacemos esa suposición, obtenemos inmediatamente otro error
        ``NameError: el nombre 'alarm_time' no está definido en la línea: 3``. La variable
        ``alarm_time`` se define en la línea 4, pero eso no nos ayuda en la línea 3.
        Además, ahora tenemos que hacer la pregunta: ¿esta llamada a la función
        ``int(present_time, set_alarm, alarm_time)`` siquiera está haciendo uso correcto de la
        función ``int``? La respuesta a eso es un rotundo no. Hagamos una lista de todos las
        cosas mal con la línea 3:

        1.  ``set_time`` no está definido y nunca se usa, el autor probablemente quiso decir ``set_alarm``.
        2.  ``alarm_time`` no se puede usar como parámetro antes de que se defina, ¡incluso en la siguiente línea!
        3.  ``int`` solo puede convertir una cadena en un entero a la vez.
        4.  Finalmente, ``int`` debe usarse en una sentencia de asignación. Incluso si se llamara ``int`` con el número correcto de parámetros, no tendría ningún efecto real.


.. advanced topic!

.. present_time = int(input("Enter the present time(hhmm):"))
.. print type(present_time)

.. min = _ * 60
.. tot_min = min + [2, 4]
.. print(tot_min)
.. set_hrs = int(input("Enter the hours (hhmm):"))
.. alarm_time = present_time + set_hrs
.. print(alarm_time)


ValueError
^^^^^^^^^^

Se producen errores de valor cuando pasa un parámetro a una función y la función está
esperando ciertas limitaciones en los valores, y el valor pasado no es compatible.
Podemos ilustrar eso con el programa anterior de dos maneras diferentes.

.. código activo :: ac4_7_8

   current_time_str = input("¿Cuál es la hora actual (en horas 0-23)?")
   current_time_int = int(current_time_str)

   wait_time_str = input("¿Cuántas horas quieres esperar?")
   wait_time_int = int(wait_time_int)

   final_time_int = current_time_int + wait_time_int
   print(final_time_int)


Ejecute el programa, pero en lugar de escribir algo en el cuadro de diálogo, simplemente haga clic en Aceptar. Le
debería aparecer el siguiente mensaje de error:  ``ValueError: invalid literal for int() with
base 10: '' on line: 4`` Este error no se debe a que haya cometido un error en su
programa. Aunque a veces queremos verificar la entrada del usuario para asegurarnos de que sea válida,
pero todavía no tenemos todas las herramientas que necesitamos para eso. El error ocurre porque el
el usuario no nos dio algo que podamos convertir a un entero, en su lugar le dimos un
string vacío. Intenta ejecutar el programa nuevamente. Ahora esta vez ingrese "diez" en lugar de
el número 10. Recibirá un mensaje de error similar.

Los ValueErrors no siempre son causados por un error de entrada del usuario, pero en este programa ese es el
caso. Volveremos a ver ValueErrors nuevamente cuando lleguemos a programas más complicados.
Por ahora vale la pena repetir que debe realizar un seguimiento de las restricciones necesarias
para sus variables, y entender qué espera su función. Puede hacer esto
escribindo comentarios en su código, o nombrar sus variables de una manera en que le recuerden
su forma correcta