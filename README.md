docker-monit: very simple daemon that helps you monitor docker containers
by maintaining PID files for them.

Create file /etc/default/docker-monit with contents:

```
CONTAINERS="container1 container2 container3"
```

Then run:

```
cp docker-monit /usr/local/bin/
```

## Upstart users

```
cp docker-monit.conf /etc/init

start docker-monit

stop docker-monit

sudo cat /var/log/upstart/docker-monit.log
```

## Monit users

Create file /etc/monit/conf.d/docker-monit with contents:

```
check process docker-monit with pidfile /var/run/docker-monit.pid
  start program = "/sbin/start docker-monit"
  stop program = "/sbin/stop docker-monit"
  if 5 restarts with 5 cycles then timeout

check process rl_db with path /var/run/docker-monit/rl_db.pid
  if 5 restarts with 5 cycles then timeout
```
