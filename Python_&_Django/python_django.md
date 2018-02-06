

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

Salvar y cerrar el editor / Salir y volver a acceder
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

1. Crear una carpeta con el nombre de la carpeta del proyecto con la primera letra en mayúsculas.
2. `$ mkvirtualenv <Nombre del ambiente virtual>` (Esto es para crear en una sola carpeta las carpetas bin, include, lib, local) y la carpeta la crea en `/home/rodolfo/.virtualenvs/<NOMBRE DE LA CARPETA CREADA>`

- Para instalar django (estando dentro del ambiente virtual),

```
pip install django
```

3. Crear un proyecto en django
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

*NOTA*: Se tiene que crear un usuario  y la contraseña tiene que cimplir con los requerimientos NUEVOS de seguridad.

Para correr el proyecto se ejecuta entramos a `http://localhost:8000/admin  - http://127.0.0.1:8000/admin` y entramos con el usuario y contraseña anterior puestas
```
$ python manage.py runserver
```

*NOTA:* ejecutando el siguiente comando nos muestra todas las opciones que podemos realizar cuando esta correctamente instalado
```
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
  ```

Para ejecutar el shell de python
```
$ python manage.py shell
```
- Con el shell de python se puede hacer CRUD en la B.D. Para revisar los datos que se modificaron a la tabla -> `$`

4 Crear (app) aplicación en django para un proyecto
```
$ python manage.py startapp [NombreDeLaApp] (POR CONVENCIÓN LAS APPS/MODULOS SE CREA SU NOMBRE EN PLURAL)
```

## Administrador de django
### Cambiar/crear Nuevo Usuario en Django
```
$ ./manage.py createsuperuser [# LAS PREGUNTAS SIGUIENTES SE CONTESTAN CORRECTAMENTE]
$ ./manage.py changepassword [# POR DEFAULT TOMA EL DE SISTEMA, EN CASO DE NO EXISTIR EL USUARIO Y DE PREFERENCIA SE DEBE DE CREAR UNO NUEVO]
```

### Configuraciones para modificar/mejorar el administrador de django

`list_display` -> Permite mejorar los listados agregando múltiples columnas.

- Un campo o atributo del modelo
- Una función que reciba una instancia del modelo.
- Una función en el ModelAdmin

- `list_filter` -> Permite agregar filtros para cuando queremos ver solo algunos de los datos. ( la barra que se encuentra en la barra de la derecha )
- `search_fields` -> Permite realizar una búsqueda por texto sencilla automática.
- `list_editable` -> Permite editar campos directamente en la lista. NO PUEDE EDITAR EL PRIMER CAMPO DE LA LISTA.
- `actions` -> Permite ejecutar acciones para multiples elementos de la lista --como exportar en excel
- `raw_id_fields` -> Permite evitar muchos problemas de carga cuando hay MUCHOS modelos asociados.
- `inlines` -> Permite controlar modelos relacionados dese el administrador de un modelo.
- `filter_horizontal` -> O `filter_vertical` permiten que el manejo de ManyToMany sea mucho más sencillo.
- `Context processors` -> Es una manera sencilla de agregar todas a todas tus platillas, Es un elemento que permite agregar datos al contexto que usan las plantillas para renderizarse.

**Middlewares** -> Es un elemento que permite modificar _GLOBALMENTE_ el comportamiento de tu aplicación de django, modificando la entrada y la salida. Es agregar un **plug.in** para django.

- Necesita agregarle un dato a una sesión del usuario
- Necesita detectar el pais de un usuario y cambiar su información acorde
- Necesita agregar una variable HTTP
- Necesita mostrar información según el subdominio.

**APIs REST** -> REPRESENTATIONAL STATE TRANSFER, y fue propuesta en una tesis de doctorado. Usa los cuatro métodos HTTP ( GET, POST, PUT, DELETE ) para ejecutar diferentes operaciones, lo importante son los recursos.

- Para exponer tus datos a otros programas
- Para facilitar el desarrollo de frontend
- Para crear arquitecturas orientadas a servicios

## Cache Django

:link:  https://docs.djangoproject.com/en/1.11/topics/cache/

¿Cuando usarlo?

Cuando necesitas una información que consume tiempo de calcular, procesar o conseguir (traer tweets, fotos de instagram) Cuando quieres que todo vaya mucho más rapido

- Low level
- Por vista - Per view -> :link:  https://docs.djangoproject.com/en/1.11/topics/cache/#the-per-site-cache
- En las plantillas

En Django se tiene que llevar un orden para poner en los Middleware el cache por vista. -> Middleware ordering
```
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
```

### Cache para las sesiones. Para un mejor rendimiento es posible utilizar en Django un backend de sesión  basado en cache.

:link:  https://docs.djangoproject.com/en/1.11/topics/http/sessions/#using-cached-sessions

Se pone en el `setings.py`

Para no pegarle tanto a la b.d. Este cache funciona de manera simultanea. Cada escritura que se ahce en la cache tambien se hace en la BD. La sesion solo usa la BD si los datos no estan en la memoria cache.
```
SESSION_ENGINE = 'django.contrib.sessions.backends.cached_db'
```

A un más -- si no nos importa que se pierda la sesion. Esta opción es para una simple sesion de cache. La sesion se almacena en la cache directo. No es persistente, se borrara si se llena la cache o si el servidor es reiniciado.
```
SESSION_ENGINE = 'django.contrib.sessions.backends.cache'
```

## Cache con REDIS

### Instalar REDIS
Para instalar redis en debian 9 se siguen los pasos del :link: https://redis.io/topics/quickstart
**NOTA**: Se tiene que leer con detenimiento
```
$ wget http://download.redis.io/redis-stable.tar.gz
$ tar xvzf redis-stable.tar.gz
$ cd redis-stable
$ make
$ sudo make install
```

### Configurar redis en debian para que funcione de manera correcta en localhost y en producción en debian y ubuntu

Seguir los pasos del :link: -> https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-redis-on-ubuntu-16-04

#### 1. Para empezar se necesita crear la carpeta de coonfiguración. Se usa la rura de la carpeta  `/etc/redis`
```
# mkdir /etc/redis
```

#### 2. Se copia el archivo `redis.conf` que se cuentra en el archivo que se descargo para instalar redis -> `redis-stable.tar.gz`
```
# cp /tmp/redis-stable/redis.conf /etc/redis
```

#### 3.- Se edita el archivo "redis.conf"
En el archivo, encuentre la directiva supervised. Actualmente, esto está establecido en **no**. Como estamos ejecutando un sistema operativo que usa el sistema de sistema **init(systemd)**, podemos cambiar esto a **systemd**
```
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
```

En la opción donde se espeficica que direcorio va a ocupar para trabajar se define con la opcion -> `/lab/lib/redis`
eje

```
# The working directory.
#
# The DB will be written inside this directory, with the filename specified
# above using the 'dbfilename' configuration directive.
#
# The Append Only File will also be created inside this directory.
#
# Note that you must specify a directory here, not a file name.
dir /var/lib/redis
```

Despues se tiene que guardar y cerrar.

### 3.1 (**SEGURIDAD**) Configurar contraseña para acceder a redis
Buscar en el archivo /etc/redis/redis.conf
```
# requirepass foobared
```

Descomentarlo y cambiarlo por:
```
requirepass [CONTRASEÑA]
```

**NOTA**:
Para poder hacer una contraseña en la linea de comandos se puede hacer de la siguiente manera:
```
$ echo "cualquer-texto" | sha512sum
```
```
$ echo "cualquer-texto" | sha512sum
```
salida..
```
8898c46dfd4e3e3f35082bfa1dae27e9e2d9991785828478f05fba38a98dd8ab5dc503658620684ed6cfa7b7d43c6d322c9ff9568b9c0b3c164b35f5d5191380
```

#### 4. Se crea el archivo para que el sistema systemd pueda administrarlo. Se creca el archivo y se edita con la siguiente
```
# vim /etc/systemd/system/redis.service
```
```
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
```

Despues se tiene que **guardar** y **cerrar.**

- En la seccion **[Unit]** se añade la descripción y la deficinón del requerimiento que la red va a estar disponible antes de iniciar el servicio.
- En la sección **[Servicio]**, necesitamos especificar el comportamiento del servicio. Por razones de seguridad, no deberíamos ejecutar nuestro servicio como **root**. Deberíamos usar un usuario y un grupo dedicado, que llamaremos **redis** para simplificar. Que se creeara mas adelante.
- Para iniciar el servicio, solo debemos llamar al binario `redis-server`, apuntando a nuestra configuración. Para detenerlo, podemos usar el comando Redis `shutdown`, que se puede ejecutar con el binario `redis-cli`. Además, dado que queremos que Redis se recupere de los fallos cuando sea posible, configuraremos la directiva de reinicio en `always`:
- Finalmente en la sección **[Install]** definimos el objetivo del sistema `systemd` que deberia conectarse al servicio si esta habilitado(configurado para iniciar al arranque de la maquina)

#### 5. Crear los direcorios, archivos de redis y usuarios y grupos

Crear el **usuario** redis y **grupo** redis
```
# adduser --system --group --no-create-home redis
```

Se crea la carpeta `/var/lib`
```
#  mkdir /var/lib/redis
```

Se cambian el grupo y el usuario a quien pertence la carpeta y se cambian los permisos para restringir el acceso
```
# chown redis:redis /var/lib/redis
# chmod 770 /var/lib/redis
```

#### 6.- Iniciar, parar, reiniciar el servicio creado
```
# systemctl start redis
```
```
# systemctl status redis
```
```
# systemctl stop redis
```

salida...
```
➜ ~ systemctl status redis
● redis.service - Redis In-Memory Data Store
  Loaded: loaded (/etc/systemd/system/redis.service; disabled; vendor preset: enabled)
  Active: active (running) since Tue 2018-01-16 17:20:27 CST; 54min ago
 Main PID: 14706 (redis-server)
  Tasks: 4 (limit: 4915)
  Memory: 1.0M
  CPU: 5.092s
  CGroup: /system.slice/redis.service
  └─14706 /usr/local/bin/redis-server 127.0.0.1:6379
  ```

#### 7. Hacer las pruebas para comprobar si funciona redis
#### 8. Para hacer que el servicio se inicie al inicio
```
# systemctl enable redis
```
salida...
```
Created symlink from /etc/systemd/system/multi-user.target.wants/redis.service to /etc/systemd/system/redis.service.
```

### Instalar Redis cache backend for Django
Para que funcione django con redis se tienen que instalar el paquete django-redis

- https://github.com/niwinz/django-redis
- http://niwinz.github.io/django-redis/latest/

Para que se hagan las configuraciones.

En el (dentro)ambiente del trabajo del proyecto:
```
$ pip install django-redis
```

En el `settings.py` de  queda de la iguiente manera:
```
""" CACHE """
CACHES = {
  "default": {
  "BACKEND": "django_redis.cache.RedisCache",
  "LOCATION": os.environ['CACHELOCATION'],
  "OPTIONS": {
       "CLIENT_CLASS": "django_redis.client.DefaultClient",
       "PASSWORD": os.environ['CACHEPSWD'],
       }
  }
}
""" CACHE """
```

## Templates

Configuración para que busque en todas las carpetas del proyecto la carpeta **templates**
```
TEMPLATES = [
  {
       'BACKEND': 'django.template.backends.django.DjangoTemplates',
        # SE LE DICE A DJANGO QUE BUSQUE LA CARPETA templates
       'DIRS': [os.path.join(os.path.dirname(__file__), 'templates'), ],
        # SE LE DICE A DJANGO QUE EN CADA APP BUSQUE LA CARPETA templates
       'APP_DIRS': True,
       'OPTIONS': {
       'context_processors': [
            'django.template.context_processors.debug',
            'django.template.context_processors.request',
            'django.contrib.auth.context_processors.auth',
            'django.contrib.messages.context_processors.messages',
             # CUSTOM CONTEXT_PROCESSOR
            'muebleria.context_processors.lista_link_muebles_relacionados',
            ],
       },
  },
]
```

## Estatic & Media files

En el archivo `settings.py` va la siguiente configuración.
```
""" [STATIC & MEDIA FILES] """

STATIC_URL = '/static/'

MEDIA_URL = '/media/'

STATICFILES_DIRS = (
  os.path.join(BASE_DIR, 'static'),
)

"""
SE ANADE LA RUTA PARA STATIC Y MEDIA FILES AFUERA DE CARPETA DE PROYECTO EN CARPETA COLLECT_STATIC
"""
STATIC_ROOT = os.path.join(os.path.dirname(BASE_DIR), "COLLECT_STATIC", "static_root")
MEDIA_ROOT = os.path.join(os.path.dirname(BASE_DIR), "COLLECT_STATIC", "media_root")

""" [STATIC & MEDIA FILES] """
```

En el `archivo url.py` que se encuentra al mismo nivel del archivo `settings.py`
```
if settings.DEBUG:
  """
  PARA SERVIR LOS ARCHIVOS ESTATICOS EN DESARROLLO
  """
  urlpatterns += static(settings.STATIC_URL, document_root=settings.STATIC_ROOT)
  urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
  ```

## Administración de las contraseñas enn Django

- Se ocupa de preferencia **Argon2** :link: https://docs.djangoproject.com/en/2.0/topics/auth/passwords/#using-argon2-with-django
- Par apoder ocupar **Argon2** se tienen que instalar en el ambiente de del proyecto. :link: https://pypi.python.org/pypi/argon2_cffi/
```
$ pip install argon2-cffi
```
```
""" settings.py """
PASSWORD_HASHERS = [
  'django.contrib.auth.hashers.Argon2PasswordHasher',
  'django.contrib.auth.hashers.PBKDF2PasswordHasher',
  'django.contrib.auth.hashers.PBKDF2SHA1PasswordHasher',
  'django.contrib.auth.hashers.BCryptSHA256PasswordHasher',
  'django.contrib.auth.hashers.BCryptPasswordHasher',
]
```

## Manejando archivos en AWS S3

![Manejando archivos en AWS S3](img/manejo_de_tus_archivos_en_s3.jpg "Manejando archivos en AWS S3")

## Instalar git

Para instalar git la versión mas reciente del link
- :link: https://github.com/git/git.git
- :link: https://www.kernel.org/pub/software/scm/git/
```
$ sudo apt-get update
$ sudo apt-get install git
$ sudo apt-get update
```
```
$ sudo apt-get install libcurl4-gnutls-dev libexpat1-dev gettext libz-dev libssl-dev
```
```
$ wget https://github.com/git/git/archive/v1.9.2.zip -O git.zip
```
```
$ unzip git.zip
$ cd git-XXX
$ make prefix=/usr/local all
$ sudo make prefix=/usr/local install
```

## Paso_GIT

**HACER LA LLAVE SSH**
Si quiere crear un par de llave RSA en vez de DSA solo debe usar -t rsa ( no debe especificar el largo "-b" por defecto el largo para RSA es de 4096 y es suficiente)
```
$ ssh-keygen -t rsa -b 4096 -C "comentario_de_la_llave+your_email@example.com" -> frase_de_la_llave
```

## Adding your SSH key to the ssh-agent
Before adding a new SSH key to the ssh-agent to manage your keys, you should have [checked for existing SSH](https://help.github.com/articles/checking-for-existing-ssh-keys/) keys and [generated a new SSH key](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/#generating-a-new-ssh-key)

1. Start the ssh-agent in the background.
```
$ eval "$(ssh-agent -s)"
Agent pid 59566
```

2. Add your SSH private key to the ssh-agent. If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_rsa in the command with the name of your private key file.
```
$ ssh-add ~/.ssh/id_rsa
```

3. Add the SSH key to your GitHub account.Copy the SSH key to your clipboard.
If your SSH key file has a different name than the example code, modify the filename to match your current setup. When copying your key, don't add any newlines or whitespace.
```
$ sudo apt-get install xclip
# Downloads and installs xclip. If you don't have `apt-get`, you might need to use another installer (like `yum`)

$ xclip -sel clip < ~/.ssh/id_rsa.pub
# Copies the contents of the id_rsa.pub file to your clipboard
```

**NOTA**.- Tip: If xclip isn't working, you can locate the hidden .ssh folder, open the file in your favorite text editor, and copy it to your clipboard.

4. In the upper-right corner of any page, click your profile photo, then click Settings.
5. Authentication keysIn the user settings sidebar, click SSH and GPG keys.
6. SSH Key buttonClick New SSH key or Add SSH key.
7. In the "Title" field, add a descriptive label for the new key. For example, if you're using a personal Mac, you might call this key "Personal MacBook Air".
8. The key fieldPaste your key into the "Key" field.
9. The Add key buttonClick Add SSH key.
10. Sudo mode dialogIf prompted, confirm your GitHub password.

## Probando su conexión ssh
After you've set up your SSH key and added it to your GitHub account, you can test your connection.

Before testing your SSH connection, you should have:

- [Checked for existing SSH keys](https://help.github.com/articles/checking-for-existing-ssh-keys)
- [Generated a new SSH key](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
- [Added a new SSH key to your GitHub account](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account)

1. Abrir la terminal  y
```
$ ssh -T git@github.com
```

# Attempts to ssh to GitHub
Se mostraran mensajes de advertencia ejem:
```
The authenticity of host 'github.com (192.30.252.1)' can't be established.
RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
Are you sure you want to continue connecting (yes/no)?

The authenticity of host 'github.com (192.30.252.1)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
Are you sure you want to continue connecting (yes/no)?
```

**Nota**: The example above lists the GitHub IP address as 192.30.252.1. When pinging GitHub, you may see a range of IP addresses. For more information, see "What IP addresses does GitHub use that I should whitelist?"

2. Verify that the fingerprint in the message you see matches one of the messages in step 2, then type yes:
```
Hi username! You've successfully authenticated, but GitHub does not
provide shell access.
```

You may see this error message:
```
Agent admitted failure to sign using the key.
debug1: No more authentication methods to try.
Permission denied (publickey).
```

This is a known problem with certain Linux distributions. For more information, see "[Error: Agent admitted failure to sign](https://help.github.com/articles/error-agent-admitted-failure-to-sign)".
Verify that the resulting message contains your username. If you receive a "permission denied" message, see "[Error: Permission denied (publickey)](https://help.github.com/articles/error-permission-denied-publickey)".

Para entrar vía terminal a maquina remota vía ssh
```
$ ssh root@XXX.XXX.XXX.XXX -> Después pedirá cambia la contraseña por otra nueva "xxxxxxxxxxxxxxx"
```

Para que se pueda conectar el VPS con nuestro repositorio en github se tiene que hacer una llave ssh en el usuario en el que se esta ejecutando nuestra aplicación.

Cuando se crea la llave ssh, en el repositorio de github se añade. Con nombre lacanteramack854JdsK
```
$ ssh-keygen -t rsa -b 4096 -C "comentario_de_la_llave" -> Frase contrasena_de_la_llave
```

Cuando se crea la llave ssh y esta instalal en github ahora en nuestra sesión de nuestro usuario en vps dentro de la carpeta donde se encuentra manage.py y dentro del ambiente virtual se ejecuta
```
$ git init
```

Se agrega la dirección del repositorio remoto
```
$ git remote add origin [REPOSITORIO HTTPS o SSH]
```

Se comprueba que se añadieron correctamente
```
$ git remote -v
```

Para descargar/jalar el repositorio a nuestro vps, tiene que ser de la rama master
```
$ git pull origin master -> Piede el password del ssh
```

## Instalar gunicorn, nginx, supervisor, postgresql

### Para instalar gunicorn :link: [gunicorn.org](http://gunicorn.org/)
>The gateway translates the request received from the web server so the application can handle it. The gateway is often responsible for logging and reporting as well. We will use Gunicorn as our Gateway for this tutorial.

Dentro del ambiente virtual del proyecto.
```
$ pip install django gunicorn
```

### Para instalar nginx :link: [nginx.com](https://www.nginx.com/)
>nginx (pronunciado en inglés “engine X”) es un servidor web/proxy inverso ligero de alto rendimiento y un proxy para protocolos de correo electrónico (IMAP/POP3). https://nginx.org/en/

> The web server receives an HTTP request from the client (the browser) and is usually responsible for load balancing, proxying requests to other processes, serving static files, caching and more. The web server usually interprets the request and sends it to the gateway.

```
$ sudo apt-get install nginx
```

### Para instalar supervisor -> [supuervisord](http://supervisord.org/)

>Supervisor es un sistema cliente/servidor que permite a los usuarios monitorear y controlar el numero de procesos en UNIX como los sistemas operativos.

```
$ sudo apt-get install supervisor
```

### Instalar PostgreSql :link: https://www.postgresql.org/

En debian 9

Añadir en el archivo `/etc/apt/sources.list`
```
deb http://apt.postgresql.org/pub/repos/apt/ stretch-pgdg main
```

Importar la key
```
# wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
```

Para que quede de la siguiente mandera:
```
# PostgreSQL
deb http://apt.postgresql.org/pub/repos/apt/ stretch-pgdg main
# wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
```
```
# apt-get install postgresql postgresql-client postgresql-contrib libpq-dev
```

### Instalar boto3 & django-storages
>Boto3 es un **SDK** "Software Development Kid" de "Amazon Web Services" **AWS** para **python**, que permite a los usuarios escribir software para hacer uso de los servicios de **AWS S3 y EC2**

- http://boto3.readthedocs.io/en/latest/
- https://github.com/boto/boto3

Estando dentro del ambiente virtual del proyecto
```
$ pip install boto3
```

>django-storages, es una colección de backends de almacenamiento personalizados para Django y boto3.

- https://django-storages.readthedocs.io/en/latest/
- https://github.com/jschneier/django-storages

Estando dentro del ambiente virtual.
```
$ pip install django-storages
```

Se añade `storages` en el archivo **settings.py**
```
INSTALLED_APPS = (
  ...
  'storages',
  ...
)
```

## Usar diferentes archivos settings.

ejemplo:
```
settings/
     __init__.py
     base.py
     local_audreyr.py
     local_pydanny.py
     local.py
     staging.py
     test.py
     production.py
```

ejemplo:
```
[PROYECTO]
├── OLD_settings.py
├── settings
│   ├── base.py
│   ├── dev.py
│   ├── __init__.pyc
│   └── prod.py
├── urls.py
└── wsgi.py
```

Para ejecutar los diferentes tipos de ambientes se hace de la siguiente manera
```
$ ./anage.py runserver --settings=<nombre_del_proyecto>.settings.<nombre_del_archivo_que_estamos_corriendo>
```
```
$ ./manage.py runserver --settings=nombre_del_proyecto.settings.prod
```

## Crear un "droplet" en digitalocean

- Antes de crear el droplet se tiene que crear la llave ssh
```
$ ssh-keygen -t rsa -b 4096 -C "comentario_de_la_llave+your_email@example.com"
```

y se guarda en `~/.ssh/<LLAVE> <LLAVE.pub>`
```
$ ssh-keygen -t rsa -b 4096 -C "COMENTARIO_DE_LA_LLAVE+YOUR_EMAIL@EXAMPLE.COM"
Generating public/private rsa key pair.
Enter file in which to save the key (/home/mack/.ssh/id_rsa): <FRASE_DE_LA_LLAVE>
Enter passphrase (empty for no passphrase): [SE_ESCRIBE_LA_FRASE]
Enter same passphrase again: [SE_ESCRIBE_LA_FRASE]
Your identification has been saved in xxxxxxxx_xxxxxxx_xxxxx_xxxxx.
Your public key has been saved in xxxxxxxx_xxxxxxx_xxxxx_xxxxx.pub.
The key fingerprint is:
SHA256:Lo1yGGq1tFSKqe+YLm4rdAW5M9Ahl4ZBP9sDy3tQq6c COMENTARIO_DE_LA_LLAVE+YOUR_EMAIL@EXAMPLE.COM
The key's randomart image is:
+---[RSA 4096]----+
|.++o+ |
| o+* |
| o+o.. |
| .*B+. |
| o=X+ S |
| o *+=.+ |
|o +o=o+ o |
|o* +o . |
|O=+E |
+----[SHA256]-----+
```

Ya que se tiene la llave creada se tiene en entrar al panel de control, y abrir la página [SHH Page](https://cloud.digitalocean.com/settings/security) y seleccionar el boton de **Create a New SSH Key**

![SSH Keys](img/add_key_00.png "SSH Keys")

- Para la sección etiquetada como **Nombre**, escriba el nombre de la máquina en la que creó el par de claves (por ejemplo, **Computadora personal**).
- Para la sección etiquetada **clave SSH pública**, copie y pegue la clave pública que creó en el paso anterior.
- Generalmente puede obtener esta clave copiando los resultados de:

- Se copia la llave a `xxxxxxxx_xxxxxxx_xxxxx_xxxxx.pub` **digitalocean**.
```
$ cat ~.ssh/xxxxxxxx_xxxxxxx_xxxxx_xxxxx.pub
```

![SSH Keys](img/key_added_01.png "SSH Keys")

- Los pasos anteriores han explicado cómo configurar un servidor con claves SSH preinstaladas. Sin embargo, no puede usar el panel de control para agregar claves a los **droplets** ya creadas.
- Para agregar llaves adicionales a **droplets** preexistentes, puede pegar las claves usando SSH:
```
$ cat ~/.ssh/id_rsa.pub | ssh root@[LA_IP_DE_EL_DROPLET] "cat >> ~/.ssh/authorized_keys"
```

Cuando realmente esté creando un nuevo servidor, seleccione las teclas que desea instalar en su servidor desde la pantalla **Create a droplet**. Puede seleccionar tantas llaves como desee:

![SSH Keys](img/add_key_02.png "SSH Keys")

Ya que este creado el "droplet" desaparece mensaje "Your root password will be emailed to you". Y no se recibirá el correo con la contraseña de root

- Ya que esta creado el "droplet" con la llave pre-instalada nos conectamos de la siguiente manera.
```
ssh root@[IP_DE_LA_MAQUINA_DROPLET]
```

Paso seguido se escriben las contraseñas de las llaves.
Cuando nos conectamos con otra maquina creada  que comparte la llave, no hay nececidad de escribir la contraseña de **root**

Cuando se elimina (destruye) un "droplet" y antes de crear un **droplet** nuevo al cual nos conectamos, posiblemente se pueda ver este mensaje
```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@ WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED! @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
```

Si se presenta el caso el nuevo **droplet** posiblemente tiene la misma IP que la anterior eliminada (destruida) pero una llave SHH diferente, Se puede eliminar el mensaje de **advertencia** eliminando la anterior llave SHH del sistema con este COMANDO.
```
ssh-kengen -T [IP_DE_LA MAQUINA_DROPLET]
```

- DESHABILITAR EL ACCESO MEDIANTE CON CONTRASEÑA ROOT
1. Por seguridad es mejor solo entrar al servidor con las llaves y no ocupar ninguna contraseña escrita.
2. Es necesario editar las configuraciones SSHd del servidor en la ruta -> /etc/ssh/sshd_config
3. Editarlo con "vim" en la linea donde se encuentre "PermitRootLogin" para que se vea como sigue:
```
PermitRootLogin without-password
```

Después es necesario reiniciar el **droplet** o reiniciar el servicio **sshd** de la siguiente manera
```
# ps auxw | grep ssh
USER PID %CPU %MEM VSZ RSS TTY STAT START TIME COMMAND
root 681 0.0 0.1 49948 2332 ? Ss 2012 3:23 /usr/sbin/sshd -D
```
```
# kill -HUP 681
```

Ahora el inicio de sesión **root** del servidor está protegido y puede entrar intentando con SSH directamente como **root**, este servidor desde un sistema que no tiene sus claves compartidas y será expulsado automáticamente sin que se le solicite una contraseña de root.

A las llaves creadas se les cambian los permisos para que solo sean de solo lectura para **root** de muestro sistema de archivos

:link: https://es.wikipedia.org/wiki/Chmod
```
# chmod 400 ruta/al/archivo/.ssh/xxxxxxxx_xxxxxxx_xxxxx_xxxxx.pub
```
```
# chmod 400 ruta/al/archivo/.ssh/xxxxxxxx_xxxxxxx_xxxxx_xxxxx.pub
```

> 4 es para "lectura"  
2 es para "escritura"  
1 es para "ejecución"  
0 es para "denegar permiso"


```
chmod [DIGITIGO-DUEÑO][DIGITO-GRUPO][DIGITO-RESTO] <ARCHIVO>
```

## Crear usuarios en el servidor de producción

**NOTA**:
Para poder hacer una contraseña en la linea de comandos se puede hacer de la siguiente manera:
```
$ echo "cualquer-texto" | sha512sum
```
```
$ echo "cualquer-texto" | sha512sum
```
salida..
```
8898c46dfd4e3e3f35082bfa1dae27e9e2d9991785828478f05fba38a98dd8ab5dc503658620684ed6cfa7b7d43c6d322c9ff9568b9c0b3c164b35f5d5191380
```

1. Se crea un usuario nuevo
```
# adduser [NOMBRE_DE_USUARIO]
```
salida..
```
# adduser [NOMBRE_DE_USUARIO]
Adding user `NOMBRE_DE_USUARIO' ...
Adding new group `NOMBRE_DE_USUARIO' (1000) ...
Adding new user `NOMBRE_DE_USUARIO' (1000) with group `NOMBRE_DE_USUARIO' ...
Creating home directory `/home/prueba1' ...
Copying files from `/etc/skel' ...
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
Changing the user information for prueba1
Enter the new value, or press ENTER for the default
Full Name []:
Room Number []:
Work Phone []:
Home Phone []:
Other []:
Is the information correct? [Y/n] y
```

Para eliminar el usuario
```
# deluser [NOMBRE_DE_USUARIO]
```

Posterior se tiene que eliminar de la carpeta `/home/` la carpeta con el nombre del usuario `[NOMBRE_DEL_USUARIO]`

2. Se tiene que añadir el usuario al grupo **sudo**
```
# usermod -aG sudo [NOMBRE_DE_USUARIO]
```

>-G, --groups -> Al grupo al que se añadirá.  
-a, --append -> Añadir el usuario al grupo suplementario y solo se usa con "-G"

[Guide to **adduser** - **useradd**](https://www.tecmint.com/add-users-in-linux/)

3. Instalar un **FireWall** -> UFW (Uncomplicated Firewall)

Link extra -> [UFW Essentials: Common Firewall Rules and Commands](https://www.digitalocean.com/community/tutorials/ufw-essentials-common-firewall-rules-and-commands)

#### Para instalar UFW
```
$ sudo apt-get install ufw
```

#### Para usar UFW con IPV6 - LAS CONFIGURACIONES PARA IPV4 FUNCIONAN PARA IPV6

Si el servidor Ubuntu tiene habilitado IPv6, asegurarse de que UFW esté configurado para admitir IPv6 para que  
administre reglas de firewall para IPv6 además de IPv4.  
Para hacer esto, abra la configuración de UFW con su editor favorito  


`/etc/default/ufw excerpt`
```
IPV6=yes
```

#### Revisar el status y las reglas, de forma predeterminada UFW esta deshabilitado

```
sudo ufw status verbose

Salida:
Status: inactive
```

#### Por ejemplo si estuviera habilidato SHH el puerto 22 se veria de esta forma

```
Salida:
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To Action From
-- ------ ----
22/tcp ALLOW IN Anywhere
```

#### NOTA: ANTES DE QUE SE HABILITE UFW Y CONFIGURARLO SE TIENE QUE CONFIGURAR EL PUERTO DE SSH

#### Para poner por default las reglas de UFW
Estos parametros son suficientes para una computadora personal, pero los servidores necesitan responder a peticiones desde fuera

```
$ sudo ufw default deny incoming
$ sudo ufw default allow outgoing
```

#### Permitir conexiones SHH

```
$ sudo ufw allow ssh
```

#### Permitir conexiones SHH POR EL PUERTO

```
$ sudo ufw allow 22
```

#### Permitir conexiones SHH POR OTRO PUERTO

```
$ sudo ufw allow 2222
```

#### Habilitar ufw

```
$ sudo ufw enable
```

#### Para ver las reglas que estan definidas

```
$ sudo ufw status verbose
```

### Permitir otras conexiones

#### HTTP—port 80
Conexiones HTTP , conexiones que no estan encriptadas

```
sudo ufw allow http
```

#### Permitir el servicio HTTP por puerto

```
sudo ufw allow 80
```

#### HTTPS—port 443
Conexiones HTTPS, conexiones que estan encriptadas

```
sudo ufw allow https
```

#### Permitir el servicio HTTPS por puerto

```
sudo ufw allow 443
```

#### FTP—port 21
Conexiones FTP , transferencia de archivos encriptada

```
sudo ufw allow ftp
```

#### Permitir el servicio FTPS por puerto

```
sudo ufw allow 21/tcp
```

#### Permitir puertos especificos

```
$ sudo ufw allow 6000:6007/tcp
$ sudo ufw allow 6000:6007/udp
```

#### Permitir IP especifica

```
$ sudo ufw allow from 15.15.15.51
```

#### Permitir IP especifica y asignarle un puerto

```
$ sudo ufw allow from 15.15.15.51 to any port 22
```

#### Permitir sub-redes
Si se requiere permitir las direcciones que van desde 15.15.15.15 a 15.15.15.254

```
$ sudo ufw allow from 15.15.15.0/24
```

#### Asignarle a la subred que se conecte por el puerto 22

```
sudo ufw allow from 15.15.15.0/24 to any port 22
```

#### Si desea crear una regla de firewall que solo se aplique a una interfaz de red específica,
puede hacer especificando "**allow in on**" seguido del nombre de la interfaz de red.  
Es posible que desee buscar sus interfaces de red antes de continuar.  

```
ip addr
```

Output Excerpt:
```
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state

3: eth1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default
```

Se tiene que identificar la red la interfas de la red publica, y despues se podria habilitar el servicio HTTP
(puerto 80)

```
$ sudo ufw allow in on eth0 to any port 80
```

Haciendo esto, se le permite a la interfas de red recibir peticiones HTTP de usuarios de internet

#### Si se requiere permitir a MySQL que tiene el puerto 3306, que escuche peticiones de una red privada en la interfaz eth1, se podria hacer
Esto permitiría que otros servidores en su red privada se conectaran a su base de datos MySQL

```
sudo ufw allow in on eth1 to any port 3306
```

### Denegar conexiones
De menera predeterminada UFW niega peticiones, pero si se requiere enfatizar o denegar especificas conexiones de uan IP especifica o subred  
Para denegar, se pueden ocupar las reglas antes mencionadas, solo lo que se necesita hacer es cambiar "alow" por "deny"  

#### Denegar conexiones HTTP

```
sudo ufw deny http
```

#### Denegar conexiones de 15.15.15.15

```
sudo ufw deny from 15.15.15.51
```

### Borrar/eliminar reglas, hay dos formas

Se pueden eliminar por "**el numero de la regla**" o por "**la regla actual**"

#### EL NUMERO DE LA REGLA

Para saber cual es el numero de la regla

```
sudo ufw status numbered
```

```
salida
Status: active

  To Action From
  -- ------ ----
[ 1] 22 ALLOW IN 15.15.15.0/24
[ 2] 80 ALLOW IN Anywhere
```

Si se requiere eliminar la regla dos

```
sudo ufw delete 2
```

#### LA REGLA ACTUAL
Si se requiere eliminar la regla "allow http" y se aliminará IPv4 y IPv6

```
sudo ufw delete allow http
```

#### REINICIAR EL SERVICIO ufw
Si ya tiene las reglas de UFW configuradas pero decide que desea comenzar de nuevo, puede usar el comando de reinicio
```
sudo ufw reset
```
