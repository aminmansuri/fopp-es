..  Copyright (C)  Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".



Invocando el Método de la Clase Principal
===========================================

A veces, la clase principal tiene un método útil, pero solo necesita ejecutar un pequeño código adicional al ejecutar el método de la subclase. Puede anular el método de la clase primaria en el método de la subclase con el mismo nombre, pero también invocar el método de la clase primaria. Así es como se hace:

Digamos que quería que la subclase ``Dog`` de ``Pet`` dijera "Arf! Thanks!" cuando se llama al método ``feed``, así como a la ejecución del código en el método original.

Aquí está la clase de mascotas original nuevamente.

.. activecode:: inheritance_pet_class_copy
    :nocanvas:

    from random import randrange

    # Here's the original Pet class
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

Y aquí hay una subclase que anula feed() al invocar el método feed() de la clase padre; entonces también ejecuta una línea extra de código. Tenga en cuenta la forma poco elegante de invocar el método de la clase padre. Nos referimos explícitamente a Pet.feed para obtener el método/objeto de función. Lo invocamos entre paréntesis. Sin embargo, dado que no estamos invocando el método de la manera normal, con <obj>.methodname, tenemos que pasar explícitamente una instancia como primer parámetro. En este caso, la variable self en Dog.feed() estará vinculada a una instancia de Dog, por lo que podemos pasar self: ``Pet.feed(self)``.

.. activecode:: feed_me_example
    :nocanvas:
    :include: inheritance_pet_class

    from random import randrange

    class Dog(Pet):
        sounds = ['Woof', 'Ruff']

        def feed(self):
            Pet.feed(self)
            print("Arf! Thanks!")

    d1 = Dog("Astro")

    d1.feed()

.. note::

    Hay una mejor manera de invocar el método de una superclase. Desafortunadamente, la implementación de python en nuestras ventanas ActiveCode no lo admite, por lo que no lo estamos usando aquí. En ese método alternativo, llamaríamos ``super().Feed()``. Esto es bueno porque es más fácil de leer y también porque pone la especificación de la clase de la que Dog hereda en un solo lugar, ``class Dog(Pet)``. En otro lugar, solo se refiere a ``super()`` y python se encarga de buscar que la clase padre (super) de Dog sea Pet.

Esta técnica se usa muy a menudo con el método ``__init__`` para una subclase. Suponga que se definen algunas variables de instancia adicionales para la subclase. Cuando invoca el constructor, pasa todos los parámetros regulares para la clase padre, más los adicionales para la subclase. El método de la subclase `` __init__`` almacena los parámetros adicionales en las variables de instancia y llama al método de la clase principal ``__init__`` para almacenar los parámetros comunes en las variables de instancia y hacer cualquier otra inicialización que normalmente hace.

Digamos que queremos crear una subclase de ``Pet``, llamada ``Bird``, y queremos que tome un parámetro adicional, ``chirp_number``, con un valor predeterminado de 2, y tenga una instancia adicional variable, ``self.chirp_number``. Luego, usaremos esto en el método ``hi`` para hacer más de un sonido.

.. activecode:: super_methods_1
    :nocanvas:
    :include: inheritance_pet_class

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

    b1 = Bird('tweety', 5)
    b1.teach("Polly wanna cracker")
    b1.hi()

**Revisa tu Entendimiento**

.. mchoice:: question_inheritance_4
   :answer_a: 5
   :answer_b: ["Mrrp"]
   :answer_c: ["chirp"]
   :answer_d: Error
   :feedback_a: Esto se imprimiría si el código fuera print(b1.chirp_number).
   :feedback_b: Configuramos b1 para que sea Bird('tweety', 5) arriba. Bird es una subclase de Pet, que tiene ["Mrrp"] para sonidos, pero Bird tiene un valor diferente para esa variable de clase. El intérprete busca primero en la subclase.
   :feedback_c: El intérprete encuentra el valor en la variable de clase para la clase Bird.
   :feedback_d: Ejecutamos el conjunto b1 para ser Bird('tweety', 5) arriba. Bird tiene un valor establecido para los sonidos del atributo.
   :correct: c

   ¿Qué se imprimirá cuando se ejecute ``print(b1.sounds)``?

.. mchoice:: question_inheritance_5
   :answer_a: Error al ser invocado
   :answer_b: La cadena no se imprimirá pero d1 reducirá su hambre.
   :answer_c: La cadena se imprimirá pero d1 no tendrá su hambre reducida.
   :answer_d: Nada sería diferente. Es lo mismo que el código actual.
   :feedback_a: Dado que ya no estamos llamando al método padre en la definición del método de subclase, las acciones definidas en el feed del método padre no sucederán, y solo Arf! Thanks! será impreso
   :feedback_b: Recuerde que el intérprete de Python verifica la existencia de feed en la clase Dog y busca feed en Pet solo si no se encuentra en Dog.
   :feedback_c: Dado que ya no estamos llamando al método de la clase Pet principal en la definición del método de la subclase Dog, la definición de clase anulará el método padre.
   :feedback_d: Recuerde que el intérprete de Python verifica la existencia de feed en la clase Dog y busca feed en Pet solo si no se encuentra en Dog.
   :correct: c
   
   Para la clase Dog definida en la ventana de activecode anterior, ¿qué sucedería cuando se ejecute d1.feed() si se elimina la línea Pet.feed(self)?

