---
layout: post
title:  "Conexión remota a un servidor con Jupyter"
date:   2019-03-08 12:00:00 -0500
categories: python
---
Normalmente cuando tienes que trabajar en un servidor porque a veces nuestras máquinas no son tan potentes o porque nuestra máquina no tiene los datos y no queremos conectarnos a través de un programa de control remoto como TeamViewer o xRDP(porque son demasiado lentos si tu internet lo es), entonces aparece como solución, conectarse directamente al notebook Jupyter del servidor desde tu pc.

Yo he encontrado esto realmente útil y lo uso muy seguido, así que hoy los enseñaré cómo hacerlo (en este caso estoy usando Linux en mi computadora pero también lo he probado en Windows y el servidor si es Linux):

1. Primero abrimos la conexión SSH hacia nuestro servidor Linux, si estamos en Linux abrimos un nuevo terminal y si estamos en Windows podemos usar Putty.
{% highlight bash%}
local_user@local_host$ ssh usuario@servidor_remoto
remote_user@servidor_remoto$ jupyter notebook --no-browser --port=8889
{% endhighlight %}
Lo anterior corre un notebook Jupyter en el servidor remoto en el puerto 8889 sin abrir el navegador ya que la conexión que hagamos permitirá que abramos un notebook en el navegador local.



2. En un nuevo terminal local o en el CMD de Windows  se realiza una nueva conexión ssh configurando un forwarding de puertos.
{% highlight bash%}
local_user@local_host$ ssh -N -L localhost:8888:localhost:8889 remote_user@servidor_remoto
{% endhighlight %}
**-N:** se usa para indicar que no correrán comandos y se hará un forwarding de puertos.

**-L:** configuración de forwarding de puertos



3. Finalmente en nuestro navegador local realizamos la conexión, colocando lo siguiente en el lugar donde va la URL.
{% highlight bash%}
localhost:8888
{% endhighlight %}
Nos abre una ventana en jupyter que nos pide un token o una clave dependiendo como lo hayamos configurado, si no lo hemos configurado, copiamos el token que nos aparece en el terminal del primer paso y si queremos configurar una nueva clave solo bajamos la página y nos solicita una clave nueva.

Espero que les haya servido y cualquier duda, déjala en los comentarios.   
:D

[comment]: <> (ref:https://hsaghir.github.io/data_science/jupyter-notebook-on-a-remote-machine-linux/)

