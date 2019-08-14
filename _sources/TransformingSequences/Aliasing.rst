..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: seqmut-4-
   :start: 1

Creando Alias
--------------

Como las variables se refieren a objetos, si asignamos una variable a otra, ambas
variables se refieren al mismo objeto:

.. activecode:: ac8_4_1
    
    a = [81, 82, 83]
    b = a
    print(a is b)
    
En este caso, el diagrama de referencia se ve así:

.. image:: Figures/refdiag4.png
   :alt: State snapshot for multiple references (aliases) to a list 

Debido a que la misma lista tiene dos nombres diferentes, ``a`` y ``b``, decimos que
tiene **alias**. Los cambios realizados con un alias afectan al otro. En el ejemplo de codelens
a continuación, puede ver que ``a`` y ``b`` se refieren a la misma lista después de ejecutar la instrucción de asignación ``b = a``.


.. activecode:: ac8_4_2

    a = [81,82,83]
    b = [81,82,83]
    print(a is b)

    b = a
    print(a == b)
    print(a is b)

    b[0] = 5
    print(a)



Aunque este comportamiento puede ser útil, a veces es inesperado o
indeseable. En general, es más seguro evitar el alias cuando estás trabajando
con objetos mutables. Por supuesto, para objetos inmutables, no hay problema.
Es por eso que Python se siente libre para crear alias de cadenas y enteros cuando ve la oportunidad de
economizar.

**Revisa tu entendimiento**


.. mchoice:: question8_1_3
   :answer_a: ['Jamboree', 'get-together', 'party']
   :answer_b: ['celebration']
   :answer_c: ['celebration', 'Jamboree', 'get-together', 'party']
   :answer_d: ['Jamboree', 'get-together', 'party', 'celebration']
   :correct: a
   :feedback_a: Sí, el valor de *y* se ha reasignado al valor de w.
   :feedback_b: No, ese era el valor inicial de y, pero y ha cambiado.
   :feedback_c: No, cuando asignamos una lista a otra lista, no concatena las listas juntas.
   :feedback_d: No, cuando asignamos una lista a otra lista, no concatena las listas juntas.
   :practice: T

   ¿Cuál es el valor de *y* después de que se haya evaluado el siguiente código?

   .. code-block:: python

      w = ['Jamboree', 'get-together', 'party']
      y = ['celebration']
      y = w



.. mchoice:: question8_4_1
   :answer_a: [4,2,8,6,5]
   :answer_b: [4,2,8,999,5]
   :correct: b
   :feedback_a: blist no es una copia de alist, es una referencia a la lista a la que se refiere alist.
   :feedback_b: Sí, ya que alist y blist ambos hacen referencia a la misma lista, los cambios a uno también cambian al otro.
   :practice: T

   ¿Qué se imprime en las siguientes declaraciones?
   
   .. code-block:: python

     alist = [4,2,8,6,5]
     blist = alist
     blist[3] = 999
     print(alist)
