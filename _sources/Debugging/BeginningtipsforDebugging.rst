..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: debug-2-
   :start: 1

👩‍💻 Consejos iniciales para la depuración
------------------------------------------------

La depuración de un programa es una forma diferente de pensar qué escribir en un programa. El proceso de depuración es como ser un detective. Aquí hay algunas reglas para que pienses en la depuración.

#. ¡Todos son sospechosos (excepto Python)! Es común que los programadores principiantes culpen a Python, pero ese debería ser su último recurso. Recuerde que Python ha sido utilizado para resolver problemas de nivel CS1 millones de veces por millones de otros programadores. Entonces, Python probablemente no sea el problema.

#. Comprueba tus suposiciones. En este punto de su carrera, todavía está desarrollando su modelo mental de cómo Python hace su trabajo. Es natural pensar que su código es correcto, pero con la depuración debe hacer que su código sea el principal sospechoso. Incluso si cree que es correcto, debe verificar que realmente lo es utilizando generosamente sentencias de impresión para verificar que los valores de las variables realmente son lo que cree que deberían ser. Te sorprenderás con qué frecuencia no lo son.

#. Encuentra pistas. Este es el trabajo más importante del detective y en este momento hay dos tipos importantes de pistas para que entiendas.

   * Mensajes de Error

   * Impresión de Sentencias

Estos son Tres tipos de errores que pueden ocurrir en un programa: `errores de sintaxis
<http://en.wikipedia.org/wiki/Syntax_error>`__, `errores en tiempo de ejecución
<http://en.wikipedia.org/wiki/Runtime_error>`__, y `errores semánticos
<http://en.wikipedia.org/wiki/Logic_error>`__.  Es útil distinguir
entre ellos para rastrearlos más rápidamente.
