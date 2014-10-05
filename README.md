docker-monit: very simple daemon that helps you monitor docker containers

Make file /etc/defaults/docker-monit

  CONTAINERS="container1 container2 container3"

cp docker-monit /usr/local/bin/

## Upstart users

cp docker-monit.conf /etc/init

start docker-monit

stop docker-monit

sudo cat /var/log/upstart/docker-monit.log

## Monit users


