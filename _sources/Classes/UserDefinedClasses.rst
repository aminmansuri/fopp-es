..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. index:: compound data type

.. _chap_constructor:

Clases Definidas Por el Usuario
---------------------------------

Ya hemos visto clases como ``str``, ``int``, ``float`` y ``list``. Estos fueron definidos por Python y
disponible para que lo usemos. Sin embargo, en muchos casos cuando estamos resolviendo problemas necesitamos crear objetos de datos
que están relacionados con el problema que estamos tratando de resolver. Necesitamos crear nuestras propias clases.

Como ejemplo, considere el concepto de un punto matemático. En dos dimensiones, un punto es dos
números (coordenadas) que se tratan colectivamente como un solo objeto.
Los puntos a menudo se escriben entre paréntesis con una coma
separando las coordenadas. Por ejemplo, ``(0, 0)`` representa el origen y
``(x, y)`` representa el punto ``x`` unidades a la derecha y ``y`` unidades arriba
desde el origen. Este ``(x,y)`` es el estado del punto.

Pensando en nuestro diagrama anterior, podríamos dibujar un objeto de ``point`` como se muestra aquí.

.. image:: Figures/objectpic2.png
   :alt: A point has an x and a y


Algunas de las operaciones típicas que uno asocia con puntos podrían ser preguntar
el punto para su coordenada x, ``getX``, o para pedir su coordenada y, ``getY``. Desea que este tipo
de funciones estén disponibles para evitar cambios accidentales en estas variables de instancia, ya que al
hacerlo le permitiría ver los valores sin acceder a ellos directamente. Puede que usted también
desee calcular la distancia de un punto desde el origen, o la distancia de un punto desde otro punto,
o encuentre el punto medio entre dos puntos, o responda la pregunta sobre si un punto cae dentro de un
rectángulo o círculo dado. En breve veremos cómo podemos organizar esto junto con los datos.

.. image:: Figures/objectpic3.png
   :alt: A point also has methods


Ahora que entendemos cómo se vería un objeto ``punto``, podemos definir una nueva **clase**.
Queremos que nuestros puntos tengan cada uno un atributo ``x`` y un atributo ``y``,
así que nuestra definición de primera clase se ve así.

.. sourcecode:: python
    :linenos:
    
    class Point:
        """ Point class for representing and manipulating x,y coordinates. """
        
        def __init__(self):
            """ Create a new point at the origin """
            self.x = 0
            self.y = 0          

Las definiciones de clase pueden aparecer en cualquier parte de un programa, pero generalmente están cerca
el comienzo (después de las declaraciones de `` importación ''). Las reglas de sintaxis para una clase
La definición es la misma que para otras declaraciones compuestas. Hay un encabezado
que comienza con la palabra clave, `` clase '', seguida del nombre de la clase,
y terminando con un colon.

Si la primera línea después del encabezado de la clase es una cadena, se convierte en
la cadena de documentación de la clase, y será reconocida por varias herramientas. (Esta
también es la forma en que funcionan las cadenas de documentos en las funciones).

Cada clase debe tener un método con el nombre especial ``__init__``.
este **método de inicializador**, a menudo denominado **constructor**, se llama automáticamente cada vez que
se crea una nueva instancia de ``Point``. Le da la oportunidad al programador
para configurar los atributos requeridos dentro de la nueva instancia dándoles
sus valores de estado iniciales. El parámetro ``self`` (puede elegir cualquier
otro nombre, ¡pero nadie lo hace!) se configura automáticamente para referenciar al
objeto recién creado que necesita ser inicializado.

Entonces usemos nuestra nueva clase Point ahora. La siguiente parte debería parecerle un poco familiar, si recuerda algo de la sintaxis de cómo creamos instancias de la clase Turtle, en el capítulo:ref:`sobre gráficos Turtle <turtles_chap>`.

.. activecode:: chp13_classes1
    
    class Point:
        """ Point class for representing and manipulating x,y coordinates. """
        
        def __init__(self):
 
            self.x = 0
            self.y = 0
    
    p = Point()         # Instantiate an object of type Point
    q = Point()         # and make a second point

    print("Nothing seems to have happened with the points")
    
   
Durante la inicialización de los objetos, creamos dos
atributos llamados `x` e `y` para cada objeto, y les dio a ambos el valor 0. Notará que cuando ejecuta el
programa, no pasa nada. Resulta que este no es el caso. De hecho, se han creado dos ``Puntos``, cada uno
tiene una coordenada x e y con valor 0. Sin embargo, debido a que no le hemos pedido al programa que haga nada con los puntos, no vemos ningún otro resultado.


.. image:: Figures/objectpic4.png
   :alt: Simple object has state and methods



El siguiente programa agrega algunas declaraciones impresas. Puede ver que la salida sugiere que cada uno es un ``objeto Point``.
Sin embargo, tenga en cuenta que el operador ``is`` devuelve ``False``, lo que significa que son objetos diferentes (tendremos más que decir sobre esto en una sección posterior).

.. activecode:: chp13_classes2
    
    class Point:
        """ Point class for representing and manipulating x,y coordinates. """
        
        def __init__(self):
 
            self.x = 0
            self.y = 0
    
    p = Point()         # Instantiate an object of type Point
    q = Point()         # and make a second point

    print(p)
    print(q)

    print(p is q)


Una función como ``Point`` que crea una nueva instancia de objeto
se llama **constructor**. Cada clase usa automáticamente el nombre de la clase como el nombre de la función constructora.
La definición de la función constructora está hecha cuando
escribe la función (método) ``__init__`` dentro de la definición de clase.

Puede ser útil pensar en una clase como una fábrica para hacer objetos.
La clase en sí no es una instancia de un punto, pero contiene la maquinaria
para hacer instancias puntuales. Cada vez que llamas al constructor, preguntas
La fábrica para hacerte un nuevo objeto. Cuando el objeto sale del
línea de producción, su método de inicialización se ejecuta para
configurar el objeto correctamente con su configuración predeterminada de fábrica.

El proceso combinado de "hacerme un nuevo objeto" y "obtener su configuración inicializada
a la configuración predeterminada de fábrica" se llama **instanciación**.

Para obtener una comprensión más clara de lo que sucede cuando se crea una instancia de una nueva instancia, examine el código anterior con CodeLens.

.. codelens:: chp13_classes2a
    
    class Point:
        """ Point class for representing and manipulating x,y coordinates. """
        
        def __init__(self):
 
            self.x = 0
            self.y = 0
    
    p = Point()         # Instantiate an object of type Point
    q = Point()         # and make a second point

    print(p)
    print(q)

    print(p is q)
    
En el Paso 2 de la ejecución de CodeLens, puede ver que ``Point`` se ha vinculado a un objeto que representa la clase ``Point``, pero todavía no hay ninguna instancia. La ejecución de la línea 9, ``p = Point()``, ocurre en los pasos 3-5. Primero, en el paso 3, puede ver que se ha creado una instancia en blanco de la clase, y se pasa como el primer (y único parámetro) al método ``__init__``. El código de ese método se ejecuta, con la variable ``self`` vinculada a esa instancia. En los pasos 4 y 5, se completan dos variables de instancia: ``x`` e ``y`` se establecen en ``0``. No se devuelve nada del método ``__init__``, pero el objeto de punto en sí se devuelve de la llamada a ``Point()``. Por lo tanto, en el paso 7, ``p`` está vinculado al nuevo punto que se creó e inicializó.

Saltando hacia adelante, cuando lleguemos al Paso 14, ``p`` y ``q`` están vinculados a diferentes instancias de ``Point``. Aunque ambos tienen variables de instancia ``x`` e ``y`` establecidas en ``0``, son *objetos diferentes*. Por lo tanto, `` p es q`` se evalúa como ``Falso``.