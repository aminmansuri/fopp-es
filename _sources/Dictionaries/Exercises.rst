..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

:skipreading:`True`

.. qnum::
   :prefix: dictionaries-8-
   :start: 1

Ejercicios
===========

#.
    .. tabbed:: q1

        .. tab:: Question

            .. actex:: ac10_8_1

               Predecir lo que se imprimirá del siguiente código. Si una línea causa un error de tiempo de ejecución, coméntelo y vea si el resto de sus predicciones fueron correctas.

               ~~~~

               d = {'apples': 15, 'grapes': 12, 'bananas': 35}
               print(d['banana'])
               d['oranges'] = 20
               print(len(d))
               print('grapes' in d)
               print(d['pears'])
               print(d.get('pears', 0))
               fruits = d.keys()
               print(fruits)
               del d['apples']
               print('apples' in d)

2. ¡Avast, prueba este, swabbies!

    .. tabbed:: q5

        .. tab:: Question

            .. actex:: ac10_8_2

               Aquí hay una tabla de traducciones del inglés al pirata

               .. table::
        
                  ==========  ==============
                  Inglés      Pirate
                  ==========  ==============
                  sir         matey
                  hotel       fleabag inn
                  student     swabbie
                  boy         matey
                  madam       proud beauty
                  professor   foul blaggart
                  restaurant  galley
                  your        yer
                  excuse      arr
                  students    swabbies
                  are         be
                  lawyer      foul blaggart
                  the         th'
                  restroom    head
                  my          me
                  hello       avast
                  is          be
                  man         matey
                  ==========  ==============

               Escriba un programa que le pida al usuario una oración en inglés y luego traduzca esa oración a Pirate.
               ~~~~

        .. tab:: Answer

            .. activecode:: answer10_8_2

                pirate = {}
                pirate['sir'] = 'matey'
                pirate['hotel'] = 'fleabag inn'
                pirate['student'] = 'swabbie'
                pirate['boy'] = 'matey'
                pirate['restaurant'] = 'galley'
                #and so on

                sentence = input("Por favor, introduzca una oración en English")

                psentence = []
                words = sentence.split()
                for aword in words:
                    if aword in pirate:
                        psentence.append(pirate[aword])
                    else:
                        psentence.append(aword)

                print(" ".join(psentence))

#. (ejercicio de desafío)

      .. tabbed:: q2

            .. tab:: Question

                  .. actex:: ac10_8_3

                     Escriba un programa que encuentre la palabra de 7 letras más utilizada en scarlet3.txt
                     ~~~~

                     f = open('scarlet3.txt', 'r')

            .. tab:: Answer

                  .. activecode:: answer10_8_3

                      f = open('scarlet3.txt', 'r')
                      contents = f.read()
                      d = {}

                      for w in contents.split():
                          if len(w) == 7:
                              if w not in d:
                                  d[w] = 1
                              else:
                                  d[w] = d[w] + 1

                      dkeys = d.keys()
                      most_used = dkeys[0]
                      for k in dkeys:
                          if d[k] > d[most_used]:
                              most_used = k

                      print("The most used word is '"+most_used+"', which is used "+str(d[most_used])+" times")

.. question:: dict_ex_4
   :number: 4

   .. tabbed:: q4

        .. tab:: Question

           .. actex:: ac10_8_4

               Escriba un programa que permita al usuario ingresar una cadena. Luego imprime un
               tabla de las letras del alfabeto en orden alfabético que ocurren en
               la cadena junto con la cantidad de veces que aparece cada letra. Caso debe
               ser ignorado. Una ejecución de muestra del programa podría verse así::
               
                   Please enter a sentence: ThiS is String with Upper and lower case Letters.
                   a  2
                   c  1
                   d  1
                   e  5
                   g  1
                   h  2
                   i  4
                   l  2
                   n  2
                   o  1
                   p  2
                   r  4
                   s  5
                   t  5
                   u  1
                   w  2
                   $
               ~~~~
               
        .. tab:: Answer

            .. activecode:: answer10_8_4

                x = input("Enter a sentence")

                x = x.lower()   # convert to all lowercase

                alphabet = 'abcdefghijklmnopqrstuvwxyz'

                letter_count = {} # empty dictionary
                for char in x:
                    if char in alphabet: # ignore any punctuation, numbers, etc
                        if char in letter_count:
                            letter_count[char] = letter_count[char] + 1
                        else:
                            letter_count[char] = 1

                keys = letter_count.keys()
                for char in sorted(keys):
                    print(char, letter_count[char])

        .. tab:: Discussion

            .. disqus::
                :shortname: interactivepython
                :identifier: disqus_de4f21e35d3a41a4a3ac4ac888f78d1a


.. datafile:: scarlet3.txt
   :fromfile: scarlet.txt
   :hide:
