..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

Agregar otros métodos a una clase
----------------------------------
          
La ventaja clave de usar una clase como ``Point`` en lugar de algo así como un simple
tupla ``(7, 6)`` ahora se hace evidente. Podemos agregar métodos a
la clase ``Point`` que son operaciones sensibles para puntos. Si hubiéramos elegido usar una
tupla para representar el punto, no tendríamos esta capacidad.
Crear una clase como ``Point`` trae una excepcional
cantidad de "poder organizacional" para nuestros programas y para nuestro pensamiento.
Podemos agrupar las operaciones sensibles y los tipos de datos
se aplican a, y cada instancia de la clase puede tener su propio estado.
          
Un **método** se comporta como una función pero se invoca en un determinado
ejemplo. Por ejemplo, con una lista vinculada a la variable L, ``L.append(7)`` llama a la función append, con la lista como el primer parámetro y 7 como el segundo parámetro. Se accede a los métodos utilizando la notación de puntos. Esta es la razón por la cual ``L.append(7)`` tiene 2 parámetros aunque pueda pensar que solo tiene uno: la lista almacenada en la variable ``L`` es el primer valor del parámetro y 7 es el segundo.

Agreguemos dos métodos simples para permitir que un punto nos brinde información sobre su estado. El método ``getX``, cuando se invoca, devolverá el valor de la coordenada x.

La implementación de este método es sencilla ya que ya sabemos cómo
escribir funciones que devuelven valores. Una cosa a tener en cuenta es que a pesar de que el método ``getX`` no necesita ninguna otra información de parámetros para hacer su trabajo, todavía hay un parámetro formal, ``self``. Como dijimos anteriormente, todos los métodos definidos en una clase que operan en objetos de esa clase tendrán ``self`` como su primer parámetro. Nuevamente, esto sirve como una referencia al objeto mismo que a su vez da acceso a los datos de estado dentro del objeto.

.. activecode:: chp13_classes4
    
    class Point:
        """ Clase de Point para representar y manipular coordenadas x,y. """
        
        def __init__(self, initX, initY):
 
            self.x = initX
            self.y = initY

        def getX(self):
            return self.x

        def getY(self):
            return self.y

    
    p = Point(7,6)
    print(p.getX())
    print(p.getY())

Tenga en cuenta que el método ``getX`` simplemente devuelve el valor de la variable de instancia x del objeto self. En otras palabras, la implementación del método es ir al estado del objeto en sí y obtener el valor de ``x``. Del mismo modo, el método ``getY`` se ve casi igual.

Agreguemos otro método, ``distanceFromOrigin``, para ver mejor los métodos de
trabajo. Este método nuevamente no necesitará ninguna información adicional para hacer su trabajo, más allá de los datos almacenados en las variables de instancia.
Realizará una tarea más compleja.

.. activecode:: chp13_classes5
    
    class Point:
        """ Clase de Point para representar y manipular coordenadas x,y. """
        
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
    print(p.distanceFromOrigin())


Tenga en cuenta que la llamada de ``distanceFromOrigin`` no *explícitamente*
proporciona un argumento para que coincida con el parámetro ``self``. Esto es cierto para todas las llamadas a métodos. La definición siempre parecerá
tener un parámetro adicional en comparación con la invocación.

**Revisa tu entendimiento**

1. Cree una clase llamada ``Animal`` que acepte dos números como entradas y los asigne respectivamente a dos variables de instancia: ``arms`` y ``legs``. Cree un método de instancia llamado ``limbs`` que, cuando se llama, devuelve el número total de extremidades que tiene el animal. Al nombre variable ``spider``, asigne una instancia de ``Animal`` que tenga 4 brazos y 4 patas. Llame al método de las extremidades en la instancia de ``spider`` y guarde el resultado en el nombre de la variable ``spidlimbs``.

.. activecode:: ac_chp13_classes_01
   :tags: Classes/ImprovingourConstructor.rst, Classes/AddingOtherMethodstoourClass.rs


   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(spider.arms, 4, "Testing that spider was assigned the correct number of arms.")
         self.assertEqual(spider.legs, 4, "Testing that spider was assigned the correct number of legs.")
         self.assertEqual(spidlimbs, 8, "Testing that spidlimbs was assigned correctly.")

   myTests().main()      
