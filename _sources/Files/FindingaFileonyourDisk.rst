..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: files-2-
   :start: 1

Encontrar un archivo en su sistema de archivos
==============================================

En los ejemplos que hemos proporcionado, y en el sistema de archivos simulados que hemos creado para este libro de texto en línea, todos los archivos se encuentran en un solo directorio, y es el mismo directorio donde se almacena el programa Python. Por lo tanto, podemos simplemente escribir ``open('myfile.txt','r')``.

Si ha instalado Python en su computadora local y está intentando que las operaciones de lectura y escritura de archivos funcionen, es posible que necesite comprender algo más. Los sistemas operativos de computadora (como Windows y Mac OS) organizan los archivos en una jerarquía de carpetas, con algunas carpetas que contienen otras carpetas.

.. image:: Figures/ExampleFileHierarchy.png
  :align: center


Si su archivo y su programa Python están en el mismo directorio, simplemente puede usar
el nombre del archivo. Por ejemplo, con la jerarquía de archivos en el diagrama, el archivo `myPythonProgram.py` podría contener el código``open('data1.txt','r')``.

Sin embargo, si su archivo y su programa Python están en directorios diferentes, entonces debe especificar una **ruta**. Puede pensar en el nombre del archivo como el nombre corto y la ruta como el nombre completo. Por lo general, especificará una *ruta de archivo relativa*, que dice dónde encontrar el archivo para abrir, en relación con el directorio desde donde se ejecuta el código. Por ejemplo, el archivo `myPythonProgram.py` podría contener el código ``open('../myData/data2.txt','r')``. El ``../`` significa subir un nivel en la estructura del directorio, a la carpeta que lo contiene (allProjects); ``myData/`` dice descender a la subcarpeta myData.

También hay una opción para usar una *ruta de archivo absoluta*. Por ejemplo, suponga que la estructura de archivos en la figura se almacena en una computadora en el directorio de inicio del usuario, ``/Users/joebob01/myFiles``. Luego, el código en cualquier programa de Python que se ejecute desde cualquier carpeta de archivos podría abrir data2.txt a través de ``open('/Users/joebob01/myFiles/allProjects/myData/data2.txt','r')``. Puede decir una ruta de archivo absoluta porque comienza con un `/`.
Si alguna vez mueve sus programas y datos a otra computadora (por ejemplo, para compartirlos con otra persona), será mucho más conveniente si usa rutas de archivos relativas en lugar de absolutas. De esa manera, si conserva la estructura de carpetas al mover todo, no necesitará cambiar su código. Si usa rutas absolutas, entonces la persona con la que comparte probablemente no tenga el mismo nombre de directorio de inicio, `/Users/joebob01/`. Tenga en cuenta que los nombres de ruta de Python siguen las convenciones de UNIX  (Mac OS es una variante de UNIX), en lugar de los nombres de ruta de archivo de Windows que usan `:` y '\'. El intérprete de python se traducirá en nombres de ruta de Windows cuando se ejecute en una máquina con Windows; debería poder compartir su programa Python entre una máquina Windows y un MAC sin tener que volver a escribir los comandos de abrir archivo.

.. note::

   Por razones de seguridad, nuestro código que se ejecuta en su navegador no lee ni escribe archivos en el archivo del sistema de su
   computadora. Más tarde, cuando ejecutas python de forma nativa en tu propia computadora, podrás leer realmente archivos, usando
   nombres de ruta como se sugirió anteriormente. Para comenzar, lo hemos falsificado al proporcionar algunos archivos que puede leer
   *como si* estuvieran en su disco duro. En este capítulo, simulamos la existencia de un archivo de texto; no puede abrir ningún otro archivo desde su computadora local desde el código del libro de texto que se ejecuta en su navegador.

**Revisa tu entendimiento**

.. mchoice:: question9_2_1
   :answer_a: open("YearlyProjections.csv", "r")
   :answer_b: open("../CompanyData/YearlyProjections.csv", "r")
   :answer_c: open("CompanyData/YearlyProjections.csv", "r")
   :answer_d: open("Project/CompanyData/YearlyProjections.csv", "r")
   :answer_e: open("../YearlyProjections.csv", "r")
   :correct: c
   :feedback_a: Esto intentaría abrir un archivo dentro del Proyecto (pero no es donde está el archivo.)
   :feedback_b: Esto iría al directorio padre de Project y buscaría un subdirectorio llamado CompanyData. Pero CompanyData está dentro de Project, por lo que no se encontrará.
   :feedback_c: Sí, así es como puedes acceder al archivo.
   :feedback_d: Esto intentaría encontrar un proyecto de subdirectorio del directorio actual llamado Project.
   :feedback_e: Recuerde que '..' lo llevará un nivel al directorio principal. Esto intentaría abrir un archivo csv en el directorio padre de Project (pero no es donde está el archivo.)
   :practice: T 

   Digamos que está en un directorio llamado Project. En él, tienes un archivo con tu código de Python. Le gustaría leer los datos de un archivo llamado "YearlyProjections.csv" que se encuentra en una carpeta llamada CompanyData, que se encuentra dentro de Project. ¿Cuál es la mejor manera de abrir el archivo en su programa de Python?

.. mchoice:: question9_2_2
   :multiple_answers:
   :answer_a: "Stacy/Applications/README.txt"
   :answer_b: "/Users/Raquel/Documents/graduation_plans.doc"
   :answer_c: "/private/tmp/swtag.txt"
   :answer_d: "ScienceData/ProjectFive/experiment_data.csv"
   :correct: a,d
   :feedback_a: Sí, esta es una ruta de archivo relativa. Se nota por la falta de "/" al comienzo del camino.
   :feedback_b: Esta es una ruta de archivo absoluta. Todas las rutas de archivos absolutas comienzan con "/".
   :feedback_c: Esta es una ruta de archivo absoluta. ¡No todas las rutas de archivos absolutas contienen "User"! En su lugar, verifique si la ruta comienza con "/".
   :feedback_d: Sí, esta es una ruta de archivo relativa. Se nota por la falta de "/" al comienzo del camino.
   :practice: T 

   ¿Cuál de las siguientes rutas son rutas de archivos relativas?
