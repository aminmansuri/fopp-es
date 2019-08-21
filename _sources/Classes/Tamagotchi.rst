..  Copyright (C)  Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. _tamagotchi_chap:

.. index:: Tamagotchi

Un Juego de Tamagotchi
------------------------

También hay muchas formas interesantes de usar clases definidas por el usuario que no involucran datos de Internet. Vamos a juntar todas estas mecánicas de una manera un poco más interesante de lo que obtuvimos con la clase Point. Recuerda `Tamagotchis <https://en.wikipedia.org/wiki/Tamagotchi>`_, las pequeñas mascotas electrónicas? A medida que pasaba el tiempo, tendrían hambre o aburrimiento. Tenías que limpiar después de ellos o se enfermarían. Y lo hiciste todo con unos pocos botones en el dispositivo.

Vamos a hacer una versión simplificada basada en texto de eso. En su conjunto de problemas y en el capítulo sobre `Herencia <cap_inheritance>` ampliaremos esto más.

Primero, comencemos con una clase ``Pet``. Cada instancia de la clase será una mascota electrónica para que el usuario se encargue. Cada instancia tendrá un estado actual, que consta de tres variables de instancia:
    * hambre, (*hunger*) un número entero
    * aburrimiento, (*boredom*)un número entero
    * sonidos, (*sounds*) una lista de cadenas, cada una una palabra que se le ha enseñado a la mascota a decir

En el método ``__init__``, el hambre y el aburrimiento se inicializan en valores aleatorios entre 0 y el umbral para tener hambre o aburrirse. La variable de instancia ``sounds`` se inicializa para ser una copia de la variable de clase con el mismo nombre. La razón por la que hacemos una copia de la lista es que realizaremos operaciones destructivas (agregando nuevos sonidos a la lista). Si no hiciéramos una copia, entonces esas operaciones destructivas afectarían la lista a la que apunta la variable de clase, y por lo tanto, ¡enseñar un sonido a cualquiera de las mascotas lo enseñaría a todas las instancias de la clase!

Hay un método ``clock_tick`` que simplemente incrementa las variables de instancia de aburrimiento y hambre, simulando la idea de que a medida que pasa el tiempo, la mascota se aburre y tiene más hambre.

El método ``__str__`` produce una representación en cadena del estado actual de la mascota, especialmente si está aburrido o hambriento o si está contento. Se aburre si la variable de instancia de aburrimiento es mayor que el umbral, que se establece como una variable de clase.

Para aliviar el aburrimiento, el dueño de la mascota puede enseñarle una nueva palabra a la mascota, usando el método ``teach()``, o interactuar con la mascota, usando el método ``hi()``. En respuesta a teach(), la mascota agrega la nueva palabra a su lista de palabras. En respuesta al método hi(), imprime una de las palabras que conoce, escogiendo al azar una de su lista de palabras conocidas. Tanto hi() como teach() provocan una invocación del método ``reduce_boredom()``. Disminuye el estado de aburrimiento en una cantidad que lee de la variable de clase hunger_decrement. El estado de aburrimiento nunca puede ir por debajo de 0.

Para aliviar el hambre, llamamos al método feed().

.. activecode:: tamagotchi_1
    :nocanvas:

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
            # state += "Hunger {} Boredom {} Words {}".format(self.hunger, self.boredom, self.sounds)
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

Intentemos hacer una mascota y jugar un poco con ella. Agregue también algunos de sus propios comandos y siga imprimiendo p1 para ver cuáles son los efectos. Si desea inspeccionar directamente el estado, intente imprimir p1.boredom o p1.hunger.

.. activecode:: tamagotchi_2_copy
    :nocanvas:
    :include: tamagotchi_1

    p1 = Pet("Fido")
    print(p1)
    for i in range(10):
        p1.clock_tick()
        print(p1)
    p1.feed()
    p1.hi()
    p1.teach("Boo")
    for i in range(10):
        p1.hi()
    print(p1)



Eso es genial si quieres interactuar con la mascota escribiendo código python. Hagamos un juego que los no programadores puedan jugar.

Utilizaremos el patrón `Listener Loop <chap_listener>`. En cada iteración, mostraremos un mensaje de texto que le recordará al usuario qué comandos están disponibles.

El usuario tendrá una lista de mascotas, cada una con un nombre. El usuario puede emitir un comando para adoptar una nueva mascota, lo que creará una nueva instancia de mascota. O el usuario puede interactuar con una mascota existente, con un comando Saludar, Enseñar o Alimentar.

No importa lo que haga el usuario, con cada comando ingresado, el reloj marca para todas sus mascotas. Cuidado, si tienes demasiadas mascotas, ¡no podrás mantenerlas todas satisfechas!

.. activecode:: tamogotchi_3:
    :nocanvas:
    :include: tamagotchi_1

    import sys
    sys.setExecutionLimit(60000)

    def whichone(petlist, name):
        for pet in petlist:
            if pet.name == name:
                return pet
        return None # no pet matched

    def play():
        animals = []

        option = ""
        base_prompt = """
            Quit
            Adopt <petname_with_no_spaces_please>
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
                    animals.append(Pet(words[1]))
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



    play()