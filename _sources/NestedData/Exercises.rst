..  Copyright (C) Lauren Murphy, Susan Doong, Haley Yaremych, Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

:skipreading:`True`

.. qnum::
   :prefix: nested-5-
   :start: 1

Ejercicios
==========

.. question:: q17_5_1

    .. tabbed:: q1

        .. tab:: Question


           .. actex:: ac17_5_1

              Itere a través de la lista de modo que si el carácter 'm' está en la cadena, se debe agregar a una nueva lista llamada ``m_list``. Sugerencia: Debido a que esto no es solo una lista de listas, piense en qué tipo de objeto desea que se almacenen sus datos. Los condicionales pueden ayudarlo.
              ~~~~

              d = ['good morning', 'hello', 'chair', 'python', ['music', 'flowers', 'facebook', 'instagram', 'snapchat', ['On my Own', 'monster', 'Words dont come so easily', 'lead me right']], 'Stressed Out', 'Pauver Coeur', 'Reach for Tomorrow', 'mariners song', 'Wonder sleeps here']

              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(m_list, ['good morning', 'music', 'instagram', 'On my Own', 'monster', 'Words dont come so easily', 'lead me right', 'Reach for Tomorrow', 'mariners song'], "Testing that m_list has the correct list assigned to it.")

              myTests().main()

.. question:: q17_5_2

    .. tabbed:: q2

        .. tab:: Question

           .. actex:: ac17_5_2

              El diccionario anidado, ``pokemon``, muestra el número de varios Pokémon que cada persona ha atrapado mientras jugaba Pokemon Go. Encuentre el número total de rattatas, dittos y pidgeys capturados y asigne a las variables ``r``, ``d`` y ``p`` respectivamente. No hagas *hardcode*. Nota: Tenga en cuenta que no todos los entrenadores han capturado un ditto.

              ~~~~

              pokemon = {'Trainer1':
                        {'normal': {'rattatas':15, 'eevees': 2, 'ditto':1}, 'water': {'magikarps':3}, 'flying': {'zubats':8, 'pidgey': 12}}, 
                        'Trainer2':
                        {'normal': {'rattatas':25, 'eevees': 1}, 'water': {'magikarps':7}, 'flying': {'zubats':3, 'pidgey': 15}}, 
                        'Trainer3':
                        {'normal': {'rattatas':10, 'eevees': 3, 'ditto':2}, 'water': {'magikarps':2}, 'flying': {'zubats':3, 'pidgey': 20}}, 
                        'Trainer4':
                        {'normal': {'rattatas':17, 'eevees': 1}, 'water': {'magikarps':9}, 'flying': {'zubats':12, 'pidgey': 14}}}


              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testSix(self):
                      self.assertEqual(r, 67, "Testing that r is assigned to correct value.")
                  def testSixB(self):
                      self.assertEqual(d, 3, "Testing that d is assigned to correct value.")
                  def testSixC(self):
                      self.assertEqual(p, 61, "Testing that p is assigned to correct value.")
     
              myTests().main()

.. question:: q17_5_3

    .. tabbed:: q3

        .. tab:: Question

           .. actex:: ac17_5_3

              A continuación, proporcionamos una lista anidada llamada ``big_list``. Use la iteración anidada para crear un diccionario, ``word_counts``, que contenga todas las palabras en ``big_list`` como claves, y la cantidad de veces que aparecen como valores.

              ~~~~

              big_list = [[['one', 'two'], ['seven', 'eight']], [['nine', 'four'], ['three', 'one']], [['two', 'eight'], ['seven', 'four']], [['five', 'one'], ['four', 'two']], [['six', 'eight'], ['two', 'seven']], [['three', 'five'], ['one', 'six']], [['nine', 'eight'], ['five', 'four']], [['six', 'three'], ['four', 'seven']]]

              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(sorted(word_counts.items()), sorted([('eight', 4), ('five', 3), ('four', 5), ('nine', 2), ('one', 4), ('seven', 4), ('six', 3), ('three', 3), ('two', 4)]), "Testing that word_counts was created correctly.")

              myTests().main() 

.. question:: q17_5_4

    .. tabbed:: q4

        .. tab:: Question

           .. actex:: ac17_5_4

              Se proporciona un diccionario que contiene datos de jugadores de pokemon go, donde cada jugador revela la cantidad de dulces que tiene cada uno de sus pokemon. Si reuniste todos los datos, ¿qué pokemon tiene la mayor cantidad de dulces? Asigna ese pokemon a la variable ``most_common_pokemon``.
              ~~~~

              pokemon_go_data = {'bentspoon': 
                                {'Rattata': 203, 'Pidgey': 120, 'Drowzee': 89, 'Squirtle': 35, 'Pikachu': 3, 'Eevee': 34, 'Magikarp': 300, 'Paras': 38}, 
                                'Laurne': 
                                {'Pidgey': 169, 'Rattata': 245, 'Squirtle': 9, 'Caterpie': 38, 'Weedle': 97, 'Pikachu': 6, 'Nidoran': 44, 'Clefairy': 15, 'Zubat': 79, 'Dratini': 4}, 
                                'picklejarlid':
                                {'Rattata': 32, 'Drowzee': 15, 'Nidoran': 4, 'Bulbasaur': 3, 'Pidgey': 56, 'Weedle': 21, 'Oddish': 18, 'Magmar': 6, 'Spearow': 14}, 
                                'professoroak': 
                                {'Charmander': 11, 'Ponyta': 9, 'Rattata': 107, 'Belsprout': 29, 'Seel': 19, 'Pidgey': 93, 'Shellder': 43, 'Drowzee': 245, 'Tauros': 18, 'Lapras': 18}}

              =====

              from unittest.gui import TestCaseGui

              class myTests(TestCaseGui):

                  def testOne(self):
                      self.assertEqual(most_common_pokemon, 'Rattata', "Testing that most_common_pokemon has the correct value.")

              myTests().main()
