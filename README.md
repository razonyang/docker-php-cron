PHP Cron Docker Image
=====================

Tags
----

- razonyang/php-cron:7.4(latest)
- razonyang/php-cron:7.3
- razonyang/php-cron:7.2

Usage
-----

### Docker run

```shell
$ docker run --name php-cron razonyang/php-cron:7.4
```

Verify:

```shell
$ docker exec php-cron tail -f /tmp/cron.log
2019-08-09 06:28:01
2019-08-09 06:29:01
2019-08-09 06:30:01
2019-08-09 06:31:01
2019-08-09 06:32:01
```

Custom configuration

```shell
$ docker run --name php-cron \
    -v /your/crontab:/etc/crontab:ro razonyang/php-cron:7.3 \
    /bin/bash -c "/usr/bin/crontab /etc/crontab && /usr/sbin/cron -f"
```

We MUST apply the new `crontab` before starting `cron` service.


### Docker compose

`docker-compose.yml`

```yml
services:
  cron:
    image: razonyang/php-cron:7.3
    restart: always
    volumes:
      - ./crontab:/etc/crontab:ro
    command: bash -c "/usr/bin/crontab /etc/crontab && /usr/sbin/cron -f"
```
