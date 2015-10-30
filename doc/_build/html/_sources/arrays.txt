Matrices
========

Agregar
-------

.. code-block:: vbnet

    a = Array("Nikole","Scarlett","Monica","Naomi","Marion")
    a = util.append(a, "Sofia")
    util.msgbox( a )

Borrar
------

.. code-block:: vbnet

    a = util.delete(a, "Nikole")
    util.msgbox( a )

Extender
--------

.. code-block:: vbnet

    a = Array("Nikole","Scarlett","Monica","Naomi","Marion")
    a2 = Array("Sofia", "Anita")
    a = util.extend(a, a2)
    util.msgbox( a )

Multiplicar
-----------

.. code-block:: vbnet

    a = Array("Nikole","Scarlett","Monica","Naomi","Marion")
    a = util.multi(a, 2)
    util.msgbox( a )

Valores únicos
--------------

.. code-block:: vbnet

    a = Array(1,2,"Two",3,3,3,4,4,4,4,5,5,5,5,5,"Uno","Uno")
    a = util.unique(a)
    util.msgbox( a )

Reversa
-------

.. code-block:: vbnet

    a = Array("Nikole","Scarlett","Monica","Naomi","Marion")
    a = util.reverse(a)
    util.msgbox( a )

Insertar
--------

Insertar un elemento en una posición.

.. code-block:: vbnet

    a = Array("Nikole","Scarlett","Monica","Naomi","Marion")
    a = util.insert(a, 2, "Mary")
    util.msgbox( a )

Remover
-------

Remover un elemento en una posición y regresar el elemento y la matriz

.. code-block:: vbnet

    a = Array(1,2,"Two",3,3,3,4,4,4,4,5,5,5,5,5,"Uno","Uno")
    data = util.pop(a, 2)
    util.msgbox( data(0) )  'Array without element in pos
    util.msgbox( data(1) )  'Element removed

Remover el primer elemento encontrado.

.. code-block:: vbnet

    a = Array(1,2,2,3,3,3,4,4,4,4,5,5,5,5,5,"Uno","Uno")
    util.msgbox( util.remove(a, 5, False) )

Remover todos los elementos encontrados.

.. code-block:: vbnet

    util.msgbox( util.remove(a, 5, True) )

Largo
-----

.. code-block:: vbnet

    a = Array(1,2,2,3,3,3,4,4,4,4,5,5,5,5,5,"Uno","Uno")
    util.msgbox( util.len(a) )

Contar
------

.. code-block:: vbnet

    a = Array(1,2,2,3,3,3,4,4,4,4,5,5,5,5,5,"Uno","Uno")
    util.msgbox( util.count(a, 3) )
    util.msgbox( util.count(a, 5) )
    util.msgbox( util.count(a, "Uno") )

Índice
------

.. code-block:: vbnet

    a = Array("Nikole","Scarlett","Monica","Naomi","Marion")
    util.msgbox( util.index(a, "Naomi") )
    util.msgbox( util.index(a, "Monica") )

Máximo, Mínimo y Promedio
-------------------------

.. code-block:: vbnet

    a = Array(1,2,3,4,5,6,7,8,9,10)
    util.msgbox( util.max(a) )
    util.msgbox( util.min(a) )
    util.msgbox( util.average(a) )

Suma
----

.. code-block:: vbnet

    a = Array(1,2,3,4,5,6,7,8,9,10)
    util.msgbox( util.sum(a) )

Solo se suman valores, el primer elemento es una candena.

.. code-block:: vbnet

    a = Array("10", 1,2,3,4,5,6,7,8,9,10, "One", "Two")
    util.msgbox( util.sum(a) )

Existe
------

Si un valor existe en la matriz.

.. code-block:: vbnet

    a = Array(1,2,3,4,5,"One","Seven",9,10)
    util.msgbox( util.exists(a, "One") )
    util.msgbox( util.exists(a, "Two") )

Igual
-----

Si una matriz es igual a una segunda.

.. code-block:: vbnet

    a1 = Array(1,2,3) : a2 = Array(1,2,3)
    util.msgbox( util.equal(a1, a2) )

    a1 = Array(1,"Dos",3) : a2 = Array(1,2,"Tres")
    util.msgbox( util.equal(a1, a2) )


Rebanadas
---------

Copiar

.. code-block:: vbnet

    a = Array("Nikole","Scarlett","Monica","Naomi","Marion","Sofia","Anita")
    a2 = util.slice(a, "[:]")
    util.msgbox( a2 )

Primeros dos (n) elementos.

.. code-block:: vbnet

    a2 = util.slice(a, "[:2]")
    util.msgbox( a2 )

Ultimos dos (n) elementos.

.. code-block:: vbnet

    a2 = util.slice(a, "[-2:]")
    util.msgbox( a2 )

Rango

.. code-block:: vbnet

    a2 = util.slice(a, "[2:-2]")
    util.msgbox( a2 )

    a2 = util.slice(a, "[::2]")
    util.msgbox( a2 )

    a2 = util.slice(a, "[1::2]")
    util.msgbox( a2 )

Reversa

.. code-block:: vbnet

    a2 = util.slice(a, "[::-1]")
    util.msgbox( a2 )


Ordenar
-------

Ordenar una matriz unidimensional.

.. code-block:: vbnet

    a = Array("Nikole","Scarlett","Monica","Naomi","Marion","Sofia","Anita")
    a = util.sorted(a, 0)
    util.msgbox( a )

Ordenar una matriz multidimensional.

.. code-block:: vbnet

    a = Array( _
        Array(1, 1, 3, "a", 56), _
        Array(1, 2, 3, "z", 43), _
        Array(1, 3, 3, "g", 78), _
        Array(1, 4, 3, "e", 32), _
        Array(1, 5, 3, "M", 89) _
    )
    a = util.sorted(a, 0)
    util.msgbox( a )
    a = util.sorted(a, 1)
    util.msgbox( a )
    a = util.sorted(a, 2)
    util.msgbox( a )
    a = util.sorted(a, 3)
    util.msgbox( a )
    a = util.sorted(a, 4)
    util.msgbox( a )

Regresar una columna de una matriz multidimensional

.. code-block:: vbnet

    util.msgbox(util.getColumn(a, 1))


Operaciones
-----------

.. code-block:: vbnet

    Sub ArraysOperations()
        util = createUnoService("org.universolibre.EasyDev")

        a1 = Array(1,2,3,4,5) : a2 = Array(3,4,5,6,7,8)
        a = util.union(a1, a2)
        util.msgbox( a )

        a = util.intersection(a1, a2)
        util.msgbox( a )

        a = util.difference(a1, a2)
        util.msgbox( a )

        a = util.symmetricDifference(a1, a2)
        util.msgbox( a )

    End Sub

