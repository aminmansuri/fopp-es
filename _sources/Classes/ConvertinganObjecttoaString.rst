..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

Convirtiendo un Objeto en una Cadena
--------------------------------------


Cuando trabajamos con clases y objetos, a menudo es necesario imprimir un objeto (es decir, imprimir el estado de un objeto).
Considere el siguiente ejemplo.

.. activecode:: chp13_classesstr1
    
    class Point:
        """ Point class for representing and manipulating x,y coordinates. """
        
        def __init__(self, initX, initY):

            self.x = initX
            self.y = initY

        def getX(self):
            return self.x

        def getY(self):
            return self.y

        def distanceFromOrigin(self):
            return ((self.x ** 2) + (self.y ** 2)) ** 0.5

    
    p = Point(7,6)
    print(p)

La función ``print`` que se muestra arriba produce una representación de cadena del Punto ``p``. La funcionalidad predeterminada proporcionada por
Python te dice que ``p`` es un objeto de tipo ``Point``. Sin embargo, no le dice nada sobre el estado específico del punto.

Podemos mejorar esta representación si incluimos un método especial llamado ``__str__``. Tenga en cuenta que este método utiliza la misma convención de nomenclatura que el constructor, es decir, dos guiones bajos antes y después del nombre. Es común que Python
utiliza esta técnica de denominación para métodos especiales.

El método ``__str__`` es responsable de devolver una representación de cadena según lo definido por el creador de la clase. En otras palabras, usted, como programador, puede elegir cómo debe ser un ``Point`` cuando se imprime. En este caso, nosotros
hemos decidido que la representación de la cadena incluirá los valores de x e y, así como algo de texto de identificación. Eso requiere que el método ``__str__`` cree y *devuelva* una cadena.

Cualquier cadena que devuelva el método ``__str__`` para una clase, esa es la cadena que se imprimirá cuando coloque cualquier instancia de esa clase en una declaración de impresión. Por esa razón, la cadena que devuelve el método ``__str__`` de una clase generalmente debe incluir valores de variables de instancia. Si un punto tiene el valor 3 de ``x`` y valor 4 de ``y``, pero otro punto tiene el valor 5 de `` x`` y el valor 9 de `` y``, esos dos objetos Point probablemente deberían verse diferentes cuando imprimirlos, ¿verdad?

Echa un vistazo al código a continuación.

.. activecode:: chp13_classesstr2

    class Point:
        """ Point class for representing and manipulating x,y coordinates. """

        def __init__(self, initX, initY):

            self.x = initX
            self.y = initY

        def getX(self):
            return self.x

        def getY(self):
            return self.y

        def distanceFromOrigin(self):
            return ((self.x ** 2) + (self.y ** 2)) ** 0.5
          
        def __str__(self):
            return "x = {}, y = {}".format(self.x, self.y)

    p = Point(7,6)
    print(p)


Cuando ejecutamos el programa anterior, puede ver que la función ``print`` ahora muestra la cadena que elegimos.

Ahora, pregunta, ¿no tenemos ya un convertidor de tipo ``str`` que pueda
convertir nuestro objeto en un String? ¡Sí!

¿Y no ``imprime`` automáticamente al imprimir cosas? ¡Si de nuevo!

Sin embargo, como vimos anteriormente, estos mecanismos automáticos no hacen exactamente lo que queremos. Python proporciona muchas implementaciones predeterminadas para
métodos que nosotros como programadores probablemente querremos cambiar. Cuando un programador cambia el significado de un método,
digamos que **anulamos** el método. Tenga en cuenta también que la función de convertidor de tipo ``str`` utiliza cualquier método ``__str__`` que
proporciona.


**Revisa tu entendimiento**

1. Cree una clase llamada Cereal que acepte tres entradas: 2 cadenas y 1 entero, y las asigne a 3 variables de instancia en el constructor: ``name``, ``brand`` y ``fiber``. Cuando se imprime una instancia de ``Cereal``, el usuario debe ver lo siguiente: "¡[nombre] cereal es producido por [marca] y tiene [integer fibra] gramos de fibra en cada porción!" Al nombre de la variable ``c1``, asigne una instancia de ``Cereal`` cuyo nombre es ``"Corn Flakes"``, la marca es ``"Kellogg's"`` y la fibra es ``2``. Al nombre de la variable ``c2``, asigne una instancia de ``Cereal`` cuyo nombre es ``"Honey Nut Cheerios" ``, la marca es ``"General Mills"`` y la fibra es ``3``. ¡Practica imprimir ambos!

.. activecode:: ac_ch13_classstr_01
   :tags: Classes/ImprovingourConstructor.rst, Classes/AddingOtherMethodstoourClass.rst, Classes/ConvertinganObjecttoaString.rst


   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(c1.__str__(), "Corn Flakes cereal is produced by Kellogg's and has 2 grams of fiber in every serving!", "Testing that c1 prints correctly.")
      def testTwo(self): 
         self.assertEqual(c2.__str__(), "Honey Nut Cheerios cereal is produced by General Mills and has 3 grams of fiber in every serving!", "Testing that c2 prints correctly.")

   myTests().main()  

