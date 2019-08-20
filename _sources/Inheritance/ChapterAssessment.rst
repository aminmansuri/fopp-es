..  Copyright (C)  Lauren Murphy, Jaclyn Cohen, Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

Evaluación del Capítulo
========================

.. activecode:: ee_inheritance_01
   :tags: Inheritance/inheritVarsAndMethods.rst
   :practice: T
   :topics: Inheritance/inheritVarsAndMethods

   La clase, ``Pokemon``, se proporciona a continuación y describe un Pokémon y sus características de nivelación y evolución. Una instancia de la clase es un pokemon que creas.

   ``Grass_Pokemon`` es una subclase que hereda de ``Pokemon`` pero cambia algunos aspectos, por ejemplo, los valores de impulso son diferentes.

   Para la subclase ``Grass_Pokemon``, agregue otro método llamado ``action`` que devuelve la cadena ``"[name of pokemon] conoce muchos movimientos diferentes!"``. Cree una instancia de esta clase con el ``name`` como ``"Belle"``. Asigne esta instancia a la variable ``p1``.
   ~~~~
   class Pokemon(object):
       attack = 12
       defense = 10
       health = 15
       p_type = "Normal"
    
       def __init__(self, name, level = 5):
           self.name = name
           self.level = level
       
       def train(self):
           self.update()
           self.attack_up()
           self.defense_up()
           self.health_up()
           self.level = self.level + 1
           if self.level%self.evolve == 0:
               return self.level, "Evolved!"
           else:
               return self.level
    
       def attack_up(self):
           self.attack = self.attack + self.attack_boost
           return self.attack
    
       def defense_up(self):
           self.defense = self.defense + self.defense_boost
           return self.defense
    
       def health_up(self):
           self.health = self.health + self.health_boost
           return self.health

       def update(self):
           self.health_boost = 5
           self.attack_boost = 3
           self.defense_boost = 2
           self.evolve = 10
        
       def __str__(self):
           self.update()
           return "Pokemon name: {}, Type: {}, Level: {}".format(self.name, self.p_type, self.level)

   class Grass_Pokemon(Pokemon):
       attack = 15
       defense = 14
       health = 12
    
       def update(self):
           self.health_boost = 6
           self.attack_boost = 2
           self.defense_boost = 3
           self.evolve = 12
        
       def moves(self):
           self.p_moves = ["razor leaf", "synthesis", "petal dance"]


   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOneA(self):
         self.assertEqual(p1.action(), "Belle knows a lot of different moves!", "Testing that action method is correct and p1 assigned to correct value")
      
   myTests().main()

.. activecode:: ee_inheritance_02
   :tags: Inheritance/inheritVarsAndMethods.rst, Inheritance/OverrideMethods.rst
   :practice: T
   :topics: Inheritance/OverrideMethods

   Modifique la subclase ``Grass_Pokemon`` para que la fuerza de ataque para las instancias de ``Grass_Pokemon`` no cambie hasta que alcancen el nivel 10. En el nivel 10 y más, su fuerza de ataque debería aumentar en la cantidad de ``attack_boost`` cuando son entrenados.

   Para probar, cree una instancia de la clase con el nombre como ``"Bulby"``. Asigne la instancia a la variable ``p2``. Cree otra instancia de la clase ``Grass_Pokemon`` con el nombre establecido en ``"Pika"`` y asigne esa instancia a la variable ``p3``. Luego, use los métodos ``Grass_Pokemon`` para entrenar la instancia ``p3`` ``Grass_Pokemon`` hasta que alcance al menos el nivel 10.
   ~~~~
   class Pokemon(object):
       attack = 12
       defense = 10
       health = 15
       p_type = "Normal"
    
       def __init__(self, name, level = 5):
           self.name = name
           self.level = level
       
       def train(self):
           self.update()
           self.attack_up()
           self.defense_up()
           self.health_up()
           self.level = self.level + 1
           if self.level%self.evolve == 0:
               return self.level, "Evolved!"
           else:
               return self.level
    
       def attack_up(self):
           self.attack = self.attack + self.attack_boost
           return self.attack
    
       def defense_up(self):
           self.defense = self.defense + self.defense_boost
           return self.defense
    
       def health_up(self):
           self.health = self.health + self.health_boost
           return self.health

       def update(self):
           self.health_boost = 5
           self.attack_boost = 3
           self.defense_boost = 2
           self.evolve = 10
        
       def __str__(self):
           return "Pokemon name: {}, Type: {}, Level: {}".format(self.name, self.p_type, self.level)

   class Grass_Pokemon(Pokemon):
       attack = 15
       defense = 14
       health = 12
       p_type = "Grass"
    
       def update(self):
           self.health_boost = 6
           self.attack_boost = 2
           self.defense_boost = 3
           self.evolve = 12
        
       def moves(self):
           self.p_moves = ["razor leaf", "synthesis", "petal dance"]
           

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOneA(self):
         self.assertEqual(p2.__str__(), "Pokemon name: Bulby, Type: Grass, Level: 5", "Testing that p2 is assigned to correct value.")
      def testOneB(self):
         self.assertTrue(p3.attack_up() >= 17, "Testing that attack value is assigned to correct value at level 10.")
      
   myTests().main()

.. activecode:: ee_inheritance_05
   :tags: Inheritance/inheritVarsAndMethods.rst

   Junto con la clase principal ``Pokemon``, también hemos proporcionado varias subclases. Escriba otro método en la clase principal que las subclases heredarán. Llámalo ``opponent``. Debería devolver contra qué tipo de pokemon el tipo actual es débil y fuerte, como una tupla.

   - **Hierba** es débil contra *Fuego* y fuerte contra *Agua*
   - **Fantasma** es débil contra *Oscuro* y fuerte contra *Psíquico*
   - **Fuego** es débil contra *Agua* y fuerte contra *Hierba*
   - **Volador** es débil contra *Eléctrico* y fuerte contra *Lucha*

   Por ejemplo, si el ``p_type`` de la subclase es ``'Grass'``, ``.opponent()`` debería devolver la tupla ``('Fire', 'Water')``
   ~~~~
   class Pokemon():
       attack = 12
       defense = 10
       health = 15
       p_type = "Normal"
    
       def __init__(self, name,level = 5):
           self.name = name
           self.level = level
           self.weak = "Normal"
           self.strong = "Normal"
    
       def train(self):
           self.update()
           self.attack_up()
           self.defense_up()
           self.health_up()
           self.level = self.level + 1
           if self.level%self.evolve == 0:
               return self.level, "Evolved!"
           else:
               return self.level
    
       def attack_up(self):
           self.attack = self.attack + self.attack_boost
           return self.attack
    
       def defense_up(self):
           self.defense = self.defense + self.defense_boost
           return self.defense
    
       def health_up(self):
           self.health = self.health + self.health_boost
           return self.health

       def update(self):
           self.health_boost = 5
           self.attack_boost = 3
           self.defense_boost = 2
           self.evolve = 10
        
       def __str__(self):
           self.update()
           return "Pokemon name: {}, Type: {}, Level: {}".format(self.name, self.p_type, self.level)

   class Grass_Pokemon(Pokemon):
       attack = 15
       defense = 14
       health = 12
       p_type = "Grass"
    
       def update(self):
           self.health_boost = 6
           self.attack_boost = 2
           self.defense_boost = 3
           self.evolve = 12
    
   class Ghost_Pokemon(Pokemon):
       p_type = "Ghost"
        
       def update(self):
           self.health_boost = 3
           self.attack_boost = 4
           self.defense_boost = 3
        
   class Fire_Pokemon(Pokemon):
       p_type = "Fire"

   class Flying_Pokemon(Pokemon):
       p_type = "Flying"
  
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOneA(self):
         self.assertEqual(Grass_Pokemon("Buggy").opponent(), ("Fire", "Water"), "Testing that Grass weak and strong are assigned to correct values.")
      def testOneB(self):
         self.assertEqual(Fire_Pokemon("Buggy").opponent(), ("Water", "Grass"), "Testing that Fire weak and strong are assigned to correct values.")
      def testOneC(self):
         self.assertEqual(Ghost_Pokemon("Buggy").opponent(), ("Dark", "Psychic"), "Testing that Ghost weak and strong are assigned to correct values.")
      def testOneD(self):
         self.assertEqual(Flying_Pokemon("Buggy").opponent(), ("Electric", "Fighting"), "Testing that Flying weak and strong are assigned to correct values.")

   myTests().main()


