..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: exceptions-2-
   :start: 1

.. index:: exception, flow-of-control, raise, try: except:

Excepciones estándar
====================

La mayoría de las *excepciones* estándar integradas en Python se enumeran a continuación.
Se organizan en grupos relacionados en función de los tipos de problemas que tratan.

========================  =============================================
Excepciones del lenguaje  Descripción
========================  =============================================
Clase StandardError       Clase base para todas las excepciones integradas excepto
                          StopIteration y SystemExit.
ImportError               Se genera cuando falla una declaración de importación.
SyntaxError               Se genera cuando hay un error en la sintaxis de Python.
IndentationError          Se genera cuando la identación no se especifica correctamente.
NameError                 Se genera cuando no se encuentra un identificador en el
                          namespace local o global.
UnboundLocalError         Se genera al intentar acceder a una variable local en un
                          función o método pero no se le ha asignado ningún valor.
TypeError                 Se genera cuando se intenta una operación o función que
                          no es válida para el tipo de dato especificado.
LookupError               Clase base para todos los errores de búsqueda.
IndexError                Se genera cuando no se encuentra un índice en una secuencia.
KeyError                  Se genera cuando la clave especificada no se encuentra en el diccionario.
ValueError                Se genera cuando la función integrada para un tipo de datos tiene
                          el tipo válido de argumentos, pero los argumentos tienen
                          valores no válidos especificados
RuntimeError              Se genera cuando un error generado no cae en ninguna categoría.
MemoryError               Se genera cuando una operación se queda sin memoria.
RecursionError            Se genera cuando se excede la profundidad máxima de recursión.
SystemError               Se genera cuando el intérprete encuentra un problema interno,
                          pero cuando se encuentra este error el intérprete de Python
                          no se detiene.
========================  =============================================

============================  ================================================
Excepciones de la clase Math  Descripción
============================  ================================================
ArithmeticError	              Clase base para todos los errores que ocurren para el cálculo numérico.
                              Sabes que ocurrió un error matemático, pero no cuál es el error específico
OverflowError                 Se genera cuando un cálculo excede el límite máximo para un tipo numérico
FloatingPointError            Se genera cuando falla un cálculo de coma flotante.
ZeroDivisonError              Se genera cuando la división o módulo por cero tiene lugar para
                              todos los tipos numéricos.
============================  ================================================

=====================  ================================================
Excepciones de E/S     Descripción
=====================  ================================================
FileNotFoundError      Se genera cuando se solicita un archivo o directorio que no existe.
IOError                Se genera cuando falla una operación de entrada/salida, como
                       la instrucción print o la función open() al intentar
                       abrir un archivo que no existe. También generado por
                       errores relacionados con el sistema operativo.
PermissionError        Se genera al intentar ejecutar una operación sin los
                       derechos de acceso adecuados.
EOFError               Se genera cuando no hay entrada desde raw_input ()
                       o input () y se alcanza el final del archivo.
KeyboardInterrupt      Se genera cuando el usuario interrumpe la ejecución del programa,
                       generalmente presionando Ctrl+c.
=====================  ================================================

=====================  ================================================
Otras Excepciones       Descripción
=====================  ================================================
Exception              Clase base para todas las excepciones. Esto atrapa más
                       mensajes de excepción
StopIteration          Se genera cuando el método next() de un iterador
                       no apunta a ningún objeto.
AssertionError         Se genera en caso de falla de la declaración Assert.
SystemExit             Se genera cuando se cierra el intérprete de Python utilizando
                       la función sys.exit (). Si no se maneja en el código,
                       hace que el intérprete detenga.
OSError                Se genera por errores relacionados con el sistema operativo.
EnvironmentError       Clase base  para todas las excepciones que se producen fuera de
                       entorno de Python.
AttributeError         Se genera en caso de falla de una referencia de atributo
                       o asignación
NotImplementedError    Se genera cuando no se implementa un método abstracto en una clase
                       heredada

=====================  ================================================

Todas las excepciones son objetos.
Las clases que definen los objetos están organizadas en una jerarquía que se muestra a continuación. Esto es importante porque la clase padre
de un conjunto de excepciones relacionadas capturará todos los mensajes de excepción para
sí mismo y su hijo. Por ejemplo, un ``ArithmeticError``, la excepción se atrapará a sí misma
y todos las excepciones ``FloatingPointError``, ``OverflowError``, y ``ZeroDivisionError``.

.. code-block:: Python

  BaseException
   +-- SystemExit
   +-- KeyboardInterrupt
   +-- GeneratorExit
   +-- Exception
        +-- StopIteration
        +-- StopAsyncIteration
        +-- ArithmeticError
        |    +-- FloatingPointError
        |    +-- OverflowError
        |    +-- ZeroDivisionError
        +-- AssertionError
        +-- AttributeError
        +-- BufferError
        +-- EOFError
        +-- ImportError
        +-- LookupError
        |    +-- IndexError
        |    +-- KeyError
        +-- MemoryError
        +-- NameError
        |    +-- UnboundLocalError
        +-- OSError
        |    +-- BlockingIOError
        |    +-- ChildProcessError
        |    +-- ConnectionError
        |    |    +-- BrokenPipeError
        |    |    +-- ConnectionAbortedError
        |    |    +-- ConnectionRefusedError
        |    |    +-- ConnectionResetError
        |    +-- FileExistsError
        |    +-- FileNotFoundError
        |    +-- InterruptedError
        |    +-- IsADirectoryError
        |    +-- NotADirectoryError
        |    +-- PermissionError
        |    +-- ProcessLookupError
        |    +-- TimeoutError
        +-- ReferenceError
        +-- RuntimeError
        |    +-- NotImplementedError
        |    +-- RecursionError
        +-- SyntaxError
        |    +-- IndentationError
        |         +-- TabError
        +-- SystemError
        +-- TypeError
        +-- ValueError
        |    +-- UnicodeError
        |         +-- UnicodeDecodeError
        |         +-- UnicodeEncodeError
        |         +-- UnicodeTranslateError
        +-- Warning
             +-- DeprecationWarning
             +-- PendingDeprecationWarning
             +-- RuntimeWarning
             +-- SyntaxWarning
             +-- UserWarning
             +-- FutureWarning
             +-- ImportWarning
             +-- UnicodeWarning
             +-- BytesWarning
             +-- ResourceWarning



