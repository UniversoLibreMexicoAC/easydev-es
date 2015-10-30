Writer
======

Parrafos
--------

Obtener todos los parrafos de un documento, incluyendo los vacíos.

.. code-block:: vbnet

    Sub GetParagraps()
        util = createUnoService("org.universolibre.EasyDev")

        'Get current doc
        doc = util.getDoc("")

        'Get all paragraphs
        paragraphs = util.getParagraphs(doc, True)
        util.msgbox(util.len(paragraphs))

    End Sub

Obtener todos los parrafos de un documento, excluyendo los vacíos.

.. code-block:: vbnet

    paragraphs = util.getParagraphs(doc, False)
    util.msgbox(util.len(paragraphs))


