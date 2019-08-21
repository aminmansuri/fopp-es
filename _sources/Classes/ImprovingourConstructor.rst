..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".


Agregando Parámetros al Constructor
------------------------------------

Nuestro constructor hasta ahora solo puede crear puntos en la ubicación ``(0,0)``. Para crear un punto en la posición (7, 6) requiere que
proporcionemos alguna capacidad adicional para que el usuario pase información al constructor. Dado que los constructores son simplemente funciones especialmente nombradas, podemos usar parámetros (como hemos visto antes) para proporcionar la información específica.
    
Podemos hacer que nuestro constructor de clases sea más generalmente utilizable poniendo parámetros adicionales en
El método ``__init__``, como se muestra en este ejemplo.

.. sourcecode:: python
    
    class Point:
        """ Point class for representing and manipulating x,y coordinates. """
        
        def __init__(self, initX, initY):
 
            self.x = initX
            self.y = initY
    
    p = Point(7,6)

Ahora, cuando creamos nuevos puntos, suministramos las coordenadas xey como parámetros. Cuando se crea el punto, los valores de ``initX`` e ``initY`` se asignan al estado del objeto, en las **variables de instancia** x e y.

Esto es algo común en el método ``__init__`` para una clase: tome algunos parámetros y guárdelos como variables de instancia. ¿Por qué es útil esto? Tenga en cuenta que las variables de parámetro desaparecerán cuando el método termine de ejecutarse. Sin embargo, las variables de instancia seguirán siendo accesibles desde cualquier lugar que tenga un controlador en la instancia del objeto. Esta es una forma de guardar los valores iniciales que se proporcionan cuando se invoca el constructor de la clase.

Más adelante, verá clases donde el método ``__init__`` hace más que guardar parámetros como variables de instancia. Por ejemplo, podría analizar el contenido de esas variables y hacer algunos cálculos sobre ellas, almacenando los resultados en variables de instancia. Incluso podría hacer una conexión a Internet, descargar algo de contenido y almacenarlo en variables de instancia.

.. image:: Figures/objectpic5.png
   :alt: Simple object has state and methods


**Revisa tu entendimiento**

1. Cree una clase llamada ``NumberSet`` que acepte 2 enteros como entrada y defina dos variables de instancia: ``num1`` y ``num2``, que contienen cada uno de los enteros de entrada. Luego, cree una instancia de ``NumberSet`` donde su num1 sea 6 y su num2 sea 10. Guarde esta instancia en una variable ``t``.

.. activecode:: ee_ch13_011
   :tags:Classes/ImprovingourConstructor.rst

      
   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOneA(self):
         self.assertEqual(t.num1, 6, "Testing that t.num1 has correct number assigned.")
      def testOneB(self):
         self.assertEqual(t.num2, 10, "Testing that t.num2 has correct number assigned.")

   myTests().main()
       
