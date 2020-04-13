# example cron/crontab.txt
```
# run every minutes
* * * * * echo "Hello world" >> /var/log/cron.log

# run docker command
00 3 * * 0 docker start [CONTAINER_NAME]

# backup mysql weekly
00 3 * * 0 mysqldump -h database -uroot -p$MYSQL_ROOT_PASSWORD [DATABASE_NAME] | gzip > /backup/mysqldump/weekly/[DATABASE_NAME]_$(date +%Y%m%d-%H%M%S).sql.gz
```

# docker run (other options)
```
docker image build -t cron .
docker run --name cron -v /var/run/docker.sock:/var/run/docker.sock -v $(pwd)/cron.log:/var/log/cron.log -v backup:/backup -d cron
```
