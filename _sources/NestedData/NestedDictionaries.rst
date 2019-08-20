..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: nested-2-
   :start: 1

Diccionarios Anidados
----------------------

Así como las listas pueden contener elementos de cualquier tipo, el valor asociado con una clave en un diccionario también puede ser un objeto de cualquier
tipo. En particular, a menudo es útil tener una lista o un diccionario como valor en un diccionario. Y por supuesto, esas listas
o diccionarios también pueden contener listas y diccionarios. Puede haber muchas capas de anidamiento.

Solo los valores en los diccionarios pueden ser objetos de tipo arbitrario. Las claves en los diccionarios deben ser uno de los
tipos de datos inmutables (números, cadenas, tuplas).



**Revisa tu Entendimiento**

.. mchoice:: question17_2_1
   :practice: T
   :multiple_answers:
   :answer_a: d[5] = {1: 2, 3: 4}
   :answer_b: d[{1:2, 3:4}] = 5
   :answer_c: d['key1']['d'] = d['key2']
   :answer_d: d[key2] = 3
   :correct: a,c
   :feedback_a: 5 es una clave válida; {1:2, 3:4} es un diccionario con dos claves, y es un valor válido para asociar con la clave 5.
   :feedback_b: las claves del diccionario deben ser de tipos inmutables. Un diccionario no se puede usar como clave en un diccionario.
   :feedback_c: d['key2'] es {'b': 3, 'c': "yes"}, un objeto python. Se puede vincular a la clave 'd' en un diccionario {'a': 5, 'c': 90, 5: 50}
   :feedback_d: key2 es una variable independiente aquí. d['clave2'] estaría bien.
    
   ¿Cuál de las siguientes es una declaración de asignación legal, después de que se ejecuta el siguiente código?
    
   .. code-block:: python 
    
       d = {'key1': {'a': 5, 'c': 90, 5: 50}, 'key2':{'b': 3, 'c': "yes"}}

.. activecode:: ac17_2_1
   :language: python
   :autograde: unittest
   :practice: T

   **1.** Extraiga el valor asociado con la clave color y asígnelo a la variable ``color``. No haga *hard code* para esto.

   ~~~~

   info = {'personal_data': 
            {'name': 'Lauren',
             'age': 20,
             'major': 'Information Science',
             'physical_features':
                {'color': {'eye': 'blue',
                           'hair': 'brown'},
                 'height': "5'8"}
            },
          'other':
            {'favorite_colors': ['purple', 'green', 'blue'],
             'interested_in': ['social media', 'intellectual property', 'copyright', 'music', 'books']
            }
         }

   =====

   from unittest.gui import TestCaseGui

   class myTests(TestCaseGui):

      def testOne(self):
         self.assertEqual(color, {'eye': 'blue', 'hair': 'brown'}, "Testing that color has the correct value.")

   myTests().main()

