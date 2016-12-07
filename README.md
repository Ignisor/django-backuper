# Backuper (Django)

## How to install

- Install backuper using pip
```sh
pip install https://github.com/Ignisor/django-backuper/raw/master/django-backuper-0.2.tar.gz
```

- In your settings.py under installed programms add
```
'django_q',
'dbbackup',
'backuper_app',
```

- Run migration
```sh
python manage.py migrate
```

- Configure settings.py
```python
DBBACKUP_STORAGE = 'django.core.files.storage.FileSystemStorage'
# where to save temporary backup file that will be sended
DBBACKUP_STORAGE_OPTIONS = {'location': BASE_DIR}
# names of temporary files
DBBACKUP_FILENAME_TEMPLATE = 'db_backup'
DBBACKUP_MEDIA_FILENAME_TEMPLATE = 'media_backup'

# project name (must exist in backup server)
BACKUPER_PROJECT_NAME = 'cool_project'
# url-adress to server
BACKUPER_SERVER_URL = 'http://69.696.69.696:6969/api/backup/'
# authorisation token for server
BACKUPER_SERVER_TOKEN = '5c30a0072e361fcb599c58d3a7d1501e2731144a'
```

- now you need to start django-q qcluster
```sh
python manage.py qcluster
```

- if everything is ok, then everyday backup will be created and sended to remote server. You can check using this command.
```sh
python manage.py create_backup
```
