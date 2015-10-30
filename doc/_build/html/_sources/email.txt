Enviando correo
===============

Enviar un correo y esperar la respuesta
---------------------------------------

.. code-block:: vbnet

    Sub SendMail()
        util = createUnoService("org.universolibre.EasyDev")

        server = createUnoStruct("org.universolibre.EasyDev.SmtpServer")
        message = createUnoStruct("org.universolibre.EasyDev.EmailMessage")

        server.Name = "smtp.gmail.com"
        server.User = "hipatia.blades@gmail.com"
        server.Password = "supersecret"
        server.Ssl = True

        temp = "Dear Madame: $name\n\nBest regards from $country"
        data = Array( _
            Array("name", "Teresa"), _
            Array("country", "México"), _
        )
        body = util.render(temp, data)

        message.To = "public@mauriciobaeza.net"
        message.Subject = "Email test"
        message.Body = body

        'Send mail and wait response
        result = util.sendMail(server, message)
        If result Then
            MsgBox "Correo enviado"
        Else
            MsgBox "Error al enviar el correo"
        End If
    End Sub


Enviar correo y no esperar respuesta
------------------------------------

.. code-block:: vbnet

    Sub SendMailNoWait()
        util = createUnoService("org.universolibre.EasyDev")

        server = createUnoStruct("org.universolibre.EasyDev.SmtpServer")
        message = createUnoStruct("org.universolibre.EasyDev.EmailMessage")

        server.Name = "smtp.gmail.com"
        server.User = "hipatia.blades@gmail.com"
        server.Password = "supersecret"
        server.Ssl = True
        server.Thread = True    'Send in other thread

        temp = "Dear Madame: $name\n\nBest regards from $country"
        data = Array( _
            Array("name", "Teresa"), _
            Array("country", "México"), _
        )
        body = util.render(temp, data)

        message.To = "public@mauriciobaeza.net"
        message.Subject = "Email test"
        message.Body = body

        'Enviar correo y no esperar respuesta
        util.sendMail(server, message)
        MsgBox "Send mail"

    End Sub


Enviar correo con copia (CC) y copia oculta (BCC)
-------------------------------------------------

.. code-block:: vbnet

    Sub SendMailNoWaitAndCCBCC()
        util = createUnoService("org.universolibre.EasyDev")

        server = createUnoStruct("org.universolibre.EasyDev.SmtpServer")
        message = createUnoStruct("org.universolibre.EasyDev.EmailMessage")

        server.Name = "smtp.gmail.com"
        server.User = "hipatia.blades@gmail.com"
        server.Password = "supersecret"
        server.Ssl = True
        server.Thread = True    'Send in other thread

        temp = "Dear Madame: $name\n\nBest regards from $country"
        data = Array( _
            Array("name", "Teresa"), _
            Array("country", "México"), _
        )
        body = util.render(temp, data)

        message.To = "public@mauriciobaeza.net"
        message.Subject = "Email test"
        message.Body = body
        message.Cc = "other1@correo.net,other2@correo.net"
        message.Bcc = "other3@correo.net,other4@correo.net"

        'Enviar correo y no esperar respuesta
        util.sendMail(server, message)
        MsgBox "Send mail"

    End Sub


Enviar correo con archivos anexos
---------------------------------

.. code-block:: vbnet

    Sub SendMailWithAttachment()
        util = createUnoService("org.universolibre.EasyDev")

        server = createUnoStruct("org.universolibre.EasyDev.SmtpServer")
        message = createUnoStruct("org.universolibre.EasyDev.EmailMessage")

        server.Name = "smtp.gmail.com"
        server.User = "hipatia.blades@gmail.com"
        server.Password = "supersecret"
        server.Ssl = True
        server.Thread = True    'Send in other thread

        temp = "Dear Madame: $name\n\nBest regards from $country"
        data = Array( _
            Array("name", "Teresa"), _
            Array("country", "México"), _
        )
        body = util.render(temp, data)

        files = Array("/home/USER/Documents/pruebas.cer", "/home/USER/Documents/pruebas.key")

        message.To = "public@mauriciobaeza.net"
        message.Subject = "Email test"
        message.Body = body
        message.Files = files

        'Enviar correo y no esperar respuesta
        util.sendMail(server, message)
        MsgBox "Send mail"

    End Sub


Enviar correo y guardar mensaje
-------------------------------

Si usas una ruta de Thunderbird, puedes ver el mensaje en una carpeta dentro
de Thunderbird

.. CAUTION::
   Siempre usa una carpeta separada dentro del árbol de carpetas de Thunderbird!

.. code-block:: vbnet

    Sub SendMailAndSave()
        util = createUnoService("org.universolibre.EasyDev")

        server = createUnoStruct("org.universolibre.EasyDev.SmtpServer")
        message = createUnoStruct("org.universolibre.EasyDev.EmailMessage")

        server.Name = "smtp.gmail.com"
        server.User = "hipatia.blades@gmail.com"
        server.Password = "supersecret"
        server.Ssl = True
        server.Thread = True    'Send in other thread
        server.PathSave = "/home/USER/.thunderbird/cwfln0bi.default/Mail/Local Folders/Sent"

        temp = "Dear Madame: $name\n\nBest regards from $country"
        data = Array( _
            Array("name", "Teresa"), _
            Array("country", "México"), _
        )
        body = util.render(temp, data)

        files = Array("/home/USER/Documents/pruebas.cer")

        message.To = "public@mauriciobaeza.net"
        message.Subject = "Email test"
        message.Body = body
        message.Files = files
        message.Save = True

        'Enviar correo y no esperar respuesta
        util.sendMail(server, message)
        MsgBox "Send mail"

    End Sub

.. image:: images/img008.png
    :width: 800px
    :align: center
