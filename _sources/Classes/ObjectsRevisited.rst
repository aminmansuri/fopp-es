..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

Objetos Revisitado
--------------------

En Python, cada valor es en realidad un objeto. Ya sea un diccionario, una lista o incluso un número entero, todos son objetos. Los programas manipulan esos objetos ya sea realizando
cálculos con ellos o pidiéndoles que realicen métodos. Para ser más específicos, decimos que un objeto tiene
un **estado** y una colección de **métodos** que puede realizar. (Más información sobre **métodos** a continuación.) El estado de un objeto representa esas cosas
que el objeto sabe de si mismo. El estado se almacena en **variables de instancia**. Por ejemplo, como hemos visto con los objetos de turtle, cada tortuga tiene un estado consistente
de la posición de la tortuga, su color, su rumbo, etc. Cada tortuga también tiene la capacidad de avanzar, retroceder o girar a la derecha o izquierda. Las tortugas individuales son diferentes en eso a pesar de que son
todas tortugas, difieren en los valores específicos de los atributos de estado individuales (tal vez estén en una ubicación diferente o tengan un dirección diferente).



.. image:: Figures/objectpic1.png
   :alt: Simple object has state and methods
