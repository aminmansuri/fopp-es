..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

Instancias como Valores de Retorno
------------------------------------

Las funciones y los métodos pueden devolver objetos. En realidad, esto no es nada nuevo, ya que todo en Python es un objeto y tenemos
estado devolviendo valores durante bastante tiempo. (También puede tener listas o tuplas de instancias de objetos, etc.) La diferencia aquí es que queremos que el método cree un objeto usando
el constructor y luego lo devuelve como el valor del método.


Supongamos que tiene un objeto Point
y desea encontrar el punto medio a medio camino entre este y algún otro punto objetivo. Nos gustaría escribir un método, llamémoslo
``halfway``, que toma otro ``Point`` como parámetro y devuelve el ``Punto`` que está a medio camino entre el punto inicial y
el punto objetivo que acepta como entrada.

.. activecode:: chp13_classesmid1

    class Point:

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

        def halfway(self, target): 
            mx = (self.x + target.x)/2
            my = (self.y + target.y)/2
            return Point(mx, my)

    p = Point(3,4)
    q = Point(5,12)
    mid = p.halfway(q)
    # note that you would have exactly the same result if you instead wrote
    # mid = q.halfway(p)
    # because they are both Point objects, and the middle is the same no matter what

    print(mid)
    print(mid.getX())
    print(mid.getY())
       

El punto resultante, ``mid``, tiene un valor x de 4 y un valor y de 8. También podemos usar cualquier otro método en ``mid`` ya que es un
objeto ``Point``.

    

