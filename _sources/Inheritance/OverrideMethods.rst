..  Copyright (C)  Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".


Sobreescritura de Métodos
==========================

Si se define un método para una clase, y también se define para su clase padre, se llama al método de la subclase y no al padre.
Esto se desprende de las reglas para buscar atributos que viste en la sección anterior.

Podemos usar la misma idea para entender la sobreescritura de métodos.

Volvamos a nuestra idea de hacer que Gatos, Perros y otras mascotas generen una cadena para cada "mood" diferente.

Aquí está la clase original Pet nuevamente.

.. activecode:: inheritance_pet_class
    :nocanvas:

    from random import randrange

    # Aquí está la clase original Pet
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

Ahora hagamos dos subclases, Dog y Cat. Los perros siempre son felices a menos que estén aburridos *y* hambrientos. Los gatos, por otro lado, son felices solo si son alimentados y si su nivel de aburrimiento está en un rango estrecho e, incluso entonces, solo con probabilidad 1/2.

.. activecode:: inheritance_override
    :nocanvas:
    :include: inheritance_pet_class

    class Cat(Pet):
        sounds = ['Meow']

        def mood(self):
            if self.hunger > self.hunger_threshold:
                return "hungry"
            if self.boredom <2:
                return "grumpy; leave me alone"
            elif self.boredom > self.boredom_threshold:
                return "bored"
            elif randrange(2) == 0:
                return "randomly annoyed"
            else:
                return "happy"

    class Dog(Pet):
        sounds = ['Woof', 'Ruff']

        def mood(self):
            if (self.hunger > self.hunger_threshold) and (self.boredom > self.boredom_threshold):
                return "bored and hungry"
            else:
                return "happy"

    c1 = Cat("Fluffy")
    d1 = Dog("Astro")

    c1.boredom = 1
    print(c1.mood())
    c1.boredom = 3
    for i in range(10):
        print(c1.mood())
    print(d1.mood())
