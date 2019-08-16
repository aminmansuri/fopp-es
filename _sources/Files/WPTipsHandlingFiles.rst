..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: files-11-
   :start: 1

👩‍💻 Consejos para manejar archivos
======================================

Al trabajar con archivos, hay algunas cosas a tener en cuenta. Al nombrar archivos, es mejor no incluir espacios.
Si bien la mayoría de los sistemas operativos pueden manejar archivos con espacios en sus nombres, no todos pueden hacerlo.

Además, los sufijos en los nombres de archivos, por ejemplo, el .txt en ``FileNameExample.txt``, no son mágicos. En cambio, estos
sufijos son una convención. Para algunos sistemas operativos, los sufijos no tienen un significado especial, y solo tienen significado cuando son
utilizados en un programa. Otros sistemas operativos infieren información de los sufijos; por ejemplo, ``.EXE`` es un sufijo que
significa que un archivo es ejecutable.

Es una buena idea seguir las convenciones. Si un archivo contiene datos con formato CSV, asígnele el nombre con la extensión ``.csv``, no ``.txt``. Un programa de Python podrá leerlo de cualquier manera, pero si sigue la convención, ayudará a otras personas a adivinar qué hay en el archivo. Y también ayudará al sistema operativo de la computadora a adivinar qué programa de aplicación debe abrir cuando haga doble clic en el archivo.
