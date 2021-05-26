# Script de Servicio de Gophish

/etc/init.d/gophish

```bash
#!/bin/bash
# /etc/systemd/system/gophish
# script para el arranque y la parada del servidor de gophish
# chkconfig: - 64 36
# description: arranca/para el servidor de gophish
# processname: gophish

### BEGIN INIT INFO
# Provides:          gophish
# Required-Start:    $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
### END INIT INFO

# variables del script

processName=Gophish
process=gophish
appDirectory=/home/ubuntu/gophish
logfile=/var/log/gophish/gophish.log
errfile=/var/log/gophish/gophish.error

# arranque del servidor

start() {
   echo "Iniciando "${processName}
   cd ${appDirectory}
   nohup ./$process >>$logfile 2>>$errfile & sleep 1
}

# parada del servidor

stop() {
   echo "Parando "${processName}
   pid=$(/bin/pidof ${process})
   kill -9 ${pid}
   sleep 1
}

# status del servidor

status() {
   pid=$(/bin/pidof ${process})
   if [[ "$pid" -ne "" ]]; then
   echo ${processName}" esta funcionando..."
   else
   echo ${processName}" no esta funcionando..."
   fi
}

case $1 in
   start|stop|status) "$1" ;;
esac
```



