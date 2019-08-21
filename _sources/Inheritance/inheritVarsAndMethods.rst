..  Copyright (C)  Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".


Heredando Variables y Métodos
================================

.. index:: Mecánicas para definir una subclase

Mecánicas para Definir una Subclase
------------------------------------

Dijimos que la herencia nos proporciona una forma más elegante de, por ejemplo, crear tipos de ``Dog`` y ``Cat``, en lugar de crear una clase muy compleja de ``Pet``. En resumen, esto es bastante intuitivo: todas las mascotas tienen ciertas cosas, pero los perros son diferentes de los gatos, que son diferentes de las aves. Yendo un paso más allá, un perro Collie es diferente de un perro Labrador, por ejemplo. La herencia nos brinda una manera fácil y elegante de representar estas diferencias.

Básicamente, funciona definiendo una nueva clase y utilizando una sintaxis especial para mostrar lo que la nueva subclase *hereda de* una superclase. Entonces, si desea definir una clase ``Dog`` como un tipo especial de ``Mascota``, diría que el tipo ``Dog hereda del tipo ``Pet``. En la definición de la clase heredada, solo necesita especificar los métodos y las variables de instancia que son diferentes de la clase principal (la **clase principal**, o la **superclase**, es lo que podemos llamar la clase que es *heredado de*. En el ejemplo que estamos discutiendo, ``Pet`` sería la superclase de ``Dog`` o ``Cat``).

Aquí hay un ejemplo. Digamos que queremos definir una clase ``Cat`` que herede de ``Pet``. Supongamos que tenemos la clase ``Pet`` que definimos anteriormente.

Queremos que el tipo ``Cat`` sea exactamente el mismo que ``Pet``, *excepto que* queremos que los gatos de sonido comiencen a conocer "Meow" en lugar de "mrrp", y queremos que la clase ``Cat`` tenga su propio método especial llamado ``chasing_rats``, que solo lo tedrá ``Cat``.

Como referencia, aquí está el código original de Tamagotchi


.. activecode:: inheritance_cat_example
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

    # Here's the new definition of class Cat, a subclass of Pet.
    class Cat(Pet): # the class name that the new class inherits from goes in the parentheses, like so.
        sounds = ['Meow']

        def chasing_rats(self):
            return "What are you doing, Pinky? Taking over the world?!"


¡Todo lo que necesitamos son las pocas líneas adicionales en la parte inferior de la ventana de ActiveCode! La elegancia de la herencia nos permite especificar solo las diferencias en la nueva clase heredada. En ese código adicional, nos aseguramos de que la clase ``Cat`` herede de la clase Pet. Hacemos eso poniendo la palabra Pet entre paréntesis, ``classCat (Pet):``. En la definición de la clase ``Cat``, solo necesitamos definir las cosas que son diferentes de las de la clase ``Pet``.

En este caso, la única diferencia es que la variable de clase ``sounds`` comienza con la cadena ``"Meow"`` en lugar de la cadena ``"mrrp"``, y hay un nuevo método ``chasing_rats``.

Todavía podemos usar todos los métodos ``Pet`` en la clase ``Cat``, de esta manera. Puede llamar al método ``__str__`` en una instancia de ``Cat`` para ``imprimir`` una instancia de ``Cat``, de la misma manera que podría llamarlo en una instancia de ``Pet`` , y lo mismo es cierto para el método ``hi``: es lo mismo para las instancias de ``Cat y ``Pet. Pero el método ``chasing_rats`` es especial: solo se puede usar en instancias ``Cat``, porque ``Cat`` es una subclase de ``Pet`` que tiene ese método adicional.

En el juego original de Tamagotchi en el último capítulo, viste código que creó instancias de la clase ``Pet``. Ahora escribamos un poco de código que usa instancias de la clase ``Pet`` e instancias de la clase ``Cat``.

.. activecode:: tamagotchi_2
    :nocanvas:
    :include: inheritance_cat_example

    p1 = Pet("Fido")
    print(p1) # we've seen this stuff before!

    p1.feed()
    p1.hi()
    print(p1)

    cat1 = Cat("Fluffy")
    print(cat1) # this uses the same __str__ method as the Pets do

    cat1.feed() # Totally fine, because the cat class inherits from the Pet class!
    cat1.hi()
    print(cat1)

    print(cat1.chasing_rats()) 

    #print(p1.chasing_rats()) # This line will give us an error. The Pet class doesn't have this method!

Y puedes continuar con el árbol de herencia. Heredamos ``Cat`` de ``Pet``. Ahora digamos que queremos una subclase de ``Cat`` llamada ``Cheshire``. Un gato de Cheshire debería heredar todo de ``Cat``, lo que significa que también hereda todo lo que ``Cat`` hereda de ``Pet`` pero la clase ``Cheshire`` tiene su propio método especial, ``smile``.

.. activecode:: inheritance_cheshire_example
    :nocanvas:
    :include: inheritance_cat_example

    class Cheshire(Cat): # this inherits from Cat, which inherits from Pet

        def smile(self): # this method is specific to instances of Cheshire
            print(":D :D :D")

    # Let's try it with instances.
    cat1 = Cat("Fluffy")
    cat1.feed() # Totally fine, because the cat class inherits from the Pet class!
    cat1.hi() # Uses the special Cat hello.
    print(cat1)

    print(cat1.chasing_rats())

    new_cat = Cheshire("Pumpkin") # create a Cheshire cat instance with name "Pumpkin"
    new_cat.hi() # same as Cat!
    new_cat.chasing_rats() # OK, because Cheshire inherits from Cat
    new_cat.smile() # Only for Cheshire instances (and any classes that you make inherit from Cheshire)

    # cat1.smile() # This line would give you an error, because the Cat class does not have this method!

    # None of the subclass methods can be used on the parent class, though.
    p1 = Pet("Teddy")
    p1.hi() # just the regular Pet hello
    #p1.chasing_rats() # This will give you an error -- this method doesn't exist on instances of the Pet class.
    #p1.smile() # This will give you an error, too. This method does not exist on instances of the Pet class.


Cómo el Intérprete Busca Atributos
---------------------------------------

Entonces, ¿qué sucede en el intérprete de Python cuando escribes programas con clases, subclases e instancias de clases y subclases primarias?

** Así es como el intérprete busca los atributos:**

1. Primero, busca una variable de instancia o un método de instancia por el nombre que está buscando.
2. Si no se encuentra una variable de instancia o método con ese nombre, busca una variable de clase. (Consulte el :ref:`capítulo anterior <class_and_instance_vars>` para obtener una explicación de la diferencia entre **variables de instancia** y **variables de clase**.)
3. Si no se encuentra ninguna variable de clase, busca una variable de clase en la clase primaria.
4. Si no se encuentra ninguna variable de clase _aquí_, el intérprete busca una variable de clase en el padre de ESA clase, si existe, la clase "abuelo".
5. Este proceso continúa hasta que se alcanza el último antepasado, momento en el que Python señalará un error.

Miremos esto con respecto a algún código.

Digamos que escribes las líneas:

.. code:: python

    new_cat = Cheshire("Pumpkin")
    print(new_cat.name)

En la segunda línea, después de crear la instancia, Python busca la variable de instancia ``name`` en la instancia ``new_cat``. En este caso, existe. El nombre en esta instancia de ``Cheshire`` es ``Pumpkin``. Ahí tienes!

Cuando se escriben y ejecutan las siguientes líneas de código:

.. code:: python

    cat1 = Cat("Sepia")
    cat1.hi()

El intérprete de Python busca ``hi`` en la instancia de ``Cat``. No lo encuentra, porque no hay una declaración de la forma ``cat1.hi = ...``. (Tenga cuidado aquí: si *hubiera* establecido una variable de instancia en Cat llamada ``hi``, hubiese sido una mala idea, porque ya no podría usar el **método** que heredó. Más adelante veremos más sobre esto).

Luego busca hola como una variable de clase (o método) en la clase Cat, y aún no la encuentra.

A continuación, busca una variable de clase ``hi`` en la clase padre de ``Cat``, ``Pet``. Encuentra que hay un **método** llamado ``hi`` en la clase ``Pet``. Debido a ``()`` después de ``hi``, se invoca el método. Todo está bien.

Sin embargo, para lo siguiente, no irá tan bien

.. code:: python

    p1 = Pet("Teddy")
    p1.chasing_rats()

El intérprete de Python busca una variable de instancia o método llamado ``chasing_rats`` en la clase ``Pet``. No existe ``Pet`` no tiene clases principales, por lo que Python señala un error.

**Revisa tu Entendimiento**

.. mchoice:: question_inheritance_1
   :answer_a: 1
   :answer_b: 2
   :answer_c: 3
   :answer_d: 4
   :feedback_a: Ni Cheshire ni Cat definen un método de constructor __init__, por lo que la clase abuela, Pet, tendrá su método __init__ llamado. Verifique cuántas variables de instancia establece.
   :feedback_b: Ni Cheshire ni Cat definen un método de constructor __init__, por lo que la clase abuela, Pet, tendrá su método __init__ llamado. Verifique cuántas variables de instancia establece.
   :feedback_c: Ni Cheshire ni Cat definen un método de constructor __init__, por lo que la clase abuela, Pet, tendrá su método __init__ llamado. Verifique cuántas variables de instancia establece.
   :feedback_d: Ni Cheshire ni Cat definen un método de constructor __init__, por lo que la clase abuela, Pet, tendrá su método __init__ llamado. Ese método constructor establece las variables de instancia nombre, hambre, aburrimiento y sonidos.
   :correct: d
   
   Después de ejecutar el código, ` new_cat = Cheshire("Pumpkin")``, ¿cuántas variables de instancia existen para la instancia new_cat de Cheshire?

.. mchoice:: question_inheritance_2
   :answer_a: We are Siamese if you please. We are Siamese if you don’t please.
   :answer_b: Error
   :answer_c: Pumpkin
   :answer_d: Nothing. There’s no print statement.
   :feedback_a: another_cat es una instancia de Siamese, por lo que se invoca su método song().
   :feedback_b: another_cat es una instancia de Siamese, por lo que se invoca su método song().
   :feedback_c: Esto se imprimiría si la instrucción fuera print new_cat.name.
   :feedback_d: Hay una declaración de impresión en la definición del método.
   :correct: a

   Lo que se imprimiría después de ejecutar el siguiente código:

   .. code-block:: python

     new_cat = Cheshire("Pumpkin”)
     class Siamese(Cat):
       def song(self):
         print("We are Siamese if you please. We are Siamese if you don’t please.")
     another_cat = Siamese("Lady")
     another_cat.song()


.. mchoice:: question_inheritance_3
   :answer_a: We are Siamese if you please. We are Siamese if you don’t please.
   :answer_b: Error
   :answer_c: Pumpkin
   :answer_d: Nothing. There’s no print statement.
   :feedback_a: No puede invocar métodos definidos en la clase Siamese en una instancia de la clase Cheshire. Ambas son subclases de Cat, pero Cheshire no es una subclase de Siamese, por lo que no hereda sus métodos.
   :feedback_b: No puede invocar métodos definidos en la clase Siamese en una instancia de la clase Cheshire. Ambas son subclases de Cat, pero Cheshire no es una subclase de Siamese, por lo que no hereda sus métodos.
   :feedback_c: Esto se imprimiría si la instrucción fuera print new_cat.name.
   :feedback_d: Hay una sentencia de impreión en la definición del método para siamés.
   :correct: b

   Qué se imprimiría después de ejecutar el siguiente código:

   .. code-block:: python

     new_cat = Cheshire("Pumpkin”)
     class Siamese(Cat):
       def song(self):
         print("We are Siamese if you please. We are Siamese if you don’t please.")
     another_cat = Siamese("Lady")
     new_cat.song()


