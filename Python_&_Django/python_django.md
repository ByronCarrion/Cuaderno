

![Django](img/python_&_django_01.jpg "Django")
![Django](img/python_&_django_02.jpg "Django")
![Django](img/python_&_django_03.jpg "Django")
![Django](img/python_&_django_04.jpg "Django")
![Django](img/python_&_django_05.jpg "Django")


# Django en maquina de desarrollo.

## 1.  Actualizar los paquetes de Ubuntu o del sistema Debian:

```
$ sudo apt-get install python-pip python3-pip python3-dev python-dev build-essential python-setuptools python-pip virtualenv virtualenvwrapper git nginx supervisor ufw
```
```
$ pip install -r requirements.txt
```

### Actualizar el índice local de paquetes
```
$ sudo apt-get update
```

### Actualizar todos los paquetes que puedan ser actualizados
```
$ sudo apt-get dist-upgrade
```

### Remover los paquetes que no sean necesarios
```
$ sudo apt-get autoremove
```

### Reiniciar la maquina (solo necesario para algunas actualizaciones)
```
$ sudo reboot
```

## 2.  Instalar build-essential y pythin dev

Build-essential es el paquete que provee todas las herramientas de compilación estándar de C.
Python-dev provee los archivos necesarios para compilar módulos Python/C.
Para instalar `pip` en Debian

```
$ sudo apt-get install build-essential python-dev python-pip
```
```
$ sudo pip install --upgrade pip
```

### Para instalar pip en Ubuntu
```
$ sudo apt-get install  python-setuptools build-essential python-dev
```
```
$ sudo easy_install pip
```

## 3. Instalar pip en debian & ubuntu
```
sudo apt-get install python-pip
```
```
# pip install -U pip
```

- Actualizar pip

:link: https://pip.pypa.io/en/latest/installing.html

## 4. Instalar virtualenv y virtualenvwrapper

Virtualenv se usa para aislar en ambientes virtuales diferentes los paquetes que vamos a instalar.
Virtualenvwrapper se usa para agilizar virtualenv

### Instalar virtualenv y virtualenvwrapper
```
$ sudo pip install virtualenv virtualenvwrapper
```

### Editar el archivo .bashrc con ayuda de vim
```
$ vim .bashrc
```

### Agregar la siguiente linea al final del archivo para #habilitar el virtualenvwrapper
```
export WORKON_HOME=$HOME/.virtualenvs
export PROJECT_HOME=$HOME/[NOMBRE_DE_USUARIO]
source /usr/local/bin/virtualenvwrapper.sh (esto es para las distribuciones debian y ubuntu)
```

Salvar y cerrar el editor
Salir y volver a acceder
```
$ exit
```

### Lo anterior se hace para que no se tenga que hacer lo siguiente
```
$ source virtualenvwrapper.sh
$ workon NOMBRE_ENTORNO
```

Por defecto virtualenvwrapper crea todos los virtualenvs en la carpeta `~/.virtualenvs`. Sin embargo ese comportamiento se puede cambiar. Para eso se necesita agregar un par de variables de entorno al archivo `~/.bashrc` ó `~/.bash_profile`:
```
export WORKON_HOME=/opt/virtualenvs
export VIRTUALENVWRAPPER_HOOK_DIR=$WORKON_HOME/hooks
```

La variable `WORKON_HOME` determina en que directorio se deben crear los virtualenvs al ejecutar el comando mkvirtualenv.
La segunda variable, `VIRTUALENVWRAPPER_HOOK_DIR`, establece el directorio en donde se instalaran algunos scripts muy útiles que pueden ser usados para automatizar ciertas tareas, como por ejemplo hacer un commit a un repositorio justo antes de desactivar el *virtualenv*.

## 5.  Crear un ambiente virtual
### Crear un ambiente virtual
```
$ mkvirtualenv <NOMBRE_DEL_AMBIENTE_VIRTUAL>
```

### Algunos comandos útiles para el ambiente virtual:
### Desactivar ambiente virtual
```
$ deactivate
```

### Activar ambiente virtual o cambiar a otro
```
$ workon <NOMBRE_DEL_AMBIENTE_VIRTUAL>
```

### Mostrar lo paquetes instalados en un ambiente virtual
```
$ workon <NOMBRE_DEL_AMBIENTE_VIRTUAL>
```
```
$ pip freeze
```

### Listar los ambientes vistuales
```
$ lsvirtualenv
```

*lsvirtualenv [-b] [-l] [-h]*

- -b -> Brief mode, disables verbose output.
- -l -> Long mode, enables verbose output. Default.
- -h -> Print the help for lsvirtualenv.

### Mostrar los detalles de un solo ambiente vistual
```
$ showvirtualenv <NOMBRE DEL AMBIENTE VIRTUAL>
```

### Remover el ambiente virtual posicionando nos en la carpeta del proyecto
```
$ rmvirtualenv <NOMBRE DE LA CARPETA VIRTUAL> (Se tiene que desactivar primero el ambiente virtual)
```

### Calling lssitepackages shows the content of the site-packages directory of the currently-active virtualenv.
```
$ lssitepackages
```

### Mostrar todos los comandos
```
$ virtualenvwrapper
```
```
add2virtualenv: add directory to the import path
allvirtualenv: run a command in all virtualenvs
cdproject: change directory to the active project
cdsitepackages: change to the site-packages directory
cdvirtualenv: change to the $VIRTUAL_ENV directory
cpvirtualenv: duplicate the named virtualenv to make a new one
lssitepackages: list contents of the site-packages directory
lsvirtualenv: list virtualenvs
mkproject: create a new project directory and its associated virtualenv
mktmpenv: create a temporary virtualenv
mkvirtualenv: Create a new virtualenv in $WORKON_HOME
rmvirtualenv: Remove a virtualenv
setvirtualenvproject: associate a project directory with a virtualenv
showvirtualenv: show details of a single virtualenv
toggleglobalsitepackages: turn access to global site-packages on/off
virtualenvwrapper: show this help message
wipeenv: remove all packages installed in the current virtualenv
workon: list or change working virtualenvs
```

## Estructura de django para crear proyectos

1. - Crear una carpeta con el nombre de la carpeta del proyecto con la primera letra en mayúsculas.
2. - `$ mkvirtualenv <Nombre del ambiente virtual>` (Esto es para crear en una sola carpeta las carpetas bin, include, lib, local) y la carpeta la crea en `/home/rodolfo/.virtualenvs/<NOMBRE DE LA CARPETA CREADA>

- Para instalar django (estando dentro del ambiente virtual),

```
pip install django
```

### 3. Crear un proyecto en django
```
$django-admin.py startproject [NombreDeTuProyecto]
```

Despues de hacer hacer el proyecto se tiene que ceacrear las tablas del proyecto, con el siguiente comando. Crea las/Prepara las migraciones para cualquier cambio que se halla echo para despues aplicarlas.

```
$ python manage.py makemigrations
```

Despues para aplicar las migraciones se ejecuta el sig comando; de esta manera los cambios echos a las BD se aplican y en caso de aver errores se mostraran en pantalla

```
$ python manage.py migrate
```
salida..
```
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying auth.0008_alter_user_username_max_length... OK
  Applying sessions.0001_initial... OK
  ```

Esto se hace para poder crear la BD inicial del proyecto y despues se tiene que crear el usuario (super usuario) para que tenga acceso sin restriciones al proyecto y a las aplicaciones.

```
$ python manage.py createsuperuser
```

*NOTA*: Se tiene que crear un usuario (mack/rodolfo) y la contraseña tiene que cimplir con los requerimientos NUEVOS de seguridad (Django mack/rodolfo 2017)

Para correr el proyecto se ejecuta entramos a http://localhost:8000/admin  - http://127.0.0.1:8000/admin y entramos con el usuario y contraseña anterior puestas
$ python manage.py runserver

NOTA: ejecutando el siguiente comando nos muestra todas las opciones que podemos realizar cuando esta correctamente instalado

./manage.py
Type 'manage.py help <subcommand>' for help on a specific subcommand.

Available subcommands:

[auth]
  changepassword
  createsuperuser

[contenttypes]
  remove_stale_contenttypes

[django]
  check
  compilemessages
  createcachetable
  dbshell
  diffsettings
  dumpdata
  flush
  inspectdb
  loaddata
  makemessages
  makemigrations
  migrate
  sendtestemail
  shell
  showmigrations
  sqlflush
  sqlmigrate
  sqlsequencereset
  squashmigrations
  startapp
  startproject
  test
  testserver

[sessions]
  clearsessions

[staticfiles]
  collectstatic
  findstatic
  runserver

Para ejecutar el shell de python ->
$ python manage.py shell
- Con el shell de python se puede hacer CRUD en la B.D. Para revisar los datos que se modificaron a la tabla -> $

### 4.-Crear (app) aplicación en django para un proyecto ->
$ python manage.py startapp [NombreDeLaApp] (POR CONVENCIÓN LAS APPS/MODULOS SE CREA SU NOMBRE EN PLURAL)

## Administrador de django
### Cambiar/crear Nuevo Usuario en Django

$ ./manage.py changepassword # POR DEFAULT TOMA EL DE SISTEMA, EN CASO DE NO EXISTIR EL USUARIO Y DE PREFERENCIA SE DEBE DE CREAR UNO NUEVO
$ ./manage.py createsuperuser # LAS PREGUNTAS SIGUIENTES SE CONTESTAN CORRECTAMENTE

### Configuraciones para modificar/mejorar el administrador de django

list_display -> Permite mejorar los listados agregando múltiples columnas.

- Un campo o atributo del modelo
- Una función que reciba una instancia del modelo.
- Una función en el ModelAdmin

list_filter -> Permite agregar filtros para cuando queremos ver solo algunos de los datos. ( la barra que se encuentra en la barra de la derecha )
search_fields -> Permite realizar una búsqueda por texto sencilla automática.
list_editable -> Permite editar campos directamente en la lista. NO PUEDE EDITAR EL PRIMER CAMPO DE LA LISTA.
actions -> Permite ejecutar acciones para multiples elementos de la lista --como exportar en excel
raw_id_fields -> Permite evitar muchos problemas de carga cuando hay MUCHOS modelos asociados.
inlines -> Permite controlar modelos relacionados dese el administrador de un modelo.
filter_horizontal -> O filter_vertical permiten que el manejo de ManyToMany sea mucho más sencillo.
Context processors -> Es una manera sencilla de agregar todas a todas tus platillas, Es un elemento que permite agregar datos al contexto que usan las plantillas para renderizarse.

**Middlewares** -> Es un elemento que permite modificar GLOBALMENTE el comportamiento de tu aplicación de django, modificando la entrada y la salida. Es agregar un plug.in para django.

- Necesita agregarle un dato a una sesión del usuario
- Necesita detectar el pais de un usuario y cambiar su información acorde
- Necesita agregar una variable HTTP
- Necesita mostrar información según el subdominio.

**APIs REST** -> REPRESENTATIONAL STATE TRANSFER, y fue propuesta en una tesis de doctorado. Usa los cuatro métodos HTTP ( GET, POST, PUT, DELETE ) para ejecutar diferentes operaciones, lo importante son los recursos.

- Para exponer tus datos a otros programas
- Para facilitar el desarrollo de frontend
- Para crear arquitecturas orientadas a servicios

## Cache Django
https://docs.djangoproject.com/en/1.11/topics/cache/
¿Cuando usarlo?
Cuando necesitas una información que consume tiempo de calcular, procesar o conseguir (traer tweets, fotos de instagram) Cuando quieres que todo vaya mucho más rapido

- Low level
- Por vista - Per view -> https://docs.djangoproject.com/en/1.11/topics/cache/#the-per-site-cache
- En las plantillas

En Django se tiene que llevar un orden para poner en los Middleware el cache por vista. -> Middleware ordering

""" setting.py """
MIDDLEWARE = [
  'django.middleware.security.SecurityMiddleware',
  'django.middleware.cache.UpdateCacheMiddleware', # ESTO PARA USAR CACHING PERO EN PRODUCCION EN LA 2da LINEA
  'django.contrib.sessions.middleware.SessionMiddleware',
  'django.middleware.common.CommonMiddleware',
  'django.middleware.csrf.CsrfViewMiddleware',
  'django.contrib.auth.middleware.AuthenticationMiddleware',
  'django.contrib.messages.middleware.MessageMiddleware',
  'django.middleware.cache.FetchFromCacheMiddleware', # ESTO PARA USAR CACHING PERO EN PRODUCCION EN LA PENULTINA LINEA
  'django.middleware.clickjacking.XFrameOptionsMiddleware',
]

### Cache para las sesiones. Para un mejor rendimiento es posible utilizar en Django un backend de sesión  basado en cache.

https://docs.djangoproject.com/en/1.11/topics/http/sessions/#using-cached-sessions

Se pone en el setings.py
Para no pegarle tanto a la b.d. Este cache funciona de manera simultanea. Cada escritura que se ahce en la cache tambien se hace en la BD. La sesion solo usa la BD si los datos no estan en la memoria cache.

SESSION_ENGINE = 'django.contrib.sessions.backends.cached_db'

A un más -- si no nos importa que se pierda la sesion. Esta opción es para una simple sesion de cache. La sesion se almacena en la cache directo. No es persistente, se borrara si se llena la cache o si el servidor es reiniciado.

SESSION_ENGINE = 'django.contrib.sessions.backends.cache'

## Cache con REDIS

### Instalar REDIS
Para instalar redis en debian 9 se siguen los pasos del link https://redis.io/topics/quickstart
NOTA: Se tiene que leer con detenimiento
$ wget http://download.redis.io/redis-stable.tar.gz
$ tar xvzf redis-stable.tar.gz
$ cd redis-stable
$ make
$ sudo make install

### Configurar redis en debian para que funcione de manera correcta en localhost y en producción en debian y ubuntu
Seguir los pasos del link -> https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-redis-on-ubuntu-16-04

#### 1.- Para empezar se necesita crear la carpeta de coonfiguración. Se usa la rura de la carpeta  /etc/redis
# mkdir /etc/redis

#### 2.- Se copia el archivo "redis.conf" que se cuentra en el archivo que se descargo para instalar redis -> "redis-stable.tar.gz"
# cp /tmp/redis-stable/redis.conf /etc/redis

#### 3.- Se edita el archivo "redis.conf"
En el archivo, encuentre la directiva supervised. Actualmente, esto está establecido en "no". Como estamos ejecutando un sistema operativo que usa el sistema de sistema init(systemd), podemos cambiar esto a systemd

# "/etc/redis/redis.conf"
# If you run Redis from upstart or systemd, Redis can interact with your
# supervision tree. Options:
# supervised no - no supervision interaction
# supervised upstart - signal upstart by putting Redis into SIGSTOP mode
# supervised systemd - signal systemd by writing READY=1 to $NOTIFY_SOCKET
# supervised auto - detect upstart or systemd method based on
# UPSTART_JOB or NOTIFY_SOCKET environment variables
# Note: these supervision methods only signal "process is ready."
# They do not enable continuous liveness pings back to your supervisor.
supervised systemd

En la opción donde se espeficica que direcorio va a ocupar para trabajar se define con la opcion -> /lab/lib/redis
eje
. . .

# The working directory.
#
# The DB will be written inside this directory, with the filename specified
# above using the 'dbfilename' configuration directive.
#
# The Append Only File will also be created inside this directory.
#
# Note that you must specify a directory here, not a file name.
dir /var/lib/redis

. . .

Despues se tiene que guardar y cerrar.

### 3.1 (SEGURIDAD) Configurar contraseña para acceder a redis
Buscar en el archivo /etc/redis/redis.conf
# requirepass foobared

Descomentarlo y cambiarlo por:

requirepass [CONTRASEÑA]

NOTA:
Para poder hacer una contraseña en la linea de comandos se puede hacer de la siguiente manera:

$ echo "cualquer-texto" | sha512sum

$ echo "cualquer-texto" | sha512sum
salida..
8898c46dfd4e3e3f35082bfa1dae27e9e2d9991785828478f05fba38a98dd8ab5dc503658620684ed6cfa7b7d43c6d322c9ff9568b9c0b3c164b35f5d5191380

#### 4.- Se crea el archivo para que el sistema systemd pueda administrarlo. Se creca el archivo y se edita con la siguiente

# vim /etc/systemd/system/redis.service

# /etc/systemd/system/redis.service
[Unit]
Description=Redis In-Memory Data Store
After=network.target

[Service]
User=redis
Group=redis
ExecStart=/usr/local/bin/redis-server /etc/redis/redis.conf
ExecStop=/usr/local/bin/redis-cli shutdown
Restart=always

[Install]
WantedBy=multi-user.target

Despues se tiene que guardar y cerrar.

- En la seccion [Unit] se añade la descripción y la deficinón del requerimiento que la red va a estar disponible antes de iniciar el servicio.
- En la sección [Servicio], necesitamos especificar el comportamiento del servicio. Por razones de seguridad, no deberíamos ejecutar nuestro servicio como "root". Deberíamos usar un usuario y un grupo dedicado, que llamaremos redis para simplificar. Que se creeara mas adelante.
- Para iniciar el servicio, solo debemos llamar al binario redis-server, apuntando a nuestra configuración. Para detenerlo, podemos usar el comando Redis shutdown, que se puede ejecutar con el binario redis-cli. Además, dado que queremos que Redis se recupere de los fallos cuando sea posible, configuraremos la directiva de reinicio en always:
- Finalmente en la sección [Install] definimos el objetivo del sistema systemd que deberia conectarse al servicio si esta habilitado(configurado para iniciar al arranque de la maquina)
