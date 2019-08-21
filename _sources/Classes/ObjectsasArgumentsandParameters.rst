..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

Objetos como Argumentos y Parámetros
--------------------------------------

Puede pasar un objeto como argumento a una función, de la forma habitual.

Aquí hay una función simple llamada ``distance`` que involucra nuestros nuevos objetos ``Point``. El trabajo de esta función es descubrir la
distancia entre dos puntos.

.. activecode:: chp13_classes6

    import math
    
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

    def distance(point1, point2):
        xdiff = point2.getX()-point1.getX()
        ydiff = point2.getY()-point1.getY()

        dist = math.sqrt(xdiff**2 + ydiff**2)
        return dist
    
    p = Point(4,3)
    q = Point(0,0)
    print(distance(p,q))


``distance`` toma dos puntos y devuelve la distancia entre ellos. Tenga en cuenta que ``distance`` **no es** un método de la clase Point. Puede ver esto mirando el patrón de sangría. No está dentro de la definición de clase. De la otra manera en la que nosotros
podemos saber que ``distance`` no es un método de Point, es que ``self`` no está incluido como un parámetro formal. Además, no invocamos ``distance`` utilizando la notación de puntos.

*Podríamos haber hecho* que distance sea un método de la clase Point. Entonces, habríamos llamado al primer parámetro self, y lo habríamos invocado usando la notación de puntos, como en el siguiente código. La forma de implementarlo es una cuestión de estilo de codificación.
Ambos funcionan correctamente. La mayoría de los programadores eligen si las funciones son independientes o los métodos de una clase en función de si la función parece semánticamente ser una operación que se realiza en instancias de la clase. En este caso, debido a que la distancia es realmente una propiedad de un par de puntos y es simétrica (la distancia de a a b es la misma que la de b a a) tiene más sentido que sea una función independiente y no un método . Se han producido muchas discusiones acaloradas entre los programadores sobre tales decisiones de estilo.

.. activecode:: chp13_classes6a

    import math
    
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

        def distance(self, point2):
            xdiff = point2.getX()-self.getX()
            ydiff = point2.getY()-self.getY()

            dist = math.sqrt(xdiff**2 + ydiff**2)
            return dist
    
    p = Point(4,3)
    q = Point(0,0)
    print(p.distance(q))


