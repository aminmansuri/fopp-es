..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: dictionaries-5-
   :start: 1

Introducción: Acumulando Múltiples Resultados en un Diccionario
================================================================

Ya has visto el patrón del acumulador; pasa por los elementos en una secuencia,
actualizar una variable acumuladora cada vez. En lugar de acumular un solo resultado, es
posible acumular muchos resultados. Supongamos, por ejemplo, que quisiéramos averiguar qué
las letras se usan con mayor frecuencia en inglés.

Supongamos que tenemos un texto razonablemente largo que pensamos que es representativo del inglés general
uso. Para nuestros propósitos en este capítulo, utilizaremos el texto de la historia de Sherlock Holmes,
"Un estudio en escarlata", por Sir Arthur Conan Doyle. El texto en realidad incluye algunos
líneas sobre la fuente de la transcripción (Proyecto Gutenberg), pero esas no
afectará materialmente nuestros análisis, por lo que los dejaremos dentro. Puede acceder a este texto
dentro de este capítulo con el código ``open('scarlet.txt', 'r')``.

.. raw:: html
   
   <div class="alert alert-info">
   <p>As with other files that we access in this textbook environment, this one is actually pre-loaded in your browser, not retrieved from your computer's file system. That's why this chapter may be a little slower to load than others. You can view the text of "A Study in Scarlet" at the <a href="#scarlet.txt">bottom of the page.</a></p>
   </div>

Si queremos averiguar con qué frecuencia aparece la letra 't', podemos acumular el resultado
en una variable de conteo.

.. activecode:: ac10_5_1

   f = open('scarlet.txt', 'r')
   txt = f.read()
   # now txt is one long string containing all the characters
   t_count = 0 #initialize the accumulator variable
   for c in txt:
       if c == 't':
           t_count = t_count + 1   #increment the counter
   print("t: " + str(t_count) + " occurrences")  

Podemos acumular conteos para más de un carácter a medida que recorremos el texto.
Supongamos, por ejemplo, que deseamos comparar los recuentos de 't' y 's' en el texto.

.. activecode:: ac10_5_2

   f = open('scarlet.txt', 'r')
   txt = f.read()
   # now txt is one long string containing all the characters
   t_count = 0 #initialize the accumulator variable
   s_count = 0 # initialize the s counter accumulator as well
   for c in txt:
       if c == 't':
           t_count = t_count + 1   #increment the t counter
       elif c == 's':
           s_count = s_count + 1
   print("t: " + str(t_count) + " occurrences") 
   print("s: " + str(s_count) + " occurrences")
   
OK, pero puedes ver que esto se volverá tedioso si intentamos acumular conteos
para todas las letras Tendremos que inicializar muchos acumuladores, y habrá
ser una declaración muy larga if..elif..elif. Usando un diccionario, podemos hacerlo mucho mejor.

Un diccionario puede contener todas las variables del acumulador. Cada clave en el diccionario
será una letra, y el valor correspondiente será el recuento hasta ahora de cuántas veces esa letra ha aparecido.

.. activecode:: ac10_5_3

   f = open('scarlet.txt', 'r')
   txt = f.read()
   # now txt is one long string containing all the characters
   x = {} # start with an empty dictionary
   x['t'] = 0  # initialize the t counter
   x['s'] = 0  # initialize the s counter
   for c in txt:
       if c == 't':
           x['t'] = x['t'] + 1  # increment the t counter
       elif c == 's':
           x['s'] = x['s'] + 1  # increment the s counter

   print("t: " + str(x['t']) + " occurrences")
   print("s: " + str(x['s']) + " occurrences")

Esto realmente no ha mejorado aún las cosas, pero mira de cerca las líneas 8-11 en el código anterior.
Independientemente del caracter que estemos viendo, t o s, estamos incrementando el contador para ese
personaje. Entonces, las líneas 9 y 11 realmente podrían ser las mismas.

.. activecode:: ac10_5_4

   f = open('scarlet.txt', 'r')
   txt = f.read()
   # now txt is one long string containing all the characters
   x = {} # start with an empty dictionary
   x['t'] = 0  # intiialize the t counter
   x['s'] = 0  # initialize the s counter
   for c in txt:
       if c == 't':
           x[c] = x[c] + 1   # increment the t counter
       elif c == 's':
           x[c] = x[c] + 1   # increment the s counter

   print("t: " + str(x['t']) + " occurrences")
   print("s: " + str(x['s']) + " occurrences")

Las líneas 9 y 11 anteriores pueden parecer un poco confusas al principio. Anteriormente, nuestra tarea
declaraciones referidas directamente a las claves, con ``x['s']`` y ``x['t']``. Aquí nosotros
solo están usando una variable ``c`` cuyo valor es 's' o 't', o algún otro caracter.

Si eso tiene perfecto sentido para usted, omita los siguientes dos párrafos. De lo contrario, sigue leyendo.
Analicemos esa línea con un poco más de detalle.

Primero, tenga en cuenta que, como con todos
declaraciones de asignación, el lado derecho se evalúa primero. En este caso, ``x[c]`` tiene que ser
evaluado. Como con todas las expresiones, primero tenemos que sustituir valores por nombres de variables.
``x`` es una variable vinculada a un diccionario. ``c`` es una variable vinculada a una letra del
cadena a la que está vinculado ``txt`` (eso es lo que dice la instrucción for:
ejecute las líneas 8-11 una vez para cada carácter en txt, con la variable c vinculada al carácter actual
en cada iteración.) Entonces, supongamos que el carácter actual es la letra ``s`` (estamos en la línea 11).
Entonces ``x[c]`` busca el valor asociado con la clave 's' en el diccionario x. Si todo funciona correctamente,
ese valor debe ser el número de veces que se ha aparecido 's' anteriormente. En aras de la discusión, supongamos que es 25.
Entonces el lado derecho evalúa a 25 + 1, 26. Mira este juego a continuación.

.. showeval:: eval10_5_4
   :trace_mode: true

   f = open('scarlet.txt', 'r')
   txt = f.read()
   # now txt is one long string containing all the characters
   x = {} # start with an empty dictionary
   x['t'] = 15  # intiialize the t counter
   x['s'] = 25  # initialize the s counter
   ~~~~
   for {{c}}{{'s'}} in txt: # we have reached the 26th s now
   {{for 's' in txt:}}{{if c == 't'}}
       if {{c}}{{'s'}} == 't':
       {{if 's' == 't':}}{{elif c == 's':}}
       elif {{c}}{{'s'}} == 's':
       {{elif 's' == 's':}}{{x[c] = x[c] + 1   # increment the s counter}}
           x[{{c] = x[c}}{{'s'] = x['s'}}] + 1   # increment the s counter
           x['s'] = {{x['s']}}{{25}} + 1   # increment the s counter
           x['s'] = {{25 + 1}}{{26}}   # increment the s counter


Ahora hemos asignado el valor 26 a ``x[c]``. Es decir, en el diccionario x, establecemos el valor asociado con el
clave 's' (el valor actual de la variable c) para ser 26. En otras palabras, hemos incrementado el valor asociado con
la clave 's' del 25 al 26.

Podemos hacerlo mejor aún. Otra cosa buena de usar un diccionario es que no tenemos que especificar previamente
cuáles serán todas las letras. En este caso, sabemos de antemano para qué sirve el alfabeto
El inglés es, pero más adelante en el capítulo contaremos las ocurrencias de las palabras, y
No sabemos de antemano todas las palabras que pueden usarse. En lugar de preespecificar
para qué letras debe contar el acumulador, podemos comenzar con un diccionario vacío y
agregue un contador al diccionario cada vez que nos encontremos con algo nuevo que queremos
comience a contar.

.. _accumulating_counts:

.. activecode:: ac10_5_5

   f = open('scarlet.txt', 'r')
   txt = f.read()
   # now txt is one long string containing all the characters
   x = {} # start with an empty dictionary
   for c in txt:
       if c not in x:
           # we have not seen this character before, so initialize a counter for it
           x[c] = 0
      
       #whether we've seen it before or not, increment its counter
       x[c] = x[c] + 1

   print("t: " + str(x['t']) + " occurrences")
   print("s: " + str(x['s']) + " occurrences")

Tenga en cuenta que en el ciclo for, ya no necesitamos preguntar explícitamente si el actual
La letra es una 's' o 't'. El paso de incremento en la línea 11 funciona para el contador
asociado con cualquiera que sea el carácter actual. Nuestro código ahora se está acumulando
cuenta para todas las letras, no solo 's' y 't'.

**Revisa tu entendimiento**

.. mchoice:: question10_5_1
   :answer_a: print txt['e'] > txt['t']
   :answer_b: print x['e'] > x['t']
   :answer_c: print x[e] > x[t]
   :answer_d: print x[c] > txt[c]
   :answer_e: print e[x] > t[x]
   :feedback_a: txt es la variable que tiene el texto original, no el diccionario de recuentos.
   :feedback_b: x es el diccionario de recuentos; desea comparar los valores asociados con 'e' y 't'.
   :feedback_c: x es el diccionario de recuentos, pero no desea evaluar e y t como variables para determinar qué claves buscar en el diccionario.
   :feedback_d: Parece que tal vez estás adivinando. Por favor revise el material anterior e intente nuevamente.
   :feedback_e: Parece que has invertido las cosas. La variable que se refiere al diccionario va fuera de los corchetes; la llave que estás buscando va adentro.
   :correct: b

   ¿Cuál de las siguientes opciones imprimirá True si hay más ocurrencias de e que t en
   el texto A Study in Scarlet, y False si t ocurrió con más frecuencia (suponiendo que el código anterior, de dict_accum_5,
   ya fue ejecutado.)


Tenga en cuenta que las declaraciones de impresión al final seleccionan las teclas específicas 't' y 's'. Nosotros
podemos generalizar eso, también, para imprimir los recuentos de ocurrencias para todos
los caracteres, usando un bucle for para iterar a través de las claves en x.

.. activecode:: ac10_5_6

   f = open('scarlet.txt', 'r')
   txt = f.read()
   # now txt is one long string containing all the characters
   letter_counts = {} # start with an empty dictionary
   for c in txt:
       if c not in letter_counts:
           # we have not seen this character before, so initialize a counter for it
           letter_counts[c] = 0
      
       #whether we've seen it before or not, increment its counter
       letter_counts[c] = letter_counts[c] + 1

   for c in letter_counts.keys():
       print(c + ": " + str(letter_counts[c]) + " occurrences")
   
Tenga en cuenta que solo se muestran las letras que realmente aparecen en el texto. Algunos
signos de puntuación que son posibles en inglés, pero que nunca se utilizaron en
texto, se omiten por completo. La línea en blanco a la mitad de la salida puede sorprenderlo.
Eso en realidad dice que el carácter de nueva línea, ``\\n``, aparece 5155 veces en
el texto. En otras palabras, hay 5155 líneas de texto en el archivo. Vamos
prueba esa hipótesis.


.. activecode:: ac10_5_7

   f = open('scarlet.txt', 'r')
   txt_lines = f.readlines()
   # now txt_lines is a list, where each item is one
   # line of text from the story
   print(len(txt_lines))
   print(txt_lines[70:85])

Ahora, aquí hay algunos problemas adicionales para probar.

.. activecode:: ac10_5_8
   :language: python
   :autograde: unittest
   :practice: T

   **2.** Se proporciona una cadena guardada en el nombre de la variable ``sentence``. Divida la cadena en una lista de palabras, luego cree un diccionario que contenga cada palabra y la cantidad de veces que ocurra. Guarde este diccionario en el nombre de la variable ``word_counts``.
   ~~~~
   sentence = "The dog chased the rabbit into the forest but the rabbit was too quick."

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(sorted(word_counts.items()), sorted([('The', 1), ('dog', 1), ('chased', 1), ('the', 3), ('rabbit', 2), ('into', 1), ('forest', 1), ('but', 1), ('was', 1), ('too', 1), ('quick.', 1)]), "Testing that word_counts was created correctly.")

   myTests().main()

.. activecode:: ac10_5_9
   :language: python
   :autograde: unittest
   :practice: T

   **3.** Cree un diccionario llamado ``char_d`` a partir de la cadena ``stri``, de modo que la clave sea un carácter y el valor sea cuántas veces se produce.
   ~~~~
   stri = "what can I do"

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(sorted(char_d.items()), sorted([('w', 1), ('h', 1), ('a', 2), ('t', 1), (' ', 3), ('c', 1), ('n', 1), ('I', 1), ('d', 1), ('o', 1)]), "Testing that char_d has been created correctly.")

   myTests().main()


.. datafile:: scarlet.txt
   :fromfile: scarlet.txt
   :hide: