..  Copyright (C)  Paul Resnick.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".


👩‍💻 Cuándo usar try/except
----------------------------

Debe usar try/except cuando tiene un bloque de código para ejecutar que a veces se ejecutará correctamente y otras no, dependiendo de las condiciones que no puede prever en el momento en que escribe el código.

Por ejemplo, cuando ejecuta código que obtiene datos de un sitio web, puede ejecutar el código cuando no tiene una conexión de red o cuando el sitio web externo no responde temporalmente. Si su programa aún puede hacer algo útil en esas situaciones, le gustaría manejar la excepción y ejecutar el resto de su código.

Como otro ejemplo, supongamos que ha obtenido algunos datos anidados de un sitio web en un diccionario d. Cuando intenta extraer elementos específicos, pueden faltar algunos: d puede no incluir una clave en particular, por ejemplo. Si anticipa que una clave en particular podría no estar presente, puede escribir un cheque if..else para encargarse de ello.

.. sourcecode:: python

    if somekey in d:
        # it's there; extract the data
        extract_data(d)
    else:
        skip_this_one(d)

Sin embargo, si extrae muchos datos diferentes, puede ser tedioso verificarlos todos. Puede atrapar toda la extracción de datos en un try/except

.. sourcecode:: python

    try:
        extract_data(d)
    except:
        skip_this_one(d)

Se considera una mala práctica atrapar todas las excepciones de esta manera. En cambio, python proporciona un mecanismo para especificar solo ciertos tipos de excepciones que detectará (por ejemplo, solo capturando excepciones de tipo KeyError, que ocurre cuando falta una clave en un diccionario.

.. sourcecode:: python

    try:
        extract_data(d)
    except KeyError:
        skip_this_one(d)

No entraremos en más detalles sobre el manejo de excepciones en este curso introductorio. Mira la sección `tutorial de Python sobre manejo de errores <https://docs.python.org/3/tutorial/errors.html>`_ en el sitio oficial  si te interesa saber más.