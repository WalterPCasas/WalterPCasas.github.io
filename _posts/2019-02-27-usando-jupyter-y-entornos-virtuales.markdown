---
layout: post
title:  "Usando Jupyter en entornos virtuales"
date:   2019-02-27 12:00:00 -0500
categories: python
---
Jupyter y sus cuadernos(notebooks) vienen ganando mucha popularidad entre programadores que realizan `análisis de datos`, su facilidad con la que podemos realizar código y al mismo tiempo ejecutarlo y ver el resultado, hacen de este software una herramienta potente.

Sin embargo, hoy  en día existe la necesidad de manejar diversos proyectos en simultáneo y para los programadores de Python, es bien conocido que existen diversas librerías, tantas que para cada proyecto muchas veces son necesarias librerías de diversas versiones, es esta la utilidad de los entornos virtuales, además de mantener limpio el sistema operativo donde corre.

Para poder lograrlo, en nuestro terminal crearemos un nuevo Kernel, primero creamos el entorno virtual con el nombre de "**proyecto**" y lo activamos:
{% highlight bash%}
$ python -m venv proyecto
$ source proyecto/bin/activate
{% endhighlight %}

Una vez dentro del entorno virtual instalamos el _ipykernel_ e instalamos el nuevo kernel:
{% highlight bash%}
(proyecto) $ pip install ipykernel
(proyecto) $ ipython kernell install --user --name=proyecto
# Levantamos el notebook
(proyecto) $ jupyter notebook
{% endhighlight %}

Una vez que terminamos, al momento de abrir un nuevo notebook elegimos, como tipo de kernel, el que acabamos de crear, **proyecto**, luego de esto podemos instalar todo lo que necesitamos dentro de este entorno virtual.

Espero que les haya servido y cualquier duda, déjala en los comentarios.   
:D

[comment]: <> (ref:https://anbasile.github.io/programming/2017/06/25/jupyter-venv/)

