..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: turtle-11-
   :start: 1

.. Week 1 Assessment 3

Evaluación del capítulo - Mecánica de tortugas y objetos
---------------------------------------------------------

**Revisa tu entendimiento**

.. mchoice:: assess_question1_3_1_1_1
   :multiple_answers:
   :answer_a: Tex.forward(20)
   :answer_b: forward() + 20
   :answer_c: forward(20)
   :answer_d: forward(20).Tex
   :answer_e: Tex.forward(10 + 10)
   :correct: a,e
   :feedback_a: Esta es una forma correcta de mover una tortuga hacia adelante.
   :feedback_b: Esto no utiliza el método de tortuga necesario para mover una tortuga hacia adelante. Además, ¿cómo sabría el programa qué tortuga debería moverse?
   :feedback_c: Esto no utiliza el método de tortuga necesario para mover una tortuga hacia adelante. Además, ¿cómo sabría el programa qué tortuga debería moverse?
   :feedback_d: Esta no es la estructura correcta para ejecutar la tarea.
   :feedback_e: Se le permite escribir expresiones dentro de los métodos, por lo que esto se escribe correctamente.
   :practice: T
   :topics: PythonTurtle/InstancesAHerdofTurtles

   ¿Cuáles son las formas correctas de decirle a una tortuga llamada Tex que avance 20 píxeles? Selecciona todas las que apliquen.

.. mchoice:: assess_question1_3_1_1_2
   :answer_a: turtle(Turtle)
   :answer_b: turtle.Turtle()
   :answer_c: Turtle.turtle()
   :answer_d: Turtle(turtle)
   :correct: b
   :feedback_a: Al hacer una nueva instancia de la clase de tortuga, debe usar la notación de puntos.
   :feedback_b: Sí, esta es la forma correcta.
   :feedback_c: tortuga representa la clase y debe ser el primero.
   :feedback_d: Al hacer una nueva instancia de la clase de tortuga, debe usar la notación de puntos.
   :practice: T
   :topics: PythonTurtle/ObjectInstances

   ¿Cuál es la forma correcta de hacer una nueva instancia de la clase Turtle?

.. mchoice:: assess_question1_3_1_1_3
   :answer_a: La clase Turtle
   :answer_b: La misma tortuga que se usa en cada dibujo que hacen sus programas.
   :answer_c: Una 'tortuga' única que puedes usar para dibujar.
   :correct: c
   :feedback_a: Aunque cada instancia usa la clase de tortuga, esta no es la mejor respuesta.
   :feedback_b: Cada instancia que se realiza utilizando la clase tortuga es única. ¿Recuerdas cómo puedes tener múltiples 'tortugas' en un solo dibujo? Cada una de ellas son tortugas diferentes, pero todas son instancias de la clase de tortuga.
   :feedback_c: Sí, una instancia de la clase tortuga representa una tortuga única. La clase de tortuga es como una plantilla o molde que se puede utilizar para hacer tantas tortugas como desee.
   :practice: T
   :topics: PythonTurtle/ObjectInstances

   ¿Qué representa cada instancia de la clase Turtle?


.. mchoice:: assess_question1_3_1_1_5
   :multiple_answers:
   :answer_a: Cambiar el valor de un atributo.
   :answer_b: Retorna valores.
   :answer_c: Cree nuevos atributos de una instancia y establezca sus valores.
   :answer_d: Eliminar instancias de objetos.
   :answer_e: Ninguna de las anteriores.
   :correct: a,b,c
   :feedback_a: Los métodos pueden cambiar el valor asociado con un atributo.
   :feedback_b: Los métodos pueden devolver valores.
   :feedback_c: Los atributos no necesitan ser declarados previamente; cualquier código puede agregar un nuevo atributo a una instancia simplemente asignándole un valor.
   :feedback_d: No elimina explícitamente instancias de objetos; cuando no hay variables u otras referencias a ellas, de modo que no se pueda acceder a ellas, se eliminan automáticamente.
   :feedback_e: Los métodos pueden hacer al menos uno de los anteriores. Echa otro vistazo.
   :practice: T
   :topics: PythonTurtle/ObjectInstances

   Seleccione todas las siguientes cosas que pueden hacer los métodos:


.. mchoice:: assess_question1_3_1_1_6
   :answer_a: student.title()
   :answer_b: title.student()
   :answer_c: title.student
   :answer_d: student(title)
   :answer_e: student.title
   :correct: e
   :feedback_a: Esto accede al atributo pero luego intenta invocarlo como un método, que fallará si el título no es un método.
   :feedback_b: student es el objeto, entonces va antes del punto; el atributo va después.
   :feedback_c: student es el objeto, entonces va antes del punto; el atributo va después.
   :feedback_d: Esta sería la sintaxis para una función de nombre student que se llama en una variable de nombre título.
   :feedback_e: Sí, esta es la sintaxis correcta para usar.
   :practice: T 
   :topics: PythonTurtle/ObjectInstances

   Para una instancia de una clase que se asigna a la variable ``student``, ¿cuál es la forma correcta de referirse a la variable de atributo/instancia de ``título``?

.. fillintheblank:: assess_question1_3_1_1_7
   :practice: T
   :topics: PythonTurtle/ObjectInstances

   ¿Cuál es el nombre del atributo de jane (no método) al que se hace referencia en el siguiente código?

   .. sourcecode:: python

    import turtle

    jane = turtle.Turtle()
    jane.forward(20)
    print(jane.x)

   The attribute is

   -  :x: Good work!
      :jane: Jane es una instancia, no un atributo.
      :forward: forward es un método.
      :turtle: tortuga es la clase, no un atributo.
      :Turtle: Turtle es un método, no un atributo
      :.*: Incorrecto. Inténtelo de nuevo.

.. fillintheblank:: assess_question1_3_1_1_8
   :practice: T
   :topics: PythonTurtle/ObjectInstances

   ¿Cuáles son los nombres de las instancias en el siguiente código? Ponga una instancia por espacio en blanco e ingréselos en el orden en que la computadora los leería.

   .. sourcecode:: python

    import turtle
    wn = turtle.Screen()

    jazz = turtle.Turtle()
    jazz.forward(50)
    jazz.right(90)
    pop = turtle.Turtle()
    pop.left(180)
    pop.forward(76)


   -  :wn: ¡Buen trabajo!
      :jazz: Prueba una ubicación diferente
      :pop: Prueba una ubicación diferente
      :.*: Incorrecto. Inténtelo de nuevo.
   -  :jazz: ¡Buen trabajo!
      :wn: Prueba una ubicación diferente
      :pop: Prueba una ubicación diferente
      :.*: Incorrecto. Inténtelo de nuevo.
   -  :pop: ¡Buen trabajo!
      :wn: Prueba una ubicación diferente
      :jazz: Prueba una ubicación diferente
      :.*: Incorrecto. Inténtelo de nuevo.


Evaluación del capítulo: dibujar con tortuga
---------------------------------------------

.. activecode:: assess_ps_01_09a
    :language: python

    Escriba el código para dibujar un pentágono regular (una figura de cinco lados con todos los lados de la misma longitud).

    ~~~~
    import turtle



.. activecode:: assess_ps_01_09
    :language: python

    Escribe un programa que use el módulo de tortuga para dibujar algo. No tiene que ser complicado, pero dibuja algo diferente de lo que hemos hecho en el pasado. (Sugerencia: si está dibujando algo complicado, podría ser tedioso verlo dibujar una y otra vez. Intente configurar ``.speed(10)`` para que la tortuga dibuje rápido, o ``.speed(0)`` para que dibuje súper rápido sin animación).
    ~~~~
    import turtle

