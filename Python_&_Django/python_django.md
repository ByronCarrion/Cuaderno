

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

# Actualizar el índice local de paquetes
```
$ sudo apt-get update
```

# Actualizar todos los paquetes que puedan ser actualizados
```
$ sudo apt-get dist-upgrade
```

# Remover los paquetes que no sean necesarios
```
$ sudo apt-get autoremove
```

# Reiniciar la maquina (solo necesario para algunas actualizaciones)
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

### Salvar y cerrar el editor
### Salir y volver a acceder
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
