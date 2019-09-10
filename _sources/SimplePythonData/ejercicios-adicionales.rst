
.. qnum::
   :prefix: data-19-
   :start: 1

.. Deber#1

Ejercicios Adicionales
----------------------

**Revisa tu entendimiento**

.. clickablearea:: fopp-es-d1-1
    :question: Haga click en todas las sentencias de asignación
    :iscode:
    :feedback: Recuerda, el operador "=" es utilizado para asignar

    :click-incorrect:def main()::endclick:
        :click-correct:x = 4:endclick:
        :click-correct:nombre = 'juan':endclick:
        for i in range(5):
            :click-correct:y = i:endclick:
            :click-incorrect:if y == 2::endclick:
                :click-incorrect:print('y=5'):endclick:

.. clickablearea:: fopp-es-d1-2
    :question: Haga click en todas las sentencias de impresión
    :iscode:
    :feedback: Recuerda, "print" es utilizado para asignar

    :click-incorrect:def main()::endclick:
        :click-incorrect:x = 4:endclick:
        :click-incorrect:nombre = 'juan':endclick:
        :click-incorrect:for i in range(5)::endclick:
            :click-incorrect:y = i:endclick:
            :click-incorrect:if y == 2::endclick:
                :click-correct:print('y=5'):endclick:


.. sourcecode:: python

    z = "uno"
    y = ''' dos
    x = 1
    z = 2
    y = 'tres'''
    print(z)

.. fillintheblank:: fopp-es-d1-3

   Qué imprime el código anterior?


    - :uno: Correcto!
      :"uno": Cerca, pero las comillas están de más.
      :.*: Recuerda cómo funcionan los comentarios y string de varias líneas
