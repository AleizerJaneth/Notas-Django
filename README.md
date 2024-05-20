# Notas-Django
Creación de notas con django y acceso de datos

1. Crear un Entorno Virtual
python -m venv venv

3. Activar el Entorno Virtual
cd venv
Scripts\activate

3. Instalar Django
Instala Django dentro del entorno virtual:
pip install django

4. Verificar Dependencias Instaladas
Para asegurarte de que Django se haya instalado correctamente, ejecuta:

pip freeze
5. Crear un Nuevo Proyecto Django
Crea un nuevo proyecto Django con:

django-admin startproject helloworld
6. Crear una Nueva Aplicación
Dentro del proyecto, crea una nueva aplicación con:

cd helloworld
python manage.py startapp myhelloapp
7. Configurar la Aplicación en settings.py
Agrega la nueva aplicación al archivo settings.py:

# settings.py
INSTALLED_APPS = [
    ...
    'myhelloapp',
]
8. Realizar Migraciones
Genera las migraciones para la nueva aplicación:

python manage.py makemigrations myhelloapp
9. Aplicar Migraciones
Aplica las migraciones al proyecto:

python manage.py migrate
10. Crear Archivos HTML Básicos
Crea dos archivos HTML básicos dentro del directorio de plantillas de la aplicación myhelloapp.

mkdir myhelloapp/templates
Archivo template1.html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Template 1</title>
</head>
<body>
    <h1>Template 1</h1>
    <ul>
        <li><a href="{% url 'template2' %}">Ir al Template 2</a></li>
    </ul>
</body>
</html>
Archivo template2.html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Template 2</title>
</head>
<body>
    <h1>Template 2</h1>
    <ul>
        <li><a href="{% url 'template1' %}">Ir al Template 1</a></li>
    </ul>
</body>
</html>
11. Modificar views.py
En el archivo views.py de la aplicación, agrega las funciones para renderizar los archivos HTML.

# views.py
from django.shortcuts import render

def template1(request):
    return render(request, 'template1.html')

def template2(request):
    return render(request, 'template2.html')
12. Definir las Rutas
Crea un archivo urls.py dentro de la aplicación para definir las rutas.

# urls.py
from django.urls import path
from . import views

urlpatterns = [
    path('template1/', views.template1, name='template1'),
    path('template2/', views.template2, name='template2'),
]
13. Incluir las Rutas en el Proyecto
Modifica el archivo urls.py en el directorio del proyecto para incluir las rutas de la aplicación.

from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path('admin/', admin.site.urls),
    path('myhelloapp/', include('myhelloapp.urls'))
]
14. Ejecutar el Servidor de Desarrollo
Inicia el servidor de desarrollo para visualizar el proyecto:

python manage.py runserver
15. Desactivar el Entorno Virtual
Una vez que hayas terminado, desactiva el entorno virtual:

deactivate
16. Crear archivo requirements.txt
Para documentar las dependencias del proyecto, genera un archivo requirements.txt con:

pip freeze > requirements.txt
¡Listo! Ahora estás listo para comenzar a desarrollar tu proyecto Django.

Este archivo README.md ha sido diseñado para proporcionar una guía clara y detallada para configurar y comenzar un proyecto Django de manera efectiva.
