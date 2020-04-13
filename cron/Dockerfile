FROM alpine
RUN apk update && apk add mysql-client docker-cli
COPY ./crontab.txt /cron/crontab.txt
WORKDIR /cron
RUN /usr/bin/crontab /cron/crontab.txt
CMD ["/usr/sbin/crond", "-f", "-l", "8"]
