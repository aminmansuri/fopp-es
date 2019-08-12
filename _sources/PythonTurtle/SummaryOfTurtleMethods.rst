..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: turtle-6-
   :start: 1

Resumen de los métodos de turtle
---------------------------------

==========  ==========  =========================
Método      Parametros  Descripción
==========  ==========  =========================
Turtle      Ninguno       Crea y devuelve un nuevo objeto tortuga
forward     distancia     Mueve la tortuga hacia adelante
backward    distancia     Mueve la tortuga hacia atrás
right       ángulo        Gira la tortuga en sentido horario
left        ángulo        Gira la tortuga en sentido antihorario
up          Ninguno       Levanta la cola de las tortugas
down        Ninguno       Baja la cola de las tortugas
color       color         Cambia el color de la cola de la tortuga
fillcolor   color         Cambia el color de la tortuga que usará para llenar un polígono
heading     Ninguno       Devuelve la orientación actual en grados
position    Ninguno       Devuelve la posición actual
goto        x,y           Mueve la tortuga a la posición x, y
begin_fill  Ninguno       Recuerde el punto de partida para un polígono relleno
end_fill    Ninguno       Cierre el polígono y rellene con el color de relleno actual.
dot         Ninguno       Deja un punto en la posición actual
stamp       Ninguno       Deja una impresión de la forma de una tortuga en la ubicación actual
shape       Figura        Debe ser 'arrow', 'triangle', 'classic', 'turtle', 'circle', o 'square'
speed       integer       0 = sin animation, más rápido; 1 = más despacio; 10 = muy rápido
==========  ==========  =========================

Una vez que se sienta cómodo con los conceptos básicos de los gráficos de tortugas, puede leer incluso
más opciones en `Python Docs Website <http://docs.python.org/dev/py3k/library/turtle.html>`_.  note que
vamos a describir Python Docs con más detalle en el siguiente capítulo.
