..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

:skipreading:`True`

.. qnum::
   :prefix: modules-5-
   :start: 1

Ejercicios
----------

#.  .. tabbed:: q1

        .. tab:: Pregunta

           .. actex:: ac13_5_1

              Use una sentencia ``for`` para imprimir 10 números aleatorios.
              ~~~~

        .. tab:: Respuesta

            .. activecode:: answer_ac13_5_1

               import random

               howmany = 10
               for counter in range(howmany):
                   arandom = random.random()
                   print(arandom)


#.  .. tabbed:: q2

        .. tab:: Pregunta

            .. actex:: ac13_5_2

               Repita el ejercicio anterior pero esta vez imprima 10 números aleatorios entre 25 y 35.
               ~~~~

