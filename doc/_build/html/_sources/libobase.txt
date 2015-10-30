Bases de datos
==============

ODBC
----

Conectar a una base de datos ODBC

.. code-block:: vbnet

    Sub ConexionODBC()

        util = createUnoService("org.universolibre.EasyDev")

        odbc = "ConSQL"
        user = "sa"
        passw = "letmein"

        con = util.conODBC(odbc, user, passw)

        util.msgbox(con)

    End Sub
