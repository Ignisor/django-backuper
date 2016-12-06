# Backuper (Django)

## How to install

- Install backuper using pip
```sh
pip install [link_to_github_with_tar.gz]
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
BACKUPER_PROJECT_NAME = 'UberTest'
# url-adress to server
BACKUPER_SERVER_URL = 'http://127.0.0.1:8001/api/backup/'
# login and password for server
BACKUPER_SERVER_LOGIN = 'admin'
BACKUPER_SERVER_PASSWORD = 'cucumber'
```

- now you need to start django-q qcluster
```sh
python manage.py qcluster
```

- if everything is ok, then everyday backup will be created and sended to remote server. You can check using this command.
```sh
python manage.py create_backup
```
