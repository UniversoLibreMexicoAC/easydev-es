Cuadros de diálogo
==================

Crear diálogo
-------------

Crear cuadro de diálogo a partir de un archivo. Puedes diseñarlo en el IDE,
exportarlo y crearlo desde el archivo exportardo.

.. image:: images/img010.png
    :width: 400px
    :align: center

.. code-block:: vbnet

    Sub CreateDialog
        util = createUnoService("org.universolibre.EasyDev")

        path = "/home/USER/dlg_test.xdl"
        dlg = util.createDialog(path)
        dlg.execute()
        dlg.dispose()
    End Sub



Etiqueta con hipervínculo
-------------------------

Automáticamente se agregar el evento **ratón encima**.

.. image:: images/img011.png
    :width: 350px
    :align: center

.. code-block:: vbnet

    path = "/home/USER/dlg_test.xdl"
    dlg = util.createDialog(path)

    properties = Array( _
        Array("Name", "link_home"), _
        Array("PositionX", 100), _
        Array("PositionY", 10), _
        Array("URL", "http://universolibre.org"), _
        Array("Label", "http://universolibre.org"), _
    )
    util.createControl(dlg, "FixedHyperlink", properties)
    dlg.execute()
    dlg.dispose()


Mapa de ruta
------------

Agregar un menú de opciones, automáticamente se agregar el evento **item cambiado**
que actualiza la propiedad Paso(**Step**) del cuadro de diálogo.

.. image:: images/img012.png
    :width: 200px
    :align: center

.. code-block:: vbnet

    path = "/home/USER/dlg_test.xdl"
    dlg = util.createDialog(path)

    options = Array("Init", "Values", "Config", "Other")
    properties = Array( _
        Array("Name", "roadmap"), _
        Array("Width", 50), _
        Array("Height", 150), _
        Array("Options", options), _
    )
    util.createControl(dlg, "Roadmap", properties)
    dlg.execute()
    dlg.dispose()


Rejilla
-------

Crear una rejilla y establecer su contenido desde un array. Automáticamente se
detectan las columnas con valores y se formatean.

.. image:: images/img013.png
    :width: 300px
    :align: center

.. code-block:: vbnet

    c1 = Array( _
        Array("Title", "State"), _
        Array("HorizontalAlign", 0), _
    )
    c2 = Array( _
        Array("Title", "People"), _
        Array("HorizontalAlign", 2), _
        Array("Identifier", True), _
    )
    columns = Array(c1, c2)
    properties = Array( _
        Array("Name", "grid"), _
        Array("PositionX", 100), _
        Array("PositionY", 50), _
        Array("Step", 4), _
        Array("Columns", columns), _
    )
    grid = util.createControl(dlg, "Grid", properties)

    data = Array( _
        Array("Uno", 2222), _
        Array("Tres", 44444), _
        Array("Cinco", 666666), _
        Array("Siete", 666666), _
    )
    col_format = Array()
    util.setGridData(grid, data, col_format)

    dlg.execute()
    dlg.dispose()

Agregar datos de un rango de celdas.

.. code-block:: vbnet

    data = ThisComponent.getCurrentSelection().getDataarray()
    col_format = Array()
    util.setGridData(grid, data, col_format)

Cambiar el formato predeterminado de las columnas con valores.

.. code-block:: vbnet

    data = ThisComponent.getCurrentSelection().getDataarray()

    'Default format
    util.numfmt = "$ {0:,.2f}"

    col_format = Array()
    util.setGridData(grid, data, col_format)

O puedes establecer el formato para cada columna.

.. code-block:: vbnet

    data = ThisComponent.getCurrentSelection().getDataarray()
    col_format = Array("{}", "$ {0:,.2f}")
    util.setGridData(grid, data, col_format)

Y devolver los datos de la rejilla.

.. code-block:: vbnet

    data = util.getGridData(grid, Array())
    util.msgbox(data)
