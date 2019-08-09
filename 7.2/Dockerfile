FROM php:7.2-cli

RUN apt-get update && apt-get install -y cron

COPY crontab /etc/crontab
RUN chmod 644 /etc/crontab
RUN crontab /etc/crontab

CMD /usr/sbin/cron -f