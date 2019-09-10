
.. qnum::
   :prefix: data-20-
   :start: 1

.. Deber#1

Deber#1
-------

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



.. fillintheblank:: fopp-es-d1-3

   ¿Qué imprime el siguiente código?

    .. sourcecode:: none

        z = "uno"
        y = ''' dos
        x = 1
        z = 2
        y = 'tres'''
        print(z)

   Imprime

   -  :uno: Correcto!
      :"uno": Cerca, pero las comillas están de más.
      :.*: Recuerda cómo funcionan los comentarios y string de varias líneas.

.. fillintheblank:: fopp-es-d1-4

   Inserta el mínimo número de paréntesis para que el siguiente código se evalúe a 4.5

    .. sourcecode:: none

        8+3*2+1-6/4+1-9

   Ingrese aquí su respuesta (sin espacios)

   -  :8\+3\*\(2\+1-6\/4\)\+1\-9: Correcto!
      :.*: Escribe 8+3*2+1-6/4+1-9 pero ingresa paréntesis en los lugares correctos (tal vez ingresaste muchos?).


.. activecode:: fopp-es-d1-5
    :language: python
    :autograde: unittest

    Recuerde la fórmula para resolver ecuaciones de segundo grado:

    .. image:: Figures/eq_cuadratica.png
       :alt: reassignment

    Complete la función siguiente para que cubra el caso '+' de esta fórmula (no te preocupes por el segundo caso).
    ~~~~

    def equacion_cuadratica(a,b,c):
        return 4

    ====
    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):

        def testOne(self):
            val = equacion_cuadratica(5,6,1)
            if (-0.2 == val) :
                self.assertAlmostEqual(val,-0.2)
                self.assertAlmostEqual(equacion_cuadratica(-1,1,6),-2.0)
            elif ((-0.2,-1.0)== val) :
                self.assertEqual(val,(-0.2,-1.0))
                self.assertEqual(equacion_cuadratica(-1,1,6),(-2.0,3.0))
            else :
                self.assertTrue(False, "Revisa tu código")

    myTests().main()