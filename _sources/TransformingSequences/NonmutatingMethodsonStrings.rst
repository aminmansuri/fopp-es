..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: seqmut-8-
   :start: 1

Métodos no mutantes en Strings
===============================

Hay una amplia variedad de métodos para objetos de cadena.
Prueba el siguiente programa.

.. activecode:: ac8_8_1

    ss = "Hello, World"
    print(ss.upper())

    tt = ss.lower()
    print(tt)
    print(ss)

En este ejemplo, ``upper`` es un método que se puede invocar en cualquier objeto de cadena para crear una nueva cadena
en el que todos los caracteres están en mayúsculas. ``lower`` funciona de manera similar cambiando todos
caracteres en la cadena a minúsculas. (La cadena original ``ss`` permanece sin cambios. Una nueva cadena
``tt`` es creada.)

.. _string_methods:

Ya has visto algunos métodos, como ``count`` e ``index``, que funcionan con cadenas y son
no mutantes además de esos y ``upper`` y ``lower``, la siguiente tabla proporciona un resumen
de algunos métodos útiles. Hay algunos ejemplos de código activo que siguen para que pueda probarlos.


==========  ==============      ==================================================================
Métodos     Parámetros          Descripción
==========  ==============      ==================================================================
upper       none                Devuelve una cadena en mayúsculas
lower       none                Devuelve una cadena en minúsculas
count       item                Devuelve el número de ocurrencias del artículo.
index       item                Devuelve el índice más a la izquierda donde se encuentra el elemento de subcadena y causa								a runtime error if item is not found
strip       none                Devuelve una cadena con el espacio en blanco inicial y final eliminado
replace     old, new            Reemplaza todas las apariciones de subcadenas antiguas por nuevas
format      substitutions       Ve a :ref:`Format-Strings`, más abajo
==========  ==============      ==================================================================

Debe experimentar con estos métodos para comprender lo que hacen. Tenga en cuenta una vez más que los métodos que devuelven cadenas no cambian el original. También puedes consultar la
`Documentación de Python para Strings <http://docs.python.org/3/library/stdtypes.html#string-methods>`_.

.. activecode:: ac8_8_2

    ss = "    Hello, World    "

    els = ss.count("l")
    print(els)

    print("***"+ss.strip()+"***")

    news = ss.replace("o", "***")
    print(news)


.. activecode:: ac8_8_3


    food = "banana bread"
    print(food.upper())


**Revisa tu entendimiento**

.. mchoice:: question8_8_1
   :answer_a: 0
   :answer_b: 2
   :answer_c: 3
   :correct: c
   :feedback_a: Definitivamente hay caracteres o y p.
   :feedback_b: Hay 2 caracteres o pero ¿qué pasa con p?
   :feedback_c: Sí, sume el número de caracteres o y el número de caracteres p.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?
   
   .. code-block:: python
   
      s = "python rocks"
      print(s.count("o") + s.count("p"))

.. mchoice:: question8_8_2
   :answer_a: yyyyy
   :answer_b: 55555
   :answer_c: n
   :answer_d: Error, no puedes combinar todas esas cosas juntas.
   :correct: a
   :feedback_a: Sí, s[1] es y y el índice de n es 5, entonces 5 caracteres. Es importante darse cuenta de que el método de índice tiene prioridad sobre el operador de repetición. La repetición se hace al final.
   :feedback_b: Cerca. 5 no se repite, es el número de veces que se repite.
   :feedback_c: Esta expresión usa el índice de n
   :feedback_d: Esto está bien, el operador de repetición utilizó el resultado de la indexación y el método de indexación.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?
   
   .. code-block:: python
   
      s = "python rocks"
      print(s[1]*s.index("n"))

.. _Format-Strings:

Método String Format
~~~~~~~~~~~~~~~~~~~~~

Hasta ahora, hemos creado cadenas con contenido variable utilizando el operador + para concatenar
cuerdas parciales juntas. Eso funciona, pero es muy difícil para las personas leer o depurar un código
línea que incluye nombres y cadenas de variables y expresiones complejas. Considera lo siguiente:

.. activecode:: ac8_8_4

   name = "Rodney Dangerfield"
   score = -1  # No respect!
   print("Hello " + name + ". Your score is " + str(score))

O quizás de manera más realista:
 
.. activecode:: ac8_8_5
 
   scores = [("Rodney Dangerfield", -1), ("Marlon Brando", 1), ("You", 100)]
   for person in scores:
       name = person[0]
       score = person[1]
       print("Hello " + name + ". Your score is " + str(score))

En esta sección, aprenderá a escribir eso de una manera más legible:

.. activecode:: ac8_8_6
 
   scores = [("Rodney Dangerfield", -1), ("Marlon Brando", 1), ("You", 100)]
   for person in scores:
       name = person[0]
       score = person[1]
       print("Hello {}. Your score is {}.".format(name, score))

En las pruebas de la escuela primaria, una convención común es usar espacios en blanco. Por ejemplo,

    Hello _____!


y puede completar el nombre de la persona saludada y combinar el texto dado con una inserción.
*Usamos esto como una analogía:* Python tiene una construcción similar, mejor llamada
rellenar las llaves. El método de cadena ``format``, hace sustituciones en lugares en una cadena
encerrada entre llaves. Ejecute este código:

.. activecode:: ac8_8_7

    person = input('Your name: ')
    greeting = 'Hello {}!'.format(person) 
    print(greeting)


¡Hay varias ideas nuevas aquí!

La cadena para el método ``formato`` tiene una forma especial, con llaves incorporadas.
Tal cadena se llama *format String*. Los lugares donde las llaves están incrustadas son reemplazadas
por el valor de una expresión tomado de la lista de parámetros para el método ``format``. Hay muchas
variaciones en la sintaxis entre las llaves. En este caso usamos
la sintaxis donde la primera (y única) ubicación en la cadena con
Las llaves tienen una sustitución hecha del primer (y único) parámetro.

En el código anterior, esta nueva cadena se asigna al identificador
``greeting``, y luego se imprime la cadena.

El identificador ``greeting`` se introdujo para dividir las operaciones en una secuencia más clara de
pasos. Sin embargo, dado que el valor de ``greeting`` solo se hace referencia una vez, se puede eliminar
con la versión más concisa:

.. activecode:: ac8_8_8

    person = input('Enter your name: ') 
    print('Hello {}!'.format(person)) 

Puede haber múltiples sustituciones, con datos de cualquier tipo.
A continuación usamos floats. Pruebe el precio original $2.50 con un 7% de descuento:

.. activecode:: ac8_8_9

    origPrice = float(input('Enter the original price: $')) 
    discount = float(input('Enter discount percentage: ')) 
    newPrice = (1 - discount/100)*origPrice
    calculation = '${} discounted by {}% is ${}.'.format(origPrice, discount, newPrice)
    print(calculation)

Es importante pasar los argumentos al método ``format`` en el orden correcto, porque
se combinan *posicionalmente* en los lugares ``{}`` para la interpolación donde hay más de uno.

Si utilizó los datos sugeridos, este resultado no es satisfactorio.
Los precios deben aparecer exactamente con dos lugares más allá del punto decimal,
pero esa no es la forma predeterminada de mostrar flotantes.

Las cadenas de formato pueden proporcionar más información dentro de las llaves
mostrando cómo formatear datos especialmente.
En particular, los flotadores se pueden mostrar con un número específico de lugares decimales.
Para dos lugares decimales, ponga ``:.2f`` dentro de las llaves para los valores monetarios:

.. activecode:: ac8_8_10

    origPrice = float(input('Enter the original price: $')) 
    discount = float(input('Enter discount percentage: ')) 
    newPrice = (1 - discount/100)*origPrice
    calculation = '${:.2f} discounted by {}% is ${:.2f}.'.format(origPrice, discount, newPrice)
    print(calculation)

El 2 en el modificador de formato se puede reemplazar por otro entero para redondear a ese
Número especificado de dígitos.

Este tipo de cadena de formato depende directamente del orden de
parámetros para el método de formato. Hay otros enfoques que haremos
omita aquí, como numerar explícitamente sustituciones.

También es importante que le dé a ``formato`` la misma cantidad de argumentos que hay ``{}`` esperando la interpolación en la cadena. Si tiene un ``{}`` en una cadena para la que no pasa argumentos, es posible que no obtenga un error, pero verá un valor extraño ``indefinido`` que probablemente no tenía la intención de insertar de repente en su cadena . Puedes ver un ejemplo a continuación.

Por ejemplo,

.. activecode:: ac8_8_11
 
   name = "Sally"
   greeting = "Nice to meet you"
   s = "Hello, {}. {}."

   print(s.format(name,greeting)) # will print Hello, Sally. Nice to meet you.

   print(s.format(greeting,name)) # will print Hello, Nice to meet you. Sally. 

   print(s.format(name)) # 2 {}s, only one interpolation item! Not ideal.


Un punto técnico: como las llaves tienen un significado especial en una cadena de formato, debe haber un
regla especial si desea incluir llaves en la cadena final *formateada*. los
la regla es duplicar las llaves: ``{{`` y ``}}``. Por ejemplo, la notación de conjuntos matemáticos utiliza
tirantes. Las llaves dobles iniciales y finales en la siguiente cadena de formato generan literal
llaves en la cadena formateada::

    a = 5
    b = 9
    setStr = 'The set is {{{}, {}}}.'.format(a, b)
    print(setStr)

Desafortunadamente, al momento de escribir esto, la implementación del formato ActiveCode tiene un error,
imprimir llaves dobladas, pero las impresiones estándar de Python ``{5, 9}``.

.. mchoice:: question8_8_3
   :answer_a: Nothing - it causes an error
   :answer_b: sum of {} and {} is {}; product: {}. 2 6 8 12
   :answer_c: sum of 2 and 6 is 8; product: 12.
   :answer_d: sum of {2} and {6} is {8}; product: {12}.
   :correct: c
   :feedback_a: It is legal format syntax:  put the data in place of the braces.
   :feedback_b: Put the data into the format string; not after it.
   :feedback_c: Yes, correct substitutions!
   :feedback_d: Close:  REPLACE the braces.
   :practice: T


   ¿Qué se imprime en las siguientes declaraciones?
   
   .. code-block:: python
   
       x = 2
       y = 6
       print('sum of {} and {} is {}; product: {}.'.format( x, y, x+y, x*y))


.. mchoice:: question8_8_4
   :answer_a: 2.34567 2.34567 2.34567
   :answer_b: 2.3 2.34 2.34567
   :answer_c: 2.3 2.35 2.3456700
   :correct: c
   :feedback_a: Los números antes de la f en las llaves dan el número de dígitos para mostrar después del punto decimal.
   :feedback_b: Cierra, pero redondea al número de dígitos y muestra el número completo de dígitos especificado.
   :feedback_c: Sí, ¡número correcto de dígitos con redondeo!
   :practice: T
   

   ¿Qué se imprime en las siguientes declaraciones?
   
   .. code-block:: python
   
       v = 2.34567
       print('{:.1f} {:.2f} {:.7f}'.format(v, v, v))
