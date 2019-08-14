..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: sequences-6-
   :start: 1

.. index::
   single: [ : ]; string slice
   slice; string

El Operador Slice
------------------

Una subcadena de una cadena se llama **slice**. Seleccionar un sector es similar a
seleccionar un caracter:

.. activecode:: ac5_6_1
    
    singers = "Peter, Paul, and Mary"
    print(singers[0:5])
    print(singers[7:11])
    print(singers[17:21])
    

El operador ``slice`` ``[n:m]`` devuelve la parte de la cadena que comienza
con el carácter en el índice ny
para arribar, pero *sin incluir* el carácter en el índice m.
O con un conteo normal desde 1, este es el carácter (n+1) hasta e incluir el carácter enésimo.

Si omite el primer índice (antes de los dos puntos), el corte comienza en el
comienzo del string. Si omite el segundo índice, el segmento va al
fin del string.

.. activecode:: ac5_6_2
    
    fruit = "banana"
    print(fruit[:3])
    print(fruit[3:])

¿Qué crees que significa ``fruit[:]``?

List Slices
===========

La operación slice que vimos con strings también funciona en listas. Recuerde que el primer índice es el punto de partida para el segmento y el segundo número es un índice más allá del final del segmento (hasta pero sin incluir ese elemento). Recordemos también
que si omite el primer índice (antes de los dos puntos), el corte comienza en el
comienzo de la secuencia. Si omite el segundo índice, el segmento va al
fin de la secuencia.

.. activecode:: ac5_6_3
    
    a_list = ['a', 'b', 'c', 'd', 'e', 'f']
    print(a_list[1:3])
    print(a_list[:4])
    print(a_list[3:])
    print(a_list[:])


Tuple Slices
============

No podemos modificar los elementos de un tuple, pero podemos hacer que una variable haga referencia a un nuevo tuple que contenga información diferente.
Afortunadamente, también podemos usar la operación de corte en tuples, así como strings y lists. Para construir el nuevo tuple, podemos aplicar
slice en partes del antiguo tuple y unir los pedazos para hacer el nuevo tuple. Entonces ``julia`` tiene una nueva película reciente, y podríamos
querer cambiar su tuple. Podemos cortar fácilmente las partes que queremos y concatenarlas con el nuevo tuple.

.. activecode:: ac5_6_4

    julia = ("Julia", "Roberts", 1967, "Duplicity", 2009, "Actress", "Atlanta, Georgia")
    print(julia[2])
    print(julia[2:6])

    print(len(julia))

    julia = julia[:3] + ("Eat Pray Love", 2010) + julia[5:]
    print(julia)



**Revisa tu entendimiento**

.. mchoice:: question5_6_1
   :answer_a: python
   :answer_b: rocks
   :answer_c: hon r
   :answer_d: Error, no puedes tener dos números dentro de [ ].
   :correct: c
   :feedback_a: Eso sería s[0:6].
   :feedback_b: Eso sería be s[7:].
   :feedback_c: Sí, comienza con el carácter en el índice 3 y sube pero no incluye el carácter en el índice 8.
   :feedback_d: Esto se llama sciling *rebanar*, no indexar. Requiere un comienzo y un final.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?
   
   .. code-block:: python

      s = "python rocks"
      print(s[3:8])

.. mchoice:: question5_6_2
   :answer_a: [ [ ], 3.14, False]
   :answer_b: [ [ ], 3.14]
   :answer_c: [ [56, 57, "dog"], [ ], 3.14, False]
   :correct: a
   :feedback_a: Sí, el segmento comienza en el índice 4 y sube e incluye el último elemento.
   :feedback_b: Al omitir el límite superior en el segmento, subimos e incluimos el último elemento.
   :feedback_c: Los valores del índice comienzan en 0.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?
   
   .. code-block:: python
   
     alist = [3, 67, "cat", [56, 57, "dog"], [ ], 3.14, False]
     print(alist[4:])

.. activecode:: ac5_6_5
   :language: python
   :autograde: unittest
   :practice: T

   Cree una nueva lista utilizando los elementos noveno a duodécimo (cuatro elementos en total) de ``new_lst`` y asígnela a la variable ``sub_lst``.
   ~~~~
   new_lst = ["computer", "luxurious", "basket", "crime", 0, 2.49, "institution", "slice", "sun", ["water", "air", "fire", "earth"], "games", 2.7, "code", "java", ["birthday", "celebration", 1817, "party", "cake", 5], "rain", "thunderstorm", "top down"]

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(sub_lst, new_lst[8:12], "Testing that sub_lst has the correct elements assigned.")

   myTests().main()
