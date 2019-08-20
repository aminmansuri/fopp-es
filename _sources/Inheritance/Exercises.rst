..  Copyright (C)  Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

:skipreading:`True`

Ejercicios
===========

Para ejercitarte, puedes expandir el juego Tamagotchi aún más. Prueba estos.

Aquí está *todo* el código que acabamos de ver para nuestro juego nuevo y mejorado, con algunas adiciones. Puedes ejecutar esto y volver a jugar.
#.

    .. tabbed:: q1

        .. tab:: Question

           .. actex:: tamagotchi_exercises
              :nocanvas:

              #. Cambie el código anterior para permitirle adoptar una mascota Tigre (que está a punto de crear). SUGERENCIA: mire la función ``whichtype`` y piense en lo que está sucediendo en el código para esa función.

              #. Ahora, modifique el código para definir una nueva clase, ``Tiger ''. La clase ``Tiger`` debe heredar de la clase ``Cat``, pero su recuento de maullidos predeterminado debe ser ``5``, no ``3``, y debe tener un método de instancia adicional, ``ROOOOOAR!``, que imprime la cadena ``ROOOOOAR!``.

              #. A continuación, modifique el código para que cuando se llame al método ``hi`` para la clase ``Tiger``, se llame al método ``ROOOOOAR!``. SUGERENCIA: Deberá llamar a un método de instancia dentro de otro, y deberá redefinir un método para la clase ``Tiger``. Consulte la sección **sobreescritura de métodos**.

              #. Ahora, modifique el código para definir otra nueva clase, ``Retriever``. Esta clase debe heredar de ``Lab``. Debería ser exactamente como ``Lab``, excepto que en lugar de imprimir solo ``I found the tennis ball!`` Cuando se llama al método ``fetch``, debería decir ``I found the tennis ball! I can fetch anything!``.

              #. Agregue sus propias mascotas nuevas y las modificaciones que desee: recuerde, para usarlas en el juego, también tendrá que alterar la función ``whichtype`` para que puedan usarse en el juego. De lo contrario, tendrá diferentes clases que pueden funcionar bien, pero no verá los efectos en el juego, ya que el código que realmente hace que el juego se encuentre en la segunda mitad del código proporcionado (busque el bucle ``while``).
              ~~~~

              from random import randrange

              class Pet():
                  boredom_decrement = 4
                  hunger_decrement = 6
                  boredom_threshold = 5
                  hunger_threshold = 10
                  sounds = ['Mrrp']

                  def __init__(self, name = "Kitty"):
                      self.name = name
                      self.hunger = randrange(self.hunger_threshold)
                      self.boredom = randrange(self.boredom_threshold)
                      self.sounds = self.sounds[:]  # copy the class attribute, so that when we make changes to it, we won't affect the other Pets in the class

                  def clock_tick(self):
                      self.boredom += 1
                      self.hunger += 1

                  def mood(self):
                      if self.hunger <= self.hunger_threshold and self.boredom <= self.boredom_threshold:
                          return "happy"
                      elif self.hunger > self.hunger_threshold:
                          return "hungry"
                      else:
                          return "bored"

                  def __str__(self):
                      state = "     I'm " + self.name + ". "
                      state += " I feel " + self.mood() + ". "
                      # state += "Hunger %d Boredom %d Words %s" % (self.hunger, self.boredom, self.sounds)
                      return state

                  def hi(self):
                      print(self.sounds[randrange(len(self.sounds))])
                      self.reduce_boredom()

                  def teach(self, word):
                      self.sounds.append(word)
                      self.reduce_boredom()

                  def feed(self):
                      self.reduce_hunger()

                  def reduce_hunger(self):
                      self.hunger = max(0, self.hunger - self.hunger_decrement)

                  def reduce_boredom(self):
                      self.boredom = max(0, self.boredom - self.boredom_decrement)

              class Dog(Pet):
                  # in the Dog class, Dog pets should express their hunger and boredom differently than generic Pets
                  def mood(self):
                      if self.hunger <= self.hunger_threshold and self.boredom <= self.boredom_threshold:
                          return "happy, arf! Happy"
                      elif self.hunger > self.hunger_threshold:
                          return "hungry already, arrrf"
                      else:
                          return "bored, so you should play with me"

              class Cat(Pet):
                  # in the Cat class, cats express their hunger and boredom a little differently, too. They also have an extra instance, variable meow_count.
                  def __init__(self, name="Fluffy", meow_count=3):
                      Pet.__init__(self, name)
                      self.meow_count = meow_count

                  def hi(self):
                      for i in range(self.meow_count):
                          print(self.sounds[randrange(len(self.sounds))])
                      self.reduce_boredom()

                  def mood(self):
                      if self.hunger <= self.hunger_threshold and self.boredom <= self.boredom_threshold:
                          return "happy, I suppose"
                      elif self.hunger > self.hunger_threshold:
                          return "mmmm...hungry"
                      else:
                          return "a bit bored"

              class Lab(Dog):
                  def fetch(self):
                      return "I found the tennis ball!"

                  def hi(self):
                      print(self.sounds[randrange(len(self.sounds))] + self.fetch())

              class Poodle(Dog):
                  def dance(self):
                      return "Dancin' in circles like poodles do."

                  def hi(self):
                      print(self.dance())
                      Dog.hi(self)

              class Bird(Pet):
                  sounds = ["chirp"]
                  def __init__(self, name="Kitty", chirp_number=2):
                      Pet.__init__(self, name) # call the parent class's constructor
                      # basically, call the SUPER -- the parent version -- of the constructor, with all the parameters that it needs.
                      self.chirp_number = chirp_number # now, also assign the new instance variable

                  def hi(self):
                      for i in range(self.chirp_number):
                          print(self.sounds[randrange(len(self.sounds))])
                      self.reduce_boredom()


              def whichone(petlist, name):
                  for pet in petlist:
                      if pet.name == name:
                          return pet
                  return None # no pet matched

              pet_types = {'dog': Dog, 'lab': Lab, 'poodle': Poodle, 'cat': Cat, 'bird': Bird}
              def whichtype(adopt_type="general pet"):
                  return pet_types.get(adopt_type.lower(), Pet)

              def play():
                  animals = []

                  option = ""
                  base_prompt = """
                      Quit
                      Adopt <petname_with_no_spaces> <adopt_type - choose dog, cat, lab, poodle, or another unknown pet type>
                      Greet <petname>
                      Teach <petname> <word>
                      Feed <petname>

                      Choice: """
                  feedback = ""
                  while True:
                      action = input(feedback + "\n" + base_prompt)
                      feedback = ""
                      words = action.split()
                      if len(words) > 0:
                          command = words[0]
                      else:
                          command = None
                      if command == "Quit":
                          print("Exiting...")
                          return
                      elif command == "Adopt" and len(words) > 1:
                          if whichone(animals, words[1]):
                              feedback += "You already have a pet with that name\n"
                          else:
                              # figure out which class it should be
                              if len(words) > 2:
                                  Cl = whichtype(words[2])
                              else:
                                  Cl = Pet
                              # Make an instance of that class and append it
                              animals.append(Cl(words[1]))
                      elif command == "Greet" and len(words) > 1:
                          pet = whichone(animals, words[1])
                          if not pet:
                              feedback += "I didn't recognize that pet name. Please try again.\n"
                              print()
                          else:
                              pet.hi()
                      elif command == "Teach" and len(words) > 2:
                          pet = whichone(animals, words[1])
                          if not pet:
                              feedback += "I didn't recognize that pet name. Please try again."
                          else:
                              pet.teach(words[2])
                      elif command == "Feed" and len(words) > 1:
                          pet = whichone(animals, words[1])
                          if not pet:
                              feedback += "I didn't recognize that pet name. Please try again."
                          else:
                              pet.feed()
                      else:
                          feedback+= "I didn't understand that. Please try again."

                      for pet in animals:
                          pet.clock_tick()
                          feedback += "\n" + pet.__str__()

              import sys
              sys.setExecutionLimit(60000)
              play()
