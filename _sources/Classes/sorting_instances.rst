..  Copyright (C)  Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

..  shortname:: Sorting Instances
..  description:: Invoking sort and sorted on lists of instances.

.. qnum::
   :prefix: sort-instances-
   :start: 1
   
.. _sort_instances_chap:

Ordenando Listas de Instancias
===============================

Aprendiste previamente:ref:`cómo ordenar listas <sort_chap>`. Ordenar listas de instancias de una clase no es fundamentalmente diferente de ordenar listas de objetos de cualquier otro tipo. Hay una manera de definir un orden de clasificación predeterminado para las instancias, directamente en la definición de la clase, pero requiere definir un montón de métodos o un método complicado, por lo que no nos molestaremos con eso. En su lugar, solo debe proporcionar una función clave como parámetro para ordenar (u ordenar).

Anteriormente, ha visto cómo proporcionar dicha función al ordenar listas de otros tipos de objetos. Por ejemplo, dada una lista de cadenas, puede ordenarlas en orden ascendente de sus longitudes pasando un parámetro clave. Tenga en cuenta que si se refiere a una función por su nombre, le da el nombre de la función sin paréntesis después de ella, porque desea que el objeto de la función en sí. La función ordenada se encargará de llamar a la función, pasando el elemento actual en la lista. Por lo tanto, en el siguiente ejemplo, escribimos ``key=len`` y no ``key=len()``.

.. activecode:: sort_instances_1

   L = ["Cherry", "Apple", "Blueberry"]
   
   print(sorted(L, key=len))
   #alternative form using lambda, if you find that easier to understand
   print(sorted(L, key= lambda x: len(x)))   

Cuando cada uno de los elementos de una lista es una instancia de una clase, debe proporcionar una función que tome una instancia como entrada y devuelva un número. Las instancias se ordenarán por sus números.

.. activecode:: sort_instances_2

   class Fruit():
       def __init__(self, name, price):
           self.name = name
           self.price = price
                      
   L = [Fruit("Cherry", 10), Fruit("Apple", 5), Fruit("Blueberry", 20)]
   for f in sorted(L, key=lambda x: x.price):
       print(f.name)

A veces, le resultará conveniente definir un método para la clase que haga algunos cálculos sobre los datos en una instancia. En este caso, nuestra clase es demasiado simple para ilustrarlo realmente. Pero para simularlo, he definido un método ``sort_priority`` que solo devuelve el precio almacenado en la instancia. Ahora, ese método, sort_priority toma una instancia como entrada y devuelve un número. Por lo tanto, es exactamente el tipo de función que debemos proporcionar como parámetro clave para ordenar. Aquí puede ser un poco confuso: para referirse a ese método, sin invocarlo realmente, puede referirse a ``Fruit.sort_priority``. Esto es análogo al código anterior que se refería a ``len`` en lugar de invocar a ``len()``.

.. activecode:: sort_instances_3

   class Fruit():
       def __init__(self, name, price):
           self.name = name
           self.price = price
           
       def sort_priority(self):
           return self.price
           
   L = [Fruit("Cherry", 10), Fruit("Apple", 5), Fruit("Blueberry", 20)]
   print("-----sorted by price, referencing a class method-----")
   for f in sorted(L, key=Fruit.sort_priority):
       print(f.name)
       
   print("---- one more way to do the same thing-----")
   for f in sorted(L, key=lambda x: x.sort_priority()):
       print(f.name)

