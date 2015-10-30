Calc
===============

Celdas
------

Regresar la celda activa, siempre se deuelve una sola celda.

.. code-block:: vbnet

    Sub getCellDoc()
        util = createUnoService("org.universolibre.EasyDev")
        address = createUnoStruct("org.universolibre.EasyDev.CellRangeAddress")

        address.Current = True
        cell = util.getCell(address)
        msg = util.format("{} {}", Array(cell.ImplementationName, cell.AbsoluteName))
        util.msgbox(msg)
    End Sub


Regresar la celda activa, buscando el documento por título, el documento debe estar previamente abierto.

.. code-block:: vbnet

        address.Doc = "test.ods"    'Title doc
        address.Current = True
        cell = util.getCell(address)
        msg = util.format("{} {}", Array(cell.ImplementationName, cell.AbsoluteName))
        util.msgbox(msg)

Regresar la celda activa de un documento

.. code-block:: vbnet

        doc = util.getDoc("")
        address.Doc = doc
        address.Current = True
        cell = util.getCell(address)
        msg = util.format("{} {}", Array(cell.ImplementationName, cell.AbsoluteName))
        util.msgbox(msg)

Regresar una celda de un documento, de una hoja y celda por nombre.

.. code-block:: vbnet

    doc = util.getDoc("")
    address.Doc = doc
    address.Sheet = "Sheet2"
    address.Name = "B5"
    cell = util.getCell(address)
    msg = util.format("{} {}", Array(cell.ImplementationName, cell.AbsoluteName))
    util.msgbox(msg)

Regresar una celda de un documento, de una hoja por nombre y la celda por posición de columna y fila.

.. code-block:: vbnet

    doc = util.getDoc("")
    address.Doc = doc
    address.Sheet = "Sheet2"
    address.Name = ""
    address.Col = 1
    address.Row = 4
    cell = util.getCell(address)
    msg = util.format("{} {}", Array(cell.ImplementationName, cell.AbsoluteName))
    util.msgbox(msg)

Regresa una celda de una instancua de una hoja, el parametro documento es omitido.

.. code-block:: vbnet

    sheet = doc.getCurrentController().getActiveSheet()
    address.Sheet = sheet
    address.Name = "D5"
    cell = util.getCell(address)
    msg = util.format("{} {}", Array(cell.ImplementationName, cell.AbsoluteName))
    util.msgbox(msg)


Rangos
------

Regresar el rango activo.

.. code-block:: vbnet

    Sub getRangeDoc()
        util = createUnoService("org.universolibre.EasyDev")
        address = createUnoStruct("org.universolibre.EasyDev.CellRangeAddress")

        address.Current = True
        range = util.getRange(address)
        msg = util.format("{} {}", Array(range.ImplementationName, range.AbsoluteName))
        util.msgbox(msg)
    End Sub

Regresar el rango activo de un documento buscado por título, el documento debe estar previamente abierto.

.. code-block:: vbnet

    address.Doc = "test.ods"    'Title doc
    address.Current = True
    range = util.getRange(address)
    msg = util.format("{} {}", Array(range.ImplementationName, range.AbsoluteName))
    util.msgbox(msg)

Regresar el rango activo de uns instancia de un documento.

.. code-block:: vbnet

        doc = util.getDoc("")
        address.Doc = doc
        address.Current = True
        range = util.getRange(address)
        msg = util.format("{} {}", Array(range.ImplementationName, range.AbsoluteName))
        util.msgbox(msg)

Regresar el rango de una instancia de un documento, de una hoja y rango por nombre.

.. code-block:: vbnet

    doc = util.getDoc("")
    address.Doc = doc
    address.Sheet = "Sheet2"
    address.Name = "B5:C10"
    range = util.getRange(address)
    msg = util.format("{} {}", Array(range.ImplementationName, range.AbsoluteName))
    util.msgbox(msg)

Regresar el rango de una instancia de un documento, de una hoja por nombre y del
rango por posición.

.. code-block:: vbnet

    address.Sheet = "Sheet2"
    address.Name = ""
    address.Col = 1
    address.Row = 4
    address.EndCol = 3
    address.EndRow = 9
    range = util.getRange(address)
    msg = util.format("{} {}", Array(range.ImplementationName, range.AbsoluteName))
    util.msgbox(msg)

Regresar el rango de uns instancia de una hoja, el argumento documento es omitido.

.. code-block:: vbnet

    sheet = doc.getCurrentController().getActiveSheet()
    address.Sheet = sheet
    address.Name = "D5:E10"
    range = util.getRange(address)
    msg = util.format("{} {}", Array(range.ImplementationName, range.AbsoluteName))
    util.msgbox(msg)


Seleccionar un rango
--------------------

.. code-block:: vbnet

    Sub SelectRange()
        util = createUnoService("org.universolibre.EasyDev")
        address = createUnoStruct("org.universolibre.EasyDev.CellRangeAddress")

        doc = util.getDoc("")
        address.Doc = doc
        address.Sheet = "Sheet2"
        address.Name = "B5:C10"
        range = util.getRange(address)

        'Select
        util.selectRange(doc, range)

    End Sub


Región actual
-------------

.. code-block:: vbnet

    Sub getCurrentRegion()

        util = createUnoService("org.universolibre.EasyDev")
        address = createUnoStruct("org.universolibre.EasyDev.CellRangeAddress")

        address.Current = True
        cell = util.getCell(address)
        msg = util.format("{} {}", Array(cell.ImplementationName, cell.AbsoluteName))
        util.msgbox(msg)

    End Sub

Solo es necesario pasar una celda que este dentro de la región actual. Se obtiene
un objeto **cursor**.

.. code-block:: vbnet

    cursor = util.getCurrentRegion(cell, True)
    msg = util.format("{} {}", Array(cursor.ImplementationName, cursor.AbsoluteName))
    util.msgbox(msg)

Se devuelve un objeto rango (**range**).

.. code-block:: vbnet

    range = util.getCurrentRegion(cell, False)
    msg = util.format("{} {}", Array(range.ImplementationName, range.AbsoluteName))
    util.msgbox(msg)


Ultima fila
-----------

Devolver la ultima fila dentro dentro de la región actual.

.. code-block:: vbnet

    Sub getLastRow()
        util = createUnoService("org.universolibre.EasyDev")
        address = createUnoStruct("org.universolibre.EasyDev.CellRangeAddress")

        address.Current = True
        cell = util.getCell(address)
        row = util.getLastRow(cell)
        util.msgbox(row)
    End Sub


Siguiente valor
---------------

En los valores de un rango de celdas, devolver el siguiente valor en la columna
pasada, por ejemplo 0 (A), 1 (B), etc.

.. code-block:: vbnet

    Sub getNextID()
        util = createUnoService("org.universolibre.EasyDev")
        address = createUnoStruct("org.universolibre.EasyDev.CellRangeAddress")

        address.Current = True
        cell = util.getCell(address)
        value = util.getNextID(cell, 0)
        util.msgbox(value)
    End Sub

.. image:: images/img009.png
    :width: 400px
    :align: center


Valor de celda
--------------

Detección automática del tipo de contenido: cadenas (string), valores (value) o formulas.

.. code-block:: vbnet

    Sub CellValue()
        util = createUnoService("org.universolibre.EasyDev")
        address = createUnoStruct("org.universolibre.EasyDev.CellRangeAddress")

        address.Current = True
        cell = util.getCell(address)

        value = "String"
        util.setValue(cell, value)
        value = util.getValue(cell)
        util.msgbox(value)

        value = 12345
        util.setValue(cell, value)
        value = util.getValue(cell)
        util.msgbox(value)

        value = "=SUM(A1:C1)"
        util.setValue(cell, value)
        value = util.getValue(cell)
        util.msgbox(value)

    End Sub
