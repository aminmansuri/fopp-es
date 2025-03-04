..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

:skipreading:`True`

Ejercicios
-----------

.. question:: classes_ex_1

    .. tabbed:: q1

        .. tab:: Question


           .. actex:: ch_cl_01

              Agregue un método a Point llamado ``reflect_x`` que devuelve un nuevo Punto, uno que es el reflejo del punto sobre el eje x. Por ejemplo, ``Point(3, 5).reflect_x()`` es (3, -5)

              ~~~~

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
                    
                  def move(self, dx, dy):
                      self.x = self.x + dx
                      self.y = self.y + dy
                        
                  def __str__(self):
                      return str(self.x)+","+str(self.y)


.. question:: classes_ex_2

    .. tabbed:: q2

        .. tab:: Question

           .. actex:: ch_cl_02

              Agregue un método llamado ``move`` que tomará dos parámetros, llámelos ``dx`` y ``dy``. El método hará que el punto se mueva en la dirección x e y el número de unidades dado. (Sugerencia: cambiar los valores del estado del punto)

              ~~~~

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
                    
                  # Put your new method here
                        
                  def __str__(self):
                      return str(self.x)+","+str(self.y)
           

        .. tab:: Answer
            
            .. activecode:: ch_cl_02_answer
            
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
                    
                    def move(self, dx, dy):
                        self.x = self.x + dx
                        self.y = self.y + dy
                        
                    def __str__(self):
                        return str(self.x)+","+str(self.y)


                p = Point(7,6)
                print(p)
                p.move(5,10)
                print(p)
