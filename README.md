### Long example : A simple messenger

Este ejemplo sigue la [guia oficial](https://erlang.org/doc/getting_started/conc_prog.html#a-larger-example). 

En primer lugar, se debe crear un cluster con nodos de erlang. Estos nodos pueden estar localizados en distintos computadores o en uno solo, para este ejemplo iniciaremos los nodos en un mismo computador. 

##### ¿Que son los nodos en erlang? 
Es una instancia de la maquina virtual de erlang ([fuente](https://stackoverflow.com/questions/38913670/what-is-an-erlang-node)), es muy ligera y se crea cada vez que se llama al comando `$ erl` en la terminal. Un nodo se identifica de la forma `username@host`. Para llamar a un nodo y darle un nombre se le llama así:

```shell
$ erl -sname gabo@mycomputer
```

La parte de `username` se puede escojer, puede ser una ciudad, un nombre o algo divertido. Por el contrario, `host` **NO** se puede escoger, este tiene que ser literalmente el usuario del computador.  

Para saber cual es el nombre del usuario se debe llamar este comando dentro de la terminal de erlang. Abra el shell de erlang con `$ erl` en la terminal  e introdusca: 

```shell
1> inet:gethostname().
output: {ok,"DESKTOP-D02VGLV"}
```

Por ejemplo, los nodos en este ejemplo se pueden llamar `pepe@DESKTOP-D02VGLV`, `miguel@DESKTOP-D02VGLV`, `papas_a_la_francesa@DESKTOP-D02VGLV`. Lo que sea...

Por ultimo, no se necesario crear los nodos con el nombre del host, podemos simplemente utilizar `$ erl -sname gabo` y el host se añade automaticamente. 

##### Setup

###### 0. Intro

En esta simulacion se tendran tres nodos: 
- *nodo messenger* : Corresponde a un nodo donde se ubica el servidor, es el intermediario entre los dos nodos. 
- *nodo ibague* : Corresponde a un nodo "en" la ciudad de ibague, donde un usuario quiere escribir mensajes a otro en neiva. 
- *nodo neiva* : Corresponde a un nodo "en" la ciudad de neiva, donde un usuario quiere escribir mensajes a otro en ibague.

###### 1. Crear los nodos
En este ejemplo se crean tres nodos, por tal motivo se abren **tres terminales** y en cada una se introduce lo sigueinte:

```shell
$ erl -sname messenger
$ erl -sname ibague
$ erl -sname neiva
```

**Importante:** En este ejemplo el host es `DESKTOP-D02VGLV` que es la maquina con la que se hace la simulacion, cuando se haga en otra maquina el host seguro va a cambiar. Para revisar el host se ejecuta `1> inet:gethostname()` en el shell de erlang. [Fuente](https://stackoverflow.com/questions/13753741/cant-get-two-erlang-nodes-to-communicate)

###### 2. Modificar el codigo
Se debe poner en a funcion el identificador del nodo del servidor. Por ejemplo, 

```erlang
%%% Change the function below to return the name of the node where the
%%% messenger server runs
server_node() ->
    'messenger@DESKTOP-D02VGLV'. % Change this
```

###### 3. Compilar el codigo
```shell
2> c(messenger).
```

###### 4. Seguir el tutorial oficial
Estos pasos eran un poco complicados, pero ya debe tener el conocimiento suficiente para seguir la [guia oficial](https://erlang.org/doc/getting_started/conc_prog.html#a-larger-example). Happy coding!
