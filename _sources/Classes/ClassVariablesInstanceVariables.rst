..  Copyright (C)  Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. _class_and_instance_vars:

Variables de Clase y Variables de Instancia
--------------------------------------------

Ya ha visto que cada instancia de una clase tiene su propio espacio de nombres con sus propias variables de instancia. Dos instancias de la clase Point tienen cada una su propia variable de instancia x. Establecer x en una instancia no afecta a la otra instancia.

Una clase también puede tener variables de clase. Una variable de clase se establece como parte de la definición de clase.

Por ejemplo, considere la siguiente versión de la clase Point. Aquí hemos agregado un método gráfico que genera una cadena que representa un pequeño gráfico basado en texto con el Punto trazado en el gráfico. No es un gráfico muy bonito, en parte porque el eje y está estirado como una banda elástica, pero puedes obtener la idea de esto.

Tenga en cuenta que hay una asignación a la variable printed_rep en la línea 4. No está dentro de ningún método. Eso lo convierte en una variable de clase. Se accede de la misma manera que las variables de instancia. Por ejemplo, en la línea 16, hay una referencia a self.printed_rep. Si cambia la línea 4, debe imprimir un carácter diferente en las coordenadas x, y del Punto en el gráfico.

.. activecode:: classvars_1

    class Point:
        """ Point class for representing and manipulating x,y coordinates. """

        printed_rep = "*"

        def __init__(self, initX, initY):

            self.x = initX
            self.y = initY

        def graph(self):
            rows = []
            size = max(int(self.x), int(self.y)) + 2
            for j in range(size-1) :
                if (j+1) == int(self.y):
                    special_row = str((j+1) % 10) + (" "*(int(self.x) -1)) + self.printed_rep
                    rows.append(special_row)
                else:
                    rows.append(str((j+1) % 10))
            rows.reverse()  # put higher values of y first
            x_axis = ""
            for i in range(size):
                x_axis += str(i % 10)
            rows.append(x_axis)

            return "\n".join(rows)


    p1 = Point(2, 3)
    p2 = Point(3, 12)
    print(p1.graph())
    print()
    print(p2.graph())

Para poder razonar sobre las variables de clase y las variables de instancia, es útil conocer las reglas que usa el intérprete de Python. De esa manera, puede simular mentalmente lo que hace el intérprete.

Cuando el intérprete ve una expresión de la forma <obj>. <varname>, esta:
    1. Comprueba si el objeto tiene un conjunto de variables de instancia. Si es así, usa ese valor.
    2. Si no encuentra una variable de instancia, verifica si la clase tiene una variable de clase. Si es así, usa ese valor.
    3. Si no encuentra una instancia o una variable de clase, crea un error de tiempo de ejecución (en realidad, primero realiza otra verificación, de la que aprenderá en el próximo capítulo).

Cuando el intérprete ve una declaración de asignación de la forma <obj>. <varname> = <expr>, esta:
    1. Evalúa la expresión en el lado derecho para producir algún objeto python;
    2. Establece la variable de instancia <varname> de <obj> para que se vincule a ese objeto de Python. Tenga en cuenta que una declaración de asignación de este formulario nunca establece la variable de clase; solo establece la variable de instancia.

Para establecer la variable de clase, utiliza una instrucción de asignación de la forma <varname> = <expr> en el nivel superior en una definición de clase, como en la línea 4 en el código anterior para establecer la variable de clase printed_rep.

En caso de que tenga curiosidad, las definiciones de métodos también crean variables de clase. Por lo tanto, en el código anterior, el gráfico se convierte en una variable de clase que está vinculada a un objeto de función / método. p1.graph () es evaluado por:
    * buscando p1 y descubriendo que es una instancia de Point
    * buscando una variable de instancia llamada gráfica en p1, pero no encuentra una
    * buscando una variable de clase llamada gráfica en la clase de p1, la clase Point; encuentra un objeto de función / método
    * Debido a () después de la palabra gráfica, invoca el objeto de función / método, con el parámetro self unido al objeto al que apunta p1.

Intente ejecutarlo en codelens y vea si puede seguir cómo funciona todo.
