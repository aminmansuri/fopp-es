..  Copyright (C)  Paul Resnick, Jaclyn Cohen.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. _thinking_about_classes:

Pensando En Clases e Instancias
------------------------------------

Ahora puede imaginar algunas razones por las que puede querer definir una clase. Ha visto ejemplos de creación de tipos que son más complicados o específicos que los integrados en Python (como listas o cadenas). ``Turtle``, con todas las variables de instancia y métodos que aprendió sobre el uso anterior en el semestre, es una clase que los programadores definieron y que ahora está incluida en el lenguaje Python. En este capítulo, definimos ``Point`` con alguna funcionalidad que puede facilitar la escritura de programas que involucran instancias de ``Point`` de coordenadas ``x,y``. Y en breve, verás cómo puedes definir clases para representar objetos en un juego.

También puede usar clases autodefinidas para almacenar datos, por ejemplo, los datos que obtiene al realizar una solicitud a una API REST.

Antes de decidir definir una nueva clase, hay algunas cosas a tener en cuenta y preguntas que debe hacerse:

* **¿Cuáles son los datos que desea tratar?** (Datos sobre un montón de canciones de iTunes? Datos sobre un montón de tweets de Twitter? Datos sobre un montón de búsquedas de hashtag en Twitter? Dos números que representan coordenadas de un punto en un plano bidimensional?)

* **¿Qué representará una instancia de su clase?** En otras palabras, ¿qué tipo de *cosa* nueva en su programa debería tener una funcionalidad elegante? ¿Una canción? ¿Un hashtag? ¿Un tweet? ¿Un punto? La respuesta a esta pregunta debería ayudarlo a decidir cómo llamar a la clase que defina.

* **¿Qué información debe tener cada instancia como variables de instancia?** Esto está relacionado con lo que representa una instancia. Vea si puede convertirlo en una oración. *"Cada instancia representa una <canción> y cada <canción> tiene un <artista> y un <título> como variables de instancia."* O, *"Cada instancia representa un <Tweet> y cada <Tweet> tiene un <usuario (quién lo publicó)> y <una cadena de contenido del mensaje> como variables de instancia ".*

* **¿Qué métodos de instancia debe tener cada instancia?** ¿Qué *debe poder hacer* cada instancia? Para continuar usando los mismos ejemplos: tal vez cada canción tiene un método que utiliza una API de letras para obtener una larga cadena de letras. Tal vez cada canción tiene un método que devuelve una cadena del nombre de su artista. O para un tweet, tal vez cada tweet tiene un método que devuelve la longitud del mensaje del tweet. (¡Enloquecer!)

* **¿Cómo debería ser la versión impresa de una instancia?** (Esta pregunta lo ayudará a determinar cómo escribir el método ``__str__``). Quizás, "Cada canción impresa mostrará el título de la canción y el nombre del artista nombre." o "Cada Tweet impreso mostrará el nombre de usuario de la persona que lo publicó y el contenido del mensaje del tweet".

Después de considerar esas preguntas y tomar decisiones sobre cómo comenzará con una definición de clase, puede comenzar a definir su clase.

Recuerde que una definición de clase, como una definición de función, es una descripción general de lo que *debería tener cada instancia de la clase*. (Cada punto tiene una ``x`` y una ``y``.) Las instancias de clase son específicas: p. el Punto con *una x e y específica>.* Es posible que tenga un Punto con un valor de ``x`` de 3 y un valor de ``y`` de 2, así que para esa *instancia* particular de la *clase* ``Point``, pasaría ``3`` y ``2`` al constructor, el método ``__init__``, así: ``new_point = Point(3,2)``, como viste en las últimas secciones.

