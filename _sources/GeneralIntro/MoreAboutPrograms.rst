..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: intro-5-
   :start: 1

.. index:: lenguaje formal, lenguaje natural, análisis, token

Más acerca de los programas
---------------------------

Un **programa** es una secuencia de instrucciones que especifican cómo realizar un
cálculo. El cálculo puede ser algo tan complejo como representar una página html en un navegador web
o codificar un video y transmitirlo a través de la red. También puede ser un
cálculo simbólico, como buscar y reemplazar texto en un documento o
(curiosamente) compilar un programa.

Los detalles se ven diferentes en diferentes idiomas, pero algunas instrucciones básicas
aparecen en casi todos los idiomas.

entrada
    Obtiene datos del teclado, un archivo u otro dispositivo.

salida
    Muestra datos en la pantalla o envia datos a un archivo u otro dispositivo.

matemática y lógica
    Realiza operaciones matemáticas básicas como la suma y la multiplicación,
    y operaciones lógicas como ``and``, ``or`` y ``not``.

ejecución condicional
    Verifique ciertas condiciones y ejecute la secuencia apropiada de
    declaraciones.

repetición
    Realice alguna acción repetidamente, generalmente con alguna variación.

Lo crea o no, eso es todo lo que hay que hacer. Cada programa que tiene
alguna vez será utilizado, no importa cuán complicado, se compone de instrucciones que se ven más
o menos como estos. Por lo tanto, podemos describir la programación como el proceso de
dividir una tarea grande y compleja en subtareas cada vez más pequeñas hasta que
las subtareas son lo suficientemente simples como para realizarse con secuencias de estas instrucciones de
elementos básicos.


Vista previa de estructuras de control
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Todavía no profundizaremos en las estructuras de control de Python, ¡pero es bueno mencionarlas temprano para darle una idea de lo que puede hacer con el lenguaje!
Si esto tiene sentido para usted ahora, ¡eso es genial!
Sin embargo, no esperamos que entienda esto todavía; la comprensión vendrá más tarde.

Primero tenemos estructuras que nos permiten iterar sobre algo.
Podemos mirar las cadenas carácter por carácter o las listas elemento por elemento hasta que hayamos llegado al final de ellas utilizando algo llamado bucle ``for``.

.. activecode:: ac1_5_1

   para el character en "Cool string":
       print(character)

También podemos iterar sin un punto de detención definido con bucles ``while``.
Puede usar esto si desea recibir información del usuario de su programa, pero no sabe cuánto tiempo tardará en hacerlo con su código.

.. activecode:: ac1_5_2

   grocery_item = ""
   while grocery_item != "done":
       grocery_item = input("Escriba un artículo para agregar a su lista de compras. Cuando haya terminado de escribir la lista, simplemente escriba: done")
       print(grocery_item)

Otras estructuras nos permitirán ejecutar solo partes de nuestros programas o solo realizar alguna tarea si se encuentra un cierto conjunto de condiciones.
Los condicionales, como se los llama, nos permiten hacer eso.
Vea cómo agregar condicionales a nuestro código puede cambiar lo que podemos escribir sobre las compras de comestibles.

.. activecode:: ac1_5_3

   grocery_item = ""
   grocery_list = []
   while grocery_item != "done":
       grocery_item = input("Escriba un artículo para agregar a su lista de compras. Cuando haya terminado de escribir la lista, simplemente escriba: done")
       if grocery_item == 'done':
           continue
       else:
           print("Agregar el elemento a la lista")
           grocery_list.append(grocery_item)
   print("Aquí está nuestra lista de compras:")
   print(grocery_list)

**Revisa tu entendimiento**

.. mchoice:: question1_5_1
   :answer_a: Una secuencia de instrucciones que especifica cómo realizar un cálculo.
   :answer_b: Algo que sigues en una obra de teatro o concierto.
   :answer_c: Un cálculo, incluso un cálculo simbólico.
   :answer_d: Lo mismo que un algoritmo.
   :correct: a
   :feedback_a: Son solo instrucciones paso a paso que la computadora puede entender y ejecutar. Los programas a menudo implementan algoritmos, pero tenga en cuenta que los algoritmos suelen ser menos precisos que los programas y no tienen que estar escritos en un lenguaje de programación.
   :feedback_b: Verdadero, pero no en este contexto. Nos referimos a un programa relacionado con una computadora.
   :feedback_c: Un programa puede realizar un cálculo, pero por sí solo no es uno.
   :feedback_d: Los programas a menudo implementan algoritmos, pero no son lo mismo. Un algoritmo es una lista de instrucciones paso a paso, pero esas instrucciones no son necesariamente lo suficientemente precisas para que una computadora las siga. Un programa debe estar escrito en un lenguaje de programación que la computadora sepa interpretar.

   Un programa es: