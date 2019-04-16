# docker-compose-lemp

Docker compose php-fpm nginx mysql sample.
Based on:

* [markshust/docker-nginx-phpfpm-percona-alpine](https://github.com/markshust/docker-nginx-phpfpm-percona-alpine.git)
* [khs1994-docker/lnmp](https://github.com/khs1994-docker/lnmp)

## Requirements

* [Docker](https://docs.docker.com/install/)
* [Docker compose](https://docs.docker.com/compose/install/)

## Directories

```bash
.
├── conf
│   ├── mysql # config for mysql
│   ├── nginx # config for nginx vhost
│   │   └── default.conf
│   └── phpfpm # config for phpfpm
│       ├── zz-docker.conf
│       └── zz-docker.ini
├── docker-compose.yml
├── dockerfile.php7-custom # custom buildfile for local/php7 image
├── .env
├── logs # logs from services
├── README.md
├── sql # .sql or .sql.tgz files to import
└── www # for web progect, index.php required
    ├── dbtest.php # check phpfpm → mysql connection
    └── phpinfo.php # show phpinfo()
```

## First start or recreate

### update images

 `docker-compose pull --include-deps --ignore-pull-failures`

### build custom images

 `docker-compose build --pull`

### start group with recreates

 `docker-compose up -d --remove-orphans --renew-anon-volumes --force-recreate --always-recreate-deps`

### stop with recreates

 `docker-compose down -v --remove-orphans`

## Usage

### start group

 `docker-compose up -d`

### stop group

 `docker-compose down`
