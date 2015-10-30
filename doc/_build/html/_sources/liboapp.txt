Documentos
==========

Nuevo
-----

Más información: `Component Loader`_

.. code-block:: vbnet

    Sub NewDoc()
        'Create new doc
        util = createUnoService("org.universolibre.EasyDev")

        'Default Calc
        doc = util.newDoc("")

    End Sub

Otros posibles valores: swriter, simpress, sdraw, smath

.. code-block:: vbnet

        doc = util.newDoc("sdraw")

Para documentos de Base.

.. code-block:: vbnet

    path_db = "/home/USER/dbtest.odb"
    db = util.newDB(path_db)


Obtener documento
-----------------

Actual

.. IMPORTANT::
   El documento actual puede ser el IDE Basic

.. code-block:: vbnet

    doc1 = util.getDoc("")
    MsgBox doc1.Title

Obtener documento por título, si no se encuentra, regresa Vacio

.. code-block:: vbnet

    doc2 = util.getDoc("Name_doc.odt")
    util.msgbox(doc2)


Tipo de documento
-----------------

Valores de retorno: calc, writer, impress, draw, math, base, ide

.. code-block:: vbnet

    doc1 = util.newDoc("sdraw")
    MsgBox util.getTypeDoc(doc1)

    doc2 = util.newDoc("swriter")
    MsgBox util.getTypeDoc(doc2)


Obtener documentos
------------------

Obtener todos los documentos abiertos.

.. code-block:: vbnet

    docs = util.getDocs()
    MsgBox util.format("{} Open documents", util.len(docs))


Abrir
-----

Más información y opciones:

    * `Component Loader`_
    * `Media Descriptor <http://api.libreoffice.org/docs/idl/ref/servicecom_1_1sun_1_1star_1_1document_1_1MediaDescriptor.html>`_

Abrir documento por ruta

.. code-block:: vbnet

    Dim options1(0) As New com.sun.star.beans.NamedValue
    util = createUnoService("org.universolibre.EasyDev")

    path = "/home/USER/Plantilla.ods"
    options = Array()
    doc = util.openDoc(path, options)

Abrir como una plantilla.

.. code-block:: vbnet

    options1(0).Name = "AsTemplate"
    options1(0).Value = True
    path = "/home/USER/Plantilla.ods"
    doc = util.openDoc(path, options1)

Abrir oculto.

.. code-block:: vbnet

    options1(0).Name = "Hidden"
    options1(0).Value = True
    path = "/home/USER/Plantilla.ods"
    doc = util.openDoc(path, options1)
    MsgBox "Close doc"
    doc.dispose()


Activar
-------

Enviar el foco a un documento.

.. code-block:: vbnet

    doc1 = util.newDoc("")
    doc2 = util.newDoc("swriter")
    wait(1000)
    util.setFocus(doc1)


Barra de estado
---------------

Establecer el texto y mostrar una barra de progreso.

.. code-block:: vbnet

    'Get current doc
    doc = util.getDoc("")
    'Get status bar
    sb = util.getStatusBar(doc)

    'Init text and up limit
    sb.start( "Row ", 10 )
    For co1 = 1 To 10
        'Set value
        sb.setValue( co1 )
        Wait 1000
    Next
    'Is import free status bar
    sb.end()


Exportar a PDF
--------------

Todas las opciones en: `PDF Export <http://wiki.services.openoffice.org/wiki/API/Tutorials/PDF_export>`_ in wiki.

Si la exportación es correcta, regresa la ruta del PDF

Exportar el documento actual en el mismo directorio y mismo nombre del documento.

.. code-block:: vbnet

    doc = util.getDoc("")
    path = util.exportPDF(doc, "", Array())
    MsgBox util.format("PDF export in: {}", path)

Exportar en otro directorio con el mismo nombre del documento.

.. code-block:: vbnet

    path_save = "/home/USER/OTHER_FOLDER"
    path_pdf = util.exportPDF(doc, path_save, Array())

Exportar en otro directorio y otro nombre de archivo.

.. code-block:: vbnet

    path_save = "/home/USER/OTHER_FOLDER/NAME.pdf"
    path_pdf = util.exportPDF(doc, path_save, Array())

Exportar con opciones.

.. code-block:: vbnet

    Dim options(0) As New com.sun.star.beans.NamedValue

    doc = util.getDoc("")
    options(0).Name = "PageRange"
    options(0).Value = "2"
    path = util.exportPDF(doc, "", options)
    MsgBox util.format("PDF export in: {}", path)


.. _Component Loader: http://www.openoffice.org/api/docs/common/ref/com/sun/star/frame/XComponentLoader.html