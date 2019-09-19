..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: moreiter-7-
   :start: 1

Iteración anidada: procesamiento de imágenes
---------------------------------------------

Las tablas bidimensionales tienen tanto filas como columnas. Probablemente haya visto muchas tablas como esta si ha utilizado un
hoja de cálculo. Otro objeto que está organizado en filas y columnas es una imagen digital. En esta sección lo haremos
Explore cómo la iteración nos permite manipular estas imágenes.

Una **imagen digital** es una colección finita de elementos de imagen pequeños y discretos llamados **píxeles**. Estos píxeles son
organizado en una cuadrícula bidimensional. Cada píxel representa la cantidad más pequeña de información de imagen que es
disponible. Algunas veces estos píxeles aparecen como pequeños "puntos".

Cada imagen (cuadrícula de píxeles) tiene su propio ancho y su propia altura. El ancho es el número de columnas y el alto es
El número de filas. Podemos nombrar los píxeles en la cuadrícula utilizando el número de columna y el número de fila. Sin embargo, es muy
Es importante recordar que a los informáticos les gusta comenzar a contar con 0. Esto significa que si hay 20 filas,
se llamará 0,1,2, y así hasta el 19. Esto será muy útil más adelante cuando iteremos usando el rango.


En la figura siguiente, el píxel de interés se encuentra en la columna **c** y la fila **r**.
.. image:: Figures/image.png

El modelo de color RGB
^^^^^^^^^^^^^^^^^^^^^^^

Cada píxel de la imagen representará un solo color. El color específico depende de una fórmula que mezcle varias cantidades.
de tres colores básicos: rojo, verde y azul. Esta técnica para crear color se conoce como **Modelo de color RGB**.
La cantidad de cada color, a veces llamada **intensidad** del color, nos permite tener un control muy fino sobre el
color resultante

El valor de intensidad mínimo para un color básico es 0. Por ejemplo, si la intensidad del rojo es 0, entonces no hay rojo en el
píxel La intensidad máxima es 255. Esto significa que en realidad hay 256 cantidades diferentes de intensidad para cada base
color. Como hay tres colores básicos, eso significa que puede crear 256\ :sup:`3` colores distintos usando el modelo de color RGB.

Aquí están las intensidades de rojo, verde y azul para algunos colores comunes. Tenga en cuenta que "Negro" está representado por
un píxel que no tiene color básico. Por otro lado, "Blanco" tiene valores máximos para los tres componentes básicos de color.

 	 =======  =======  =======  =======
	 Color    Red      Green    Blue
	 =======  =======  =======  =======
	 Red      255      0        0
	 Green    0        255      0
	 Blue     0        0        255
	 White    255      255      255
	 Black    0        0        0
	 Yellow   255      255      0
	 Magenta  255      0        255
	 =======  =======  =======  =======

Para manipular una imagen, necesitamos poder acceder a píxeles individuales. Esta capacidad es proporcionada por un módulo
llamado **image**, proporcionado en ActiveCode [1]_. El módulo de image define dos clases: ``Image`` y ``Pixel``.

.. [1] Si desea explorar el procesamiento de imágenes por su cuenta fuera del navegador, puede instalar el módulo cImage desde http://pypi.org.

Cada objeto Pixel tiene tres atributos: la intensidad roja, la intensidad verde y la intensidad azul. Un píxel proporciona
tres métodos que nos permiten preguntar por los valores de intensidad. Se llaman ``getRed``, ``getGreen`` y ``getBlue``.
Además, podemos pedirle a un píxel que cambie un valor de intensidad usando sus métodos ``setRed``, ``setGreen`` y ``setBlue``.


    =================  ================            =========================================================
    Nombre del método  Ejemplo                     Explicación
    =================  ================            =========================================================
    Pixel(r,g,b)       Pixel(20,100,50)                 Cree un nuevo píxel con 20 rojos, 100 verdes y 50 azules.
    getRed()           r = p.getRed()                   Devuelve la intensidad del componente rojo.
    getGreen()         r = p.getGreen()                 Devuelve la intensidad del componente verde.
    getBlue()          r = p.getBlue()                  Devuelve la intensidad del componente azul.
    setRed()           p.setRed(100)                    Establezca la intensidad del componente rojo en 100.
    setGreen()         p.setGreen(45)                   Establezca la intensidad del componente verde en 45.
    setBlue()          p.setBlue(156)                   Establezca la intensidad del componente azul en 156.
    =================  ================            =========================================================

En el siguiente ejemplo, primero creamos un píxel con 45 unidades de rojo, 76 unidades de verde y 200 unidades de azul.
Luego imprimimos la cantidad actual de rojo, cambiamos la cantidad de rojo y, finalmente, establecemos la cantidad de azul para que sea
lo mismo que la cantidad actual de verde.

.. activecode::  ac14_7_1
    :nocodelens:

    import image

    p = image.Pixel(45, 76, 200)
    print(p.getRed())
    p.setRed(66)
    print(p.getRed())
    p.setBlue(p.getGreen())
    print(p.getGreen(), p.getBlue())

**Revisa tu entendimiento**

.. mchoice:: question14_7_1
   :answer_a: Rojo oscuro
   :answer_b: Rojo claro
   :answer_c: Verde oscuro
   :answer_d: Verde claro
   :correct: a
   :feedback_a: Como los tres valores están cerca de 0, el color será oscuro. Pero debido a que el valor rojo es más alto que los otros dos, el color aparecerá rojo.
   :feedback_b: Cuanto más cerca estén los valores de 0, más oscuro aparecerá el color.
   :feedback_c: El primer valor en RGB es el valor rojo. El segundo es el verde. Este color no tiene verde.
   :feedback_d: El primer valor en RGB es el valor rojo. El segundo es el verde. Este color no tiene verde.

   Si tiene un píxel cuyo valor RGB es (50, 0, 0), ¿de qué color será este píxel?

Objetos Image
^^^^^^^^^^^^^^

Para acceder a los píxeles en una imagen real, primero debemos crear un objeto ``Image``. Los objetos de imagen se pueden crear en dos
formas. Primero, se puede hacer un objeto Imagen a partir de los archivos que almacenan imágenes digitales. El objeto de imagen tiene un atributo
correspondiente al ancho, la altura y la colección de píxeles en la imagen.

También es posible crear un objeto de imagen que esté "vacío". Una ``EmptyImage`` tiene un ancho y una altura. Sin embargo,
colección de píxeles consta solo de píxeles "blancos".

Podemos pedirle a un objeto de imagen que devuelva su tamaño utilizando los métodos ``getWidth`` y ``getHeight``. También podemos obtener un píxel
desde una ubicación particular en la imagen usando ``getPixel`` y cambie el píxel en una ubicación particular usando ``setPixel``.


La clase de imagen se muestra a continuación. Tenga en cuenta que las dos primeras entradas muestran cómo crear objetos de imagen. Los parámetros son
diferente dependiendo de si está utilizando un archivo de imagen o está creando una imagen vacía.

   ===================  ===============================  ===============================================================
   Nombre del método    Ejemplo                          Explicación
   ===================  ===============================  ===============================================================
   Image(filename)      img = image.Image("cy.png")      Crea un objeto de imagen desde el archivo cy.png.
   EmptyImage()         img = image.EmptyImage(100,200)  Cree aun objeto de imagen que tenga todos los píxeles "blancos"
   getWidth()           w = img.getWidth()               Devuelve el ancho de la imagen en píxeles.
   getHeight()          h = img.getHeight()              Devuelve la altura de la imagen en píxeles.
   getPixel(col,row)    p = img.getPixel(35,86)          Devuelve el píxel en la columna 35, fila 86.
   setPixel(col,row,p)  img.setPixel(100,50,mp)          Establece el píxel en la columna 100, fila 50 para que sea mp.
   ===================  ===============================  ===============================================================

Considere la imagen que se muestra a continuación. Suponga que la imagen se almacena en un archivo llamado "luther.jpg". La línea 2 abre el archivo y
usa el contenido para crear un objeto de imagen al que se refiere ``img``. Una vez que tenemos un objeto de imagen, podemos usar los
métodos previamente mencionados para acceder a información sobre la imagen o para obtener un píxel específico y verificar su color básico intensidades



.. raw:: html

    <img src="../_static/LutherBellPic.jpg" id="luther.jpg" alt="image of Luther College bell picture">



.. activecode::  ac14_7_2
    :nocodelens:

    import image
    img = image.Image("luther.jpg")

    print(img.getWidth())
    print(img.getHeight())

    p = img.getPixel(45, 55)
    print(p.getRed(), p.getGreen(), p.getBlue())


Cuando ejecuta el programa, puede ver que la imagen tiene un ancho de 400 píxeles y una altura de 244 píxeles. También el
píxel en la columna 45, fila 55, tiene valores RGB de 165, 161 y 158. Pruebe algunas otras ubicaciones de píxel cambiando los argumentos ``getPixel`` y ejecutando nuevamente el programa.

**Revisa tu entendimiento**

.. mchoice:: question14_7_2
   :answer_a: 149 132 122
   :answer_b: 183 179 170
   :answer_c: 165 161 158
   :answer_d: 201 104 115
   :correct: b
   :feedback_a: Estos son los valores para el píxel en la fila 30, columna 100.  Obtenga los valores para la fila 100 y la columna 30 con p = img.getPixel(30, 100). (Tenga en cuenta que el primer argumento para getPixel es la columna, no la fila.)
   :feedback_b: Sí, los valores RGB son 183 179 170 en la fila 100 y la columna 30.
   :feedback_c: Estos son los valores del ejemplo original (fila 45, columna 55). Obtenga los valores para la fila 100 y la columna 30 con p = img.getPixel(30, 100).
   :feedback_d: Estos son simplemente valores inventados que pueden o no aparecer en la imagen. Obtenga los valores para la fila 100 y la columna 30 con p = img.getPixel(30, 100).

   Usando el ejemplo anterior de ActiveCode, seleccione la respuesta más cercana a los valores RGB del píxel en la fila 100, columna 30? Los valores pueden estar desactivados en uno o dos debido a las diferencias en los navegadores.


Procesamiento de imágenes e iteración anidada
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Procesamiento de imagen** se refiere a la capacidad de manipular los píxeles individuales en una imagen digital. Para procesar
todos los píxeles, necesitamos poder visitar sistemáticamente todas las filas y columnas de la imagen. La mejor manera
hacer esto es usar **iteración anidada**.

La iteración anidada simplemente significa que colocaremos una construcción de iteración dentro de otra. Llamaremos a estos dos
iteraciones la **iteración externa** y la **iteración interna**. Para ver cómo funciona esto, considere la siguiente iteración.

.. sourcecode:: python

    for i in range(5):
        print(i)

Hemos visto esto suficientes veces para saber que el valor de ``i`` será 0, luego 1, luego 2, y así sucesivamente hasta 4. El
La ``impresión`` se realizará una vez por cada pase. Sin embargo, el cuerpo del bucle puede contener cualquier declaración,
incluida otra iteración (otra declaración ``para``). Por ejemplo,

.. sourcecode:: python

    for i in range(5):
        for j in range(3):
            print(i, j)

La iteración ``para i`` es la `iteración externa` y la iteración ``para j`` es la `iteración interna`. Cada paso a través
la iteración externa dará como resultado el procesamiento completo de la iteración interna de principio a fin. Esto significa que
la salida de esta iteración anidada mostrará que para cada valor de ``i``, se producirán todos los valores de ``j``.

Aquí está el mismo ejemplo en activecode. Intentalo. Tenga en cuenta que el valor de ``i`` permanece igual mientras que el
valor de ``j`` cambios La iteración interna, en efecto, se mueve más rápido que la iteración externa.

.. activecode:: ac14_7_3

    for i in range(5):
        for j in range(3):
            print(i, j)

Otra forma de ver esto con más detalle es examinar el comportamiento con codelens. Recorre las iteraciones para ver el
flujo de control como ocurre con la iteración anidada. Nuevamente, para cada valor de ``i``, se producirán todos los valores de ``j``.Puede ver que la iteración interna se completa antes de pasar al siguiente paso de la iteración externa.
.. codelens:: clens14_7_1

    for i in range(5):
        for j in range(3):
            print(i, j)

Nuestro objetivo con el procesamiento de imágenes es visitar cada píxel. Usaremos una iteración para procesar cada `fila`. Dentro de eso
iteración, utilizaremos una iteración anidada para procesar cada `columna`. El resultado es una iteración anidada, similar a la
visto arriba, donde el bucle externo ``for`` procesa las filas, desde 0 hasta, pero sin incluir la altura de la imagen.
El bucle ``for`` interno procesará cada columna de una fila, nuevamente desde 0 hasta, pero sin incluir el ancho de la imagen.

El código resultante tendrá el siguiente aspecto. Ahora somos libres de hacer lo que queramos con cada píxel en la imagen.

.. sourcecode:: python

	for row in range(img.getHeight()):
	    for col in range(img.getWidth()):
	        # hacer algo con el píxel en la posición (col, fila)

Uno de los algoritmos de procesamiento de imágenes más fáciles creará lo que se conoce como una imagen **negativa**. Una imagen negativa simplemente
significa que cada píxel será el "opuesto" de lo que era originalmente. ¿Pero qué significa lo contrario?

En el modelo de color RGB, podemos considerar lo contrario del componente rojo como la diferencia entre el rojo original
y 255. Por ejemplo, si el componente rojo original era 50, entonces el valor rojo opuesto o negativo sería ``255-50``
o 205. En otras palabras, los píxeles con mucho rojo tendrán negativos con poco rojo y los píxeles con poco rojo tendrán
negativos con mucho. Hacemos lo mismo para el azul y el verde también.

El siguiente programa implementa este algoritmo utilizando la imagen anterior (luther.jpg). Ejecútelo para ver el negativo resultante
imagen. Tenga en cuenta que se está produciendo una gran cantidad de procesamiento y esto puede tardar unos segundos en completarse. Además, aquí
Hay otras dos imágenes que puede usar (cy.png y goldygopher.png).


.. raw:: html

    <img src="../_static/cy.png" id="cy.png"  alt="image of Cy the Cardinal, mascot of the Iowa State University">
    <h4 style="text-align: center;">cy.png</h4>

.. raw:: html

    <img src="../_static/goldygopher.png" id="goldygopher.png" alt="image of Goldy Gopher, mascot of the University of Minnesota-Twin Cities">
    <h4 style="text-align: center;">goldygopher.png</h4>


Cambie el nombre del archivo en la llamada ``image.Image()`` para ver cómo se ven estas imágenes como negativas. Además, tenga en cuenta que
hay una llamada al método ``exitonclick`` al final que cerrará la ventana cuando haga clic en ella. Esto permitira
"borrar la pantalla" antes de dibujar el siguiente negativo.


.. activecode::  ac14_7_4
    :nocodelens:

    import image

    img = image.Image("luther.jpg")
    win = image.ImageWin(img.getWidth(), img.getHeight())
    img.draw(win)
    img.setDelay(1,15)   # setDelay(0) turns off animation

    for row in range(img.getHeight()):
        for col in range(img.getWidth()):
            p = img.getPixel(col, row)

            newred = 255 - p.getRed()
            newgreen = 255 - p.getGreen()
            newblue = 255 - p.getBlue()

            newpixel = image.Pixel(newred, newgreen, newblue)

            img.setPixel(col, row, newpixel)

    img.draw(win)
    win.exitonclick()

Echemos un vistazo más de cerca al código. Después de importar el módulo de imagen, creamos un objeto de imagen llamado ``img`` que
representa una foto digital típica. Actualizaremos cada píxel en esta imagen de arriba a abajo, de izquierda a derecha, que usted
debería poder observar. Puede cambiar los valores en ``setDelay`` para hacer que el programa avance más rápido o más lento.

Las líneas 8 y 9 crean la iteración anidada que discutimos anteriormente. Esto nos permite procesar cada píxel en la imagen.
La línea 10 obtiene un píxel individual.

Las líneas 12-14 crean los valores de intensidad negativos al extraer la intensidad original del píxel y restarla
desde 255. Una vez que tenemos los valores ``newred``, ``newgreen`` y ``newblue``, podemos crear un nuevo píxel (Línea 15).

Finalmente, necesitamos reemplazar el viejo píxel con el nuevo píxel en nuestra imagen. Es importante colocar el nuevo píxel en el
misma ubicación que el píxel original del que vino en la foto digital.

Intente cambiar el programa anterior para que el bucle externo itere sobre las columnas y el bucle interno itere sobre el
filas Todavía creamos una imagen negativa, pero puede ver que los píxeles se actualizan en un orden muy diferente.

.. admonition:: Otra manipulación de píxeles

    Hay varios algoritmos de procesamiento de imágenes diferentes que siguen el mismo patrón que se muestra arriba. Es decir, tome el píxel original, extraiga las intensidades roja, verde y azul, y luego cree un nuevo píxel a partir de ellas. El nuevo píxel se inserta en una imagen vacía en la misma ubicación que el original.

    Por ejemplo, puede crear un píxel **escala de grises** promediando las intensidades roja, verde y azul y luego usando ese valor para todas las intensidades.

    A partir de la escala de grises, puede crear **blanco negro** estableciendo un umbral y seleccionando insertar un píxel blanco para un píxel negro en la imagen vacía.

    También puede hacer algunas operaciones aritméticas complejas y crear efectos interesantes, como
	`Tono sepia <http://en.wikipedia.org/wiki/Sepia_tone#Sepia_toning>`_

**Revisa tu entendimiento**

.. mchoice:: question14_7_3
   :answer_a: Salida a
   :answer_b: Salida b
   :answer_c: Salida c
   :answer_d: Salida d
   :correct: a
   :feedback_a: Comenzará con un valor de 0 y luego j iterará de 0 a 1. A continuación, será 1 y j iterará de 0 a 1. Finalmente, será 2 y j iterará de 0 a 1.
   :feedback_b: El bucle for interno controla el segundo dígito (j). El bucle for interno debe completarse antes de que avance el bucle for externo.
   :feedback_c: El bucle for interno controla el segundo dígito (j). Observe que el bucle for interno está sobre la lista [0, 1].
   :feedback_d: El for-loop externo se ejecuta 3 veces (0, 1, 2) y el for-loop interno se ejecuta dos veces cada vez que se ejecuta el for-loop externo, por lo que este código imprime exactamente 6 líneas.

   ¿Qué imprimirá el siguiente bucle for anidado? (Tenga en cuenta que si tiene problemas con esta pregunta, revise CodeLens 3).

   .. code-block:: python

      for i in range(3):
          for j in range(2):
              print(i, j)

   ::

      a.

      0	0
      0	1
      1	0
      1	1
      2	0
      2	1

      b.

      0   0
      1   0
      2   0
      0   1
      1   1
      2   1

      c.

      0   0
      0   1
      0   2
      1   0
      1   1
      1   2

      d.

      0   1
      0   1
      0   1


.. mchoice:: question14_7_4
   :answer_a: Se vería como una versión roja de la imagen de la campana
   :answer_b: Sería un rectángulo rojo sólido del mismo tamaño que la imagen original
   :answer_c: Se vería igual que la imagen original
   :answer_d: Se vería igual que la imagen negativa en el código de ejemplo
   :correct: a
   :feedback_a: Debido a que estamos eliminando los valores verde y azul, pero manteniendo la variación del rojo igual, obtendrá la misma imagen, pero parecerá que se ha bañado en rojo.
   :feedback_b: Debido a que el valor rojo varía de píxel a píxel, esto no se verá como un rectángulo rojo sólido. Para que se vea como un rectángulo rojo sólido, cada píxel debería tener exactamente el mismo valor rojo.
   :feedback_c: Si elimina los valores azul y verde de los píxeles, la imagen se verá diferente, aunque no parezca azul o verde en la imagen original (recuerde que otros colores están hechos de combinaciones de rojo, verde y azul).
   :feedback_d: Debido a que hemos cambiado el valor de los píxeles de lo que eran en el código del cuadro ActiveCode original, la imagen no será la misma.

   ¿Cómo se vería la imagen producida desde el cuadro 16 de ActiveCode si reemplazara las líneas?

   .. code-block:: python

      newred = 255 - p.getRed()
      newgreen = 255 - p.getGreen()
      newblue = 255 - p.getBlue()

   con las lineas:

   .. code-block:: python

      newred = p.getRed()
      newgreen = 0
      newblue = 0
