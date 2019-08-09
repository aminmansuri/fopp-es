..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: intro-9-
   :start: 1

👩‍💻 Para comprender un programa, ¡Modifíquelo!
=================================================

Para verificar su comprensión o sus predicciones, va a ejecutar un programa.

Para verificar su comprensión sobre el estado de las variables antes de que se ejecute su fragmento de código, agregue impresión de diagnóstico
declaraciones que imprimen los tipos y valores de variables. Agregue estas declaraciones de impresión justo *antes* del fragmento de código
que estás tratando de entender.

Si realizó una predicción sobre el resultado que se generará cuando se ejecute el fragmento de código, entonces puede ejecutar
el programa. Sin embargo, si hizo una predicción sobre un cambio que ocurre en el valor de una variable, necesitará agregar una
declaración de impresión de diagnóstico adicional justo después de la línea de código que cree que debería cambiar esa variable.

Las declaraciones de impresión de diagnóstico son temporales. Una vez que haya verificado que un programa está haciendo lo que cree que está
haciendo, eliminará estas declaraciones de impresión adicionales.

Sin embargo, incluso si cree que tiene un buen conocimiento del programa, le recomendamos cambiarlo al menos algunas veces para ver si comprende cómo se comporta en diferentes situaciones. ¡A veces te sorprenderás!
Si tiene alguna sorpresa, entonces querrá revisar su comprensión o sus predicciones. Si estabas equivocado
sobre los valores o tipos de variables antes de que se ejecutara el fragmento de código, es posible que desee revisar su comprensión del
código anterior. Una vez que comprenda cómo surgió ese resultado, debe hacer algunos cambios en el programa para asegurarse de que su nueva comprensión sea precisa.
