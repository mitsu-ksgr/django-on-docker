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

