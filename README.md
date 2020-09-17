Django on docker-compose
========================

- [Quickstart: Compose and Django \| Docker Documentation](https://docs.docker.com/compose/django/)



### Start your project.

1. remove `djangoproj`.

```sh
$ rm -rf djangoproj
$ rm manage.py
```

2. create django project.

```sh
$ docker-compose run web django-admin startproject {YOUR_PROJECT} .
```

3. if use linux: change the ownership of the new files.

```sh
$ sudo chown -R $USER:$USER .
```

4. set up the database connection.

edit `${YOUR_PROJECT}/settings.py`.


```diff
 DATABASES = {
     'default': {
-        'ENGINE': 'django.db.backends.sqlite3',
-        'NAME': BASE_DIR / 'db.sqlite3',
+        'ENGINE': 'django.db.backends.postgresql',
+        'NAME': 'postgres',
+        'USER': 'postgres',
+        'PASSWORD': 'password',
+        'HOST': 'db',
+        'PORT': '5432',
     }
 }
```

5. run `docker-compose up`!

```sh
$ docker-compose up -d
django-on-docker_db_1_319eb62ad03b is up-to-date
Creating django-on-docker_web_1_9e8ad1997549 ... done

$ docker-compose ps
            Name                          Command              State           Ports
---------------------------------------------------------------------------------------------
django-                         docker-entrypoint.sh           Up      5432/tcp
on-docker_db_1_319eb62ad03b     postgres
django-                         python manage.py runserver     Up      0.0.0.0:8000->8000/tcp
on-docker_web_1_59fbf841c410    ...


# if you want to stop servers, run "docker-compose down" command.
$ docker-compose down
Stopping django-on-docker_web_1_59fbf841c410 ... done
Stopping django-on-docker_db_1_319eb62ad03b  ... done
Removing django-on-docker_web_1_59fbf841c410     ... done
Removing django-on-docker_web_run_2_fb8ab26bb6bb ... done
Removing django-on-docker_web_run_1_c0ef76d0b718 ... done
Removing django-on-docker_db_1_319eb62ad03b      ... done
Removing network django-on-docker_default
```

6. access to `localhost:8000`

http://localhost:8000/


