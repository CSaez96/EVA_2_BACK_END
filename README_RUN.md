Salud Vital - EVA2 (Back End)
--------------------------------
Instrucciones rápidas para Windows (usa entorno virtual eva2)

1) Crear y activar entorno virtual (Windows PowerShell):
   python -m venv eva2
   .\eva2\Scripts\Activate.ps1   # o Activate.bat en cmd
   pip install --upgrade pip

2) Instalar dependencias:
   pip install -r requirements.txt

3) (.env) Ya incluido con valores por defecto para PostgreSQL. Si quieres probar sin Postgres,
   borra/renombra .env o deja las variables POSTGRES_* sin configurar y el proyecto usará sqlite (db.sqlite3 incluida para pruebas).

4) Migraciones (si usas Postgres, asegúrate que el servicio esté corriendo y que el usuario/DB existan):
   python manage.py makemigrations
   python manage.py migrate

5) Crear superuser y usuario aplicativo requerido:
   python manage.py createsuperuser
   python manage.py shell
   >>> from django.contrib.auth.models import User
   >>> User.objects.create_user('usuario_eva2', password='Password123')
   >>> exit()

6) Cargar datos de ejemplo (si usas fixtures):
   python manage.py loaddata clinica/fixtures/datos_ejemplo.json

7) Ejecutar servidor:
   python manage.py runserver

Notas:
- El archivo .env viene con valores por defecto (Postgres). Si no quieres usar Postgres local, usa sqlite por defecto.
- Footer con nombre y sección agregado en templates.
