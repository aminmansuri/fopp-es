..  Copyright (C)  Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. _inheritance_chap:

Introducción: Herencia de Clase
================================

Las clases pueden "heredar" métodos y variables de clase de otras clases. Veremos la mecánica de cómo funciona esto en secciones posteriores. Primero, sin embargo, motivemos por qué esto podría ser valioso. Resulta que la herencia no te permite hacer nada que no podrías hacer sin ella, pero hace que algunas cosas sean mucho más elegantes. También encontrará que es útil cuando alguien más ha definido una clase en un módulo o biblioteca, y solo desea anular algunas cosas sin tener que volver a implementar todo lo que ha hecho.

Considera nuestro juego Tamagotchi. Supongamos que queremos hacer algunos tipos diferentes de mascotas que tengan la misma estructura que otras mascotas, pero que tengan algunos atributos diferentes o se comporten de manera un poco diferente. Por ejemplo, suponga que las mascotas de los perros deben mostrar su estado emocional de manera un poco diferente a los gatos o actuar de manera diferente cuando tienen hambre o cuando se les pide que vayan a buscar algo.

Puede implementar esto haciendo una variable de instancia para el tipo de mascota y despachando en esa variable de instancia en varios métodos.

.. code:: python

    from random import randrange

    class Pet():
        boredom_decrement = 4
        hunger_decrement = 6
        boredom_threshold = 5
        hunger_threshold = 10
        sounds = ['Mrrp']
        def __init__(self, name = "Kitty", pet_type="dog"):
            self.name = name
            self.hunger = randrange(self.hunger_threshold)
            self.boredom = randrange(self.boredom_threshold)
            self.sounds = self.sounds[:]  # copy the class attribute, so that when we make changes to it, we won't affect the other Pets in the class
            self.pet_type = pet_type

        def clock_tick(self):
            self.boredom += 1
            self.hunger += 1

        def mood(self):
            if self.hunger <= self.hunger_threshold and self.boredom <= self.boredom_threshold:
                if self.pet_type == "dog": # if the pet is a dog, it will express its mood in different ways from a cat or any other type of animal
                    return "happy"
                elif self.pet_type == "cat":
                    return "happy, probably"
                else:
                    return "HAPPY"
            elif self.hunger > self.hunger_threshold:
                if self.pet_type == "dog": # same for hunger -- dogs and cats will express their hunger a little bit differently in this version of the class definition
                    return "hungry, arf"
                elif self.pet_type == "cat":
                    return "hungry, meeeeow"
                else:
                    return "hungry"
            else:
                return "bored"

        def __str__(self):
            state = "     I'm " + self.name + ". "
            state += " I feel " + self.mood() + ". "
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


Ese código es exactamente el mismo que define la clase ``Pet`` que viste en la sección:ref:`Tamagotchi <tamagotchi_chap>`, excepto que hemos agregado algunas cosas.
    * Una nueva entrada al constructor: el parámetro de entrada ``pet_type``, que por defecto es ``"dog"``, y la variable de instancia ``self.pet_type``.
    * if..elif..else en el método ``self.mood()``, de modo que los diferentes tipos de mascotas (un perro, un gato o cualquier otro tipo de animal) expresen sus estados de ánimo y su hambre de manera ligeramente diferente formas.

Pero esa no es una forma elegante de hacerlo. Oculta las partes de ser una mascota que son comunes a todas las mascotas y entierra las cosas únicas de ser un perro o un gato en medio del método del estado de ánimo. ¿Qué pasaría si también quisieras que un perro redujera el aburrimiento a un ritmo diferente al de un gato y quisieras que una mascota pájaro fuera diferente? Aquí, solo hemos implementado **perros**, **gatos** y **otros**, pero puedes imaginar las posibilidades.

Si hubiera muchos tipos diferentes de mascotas, esos métodos comenzarían a tener cláusulas de código **if..elif..elif** largas y complejas, lo que puede ser confuso. Y necesitaría eso en cada método donde el comportamiento era diferente para los diferentes tipos de mascotas. La herencia de clase nos dará una forma más elegante de hacerlo.