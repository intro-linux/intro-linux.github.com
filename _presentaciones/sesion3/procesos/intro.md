!SLIDE

# Procesos


!SLIDE bullets

#Linux es multi-proceso

* Puede haber varios procesos
* Un programa puede consistir en _más de uno_
* Varios usuarios pueden estar

!SLIDE smbullets 

#Procesos interactivos

* Iniciados explícitamente
* Son los que quedan conectados a la terminal 
* Pueden esperar participación del usuario (p.e. `more`, `vi`)
* Pero algunos podrían enviarse al fondo (__background__)
* P.e: descargar archivos o crear respaldos

!SLIDE smbullets incremental

#Foreground vs Background

* ¿Qué pasa si iniciamos el proceso `firefox`?
* Cómo hacemos que _no_ se apropie de la terminal
* `firefox &`
* El comando `jobs` para ver los procesos de fondo
* ¿Cómo detenemos/matamos un proceso de fondo?
* La expresión `%`, `CTRL+Z` vs `CTRL+C`; `fg` vs. `bg`

!SLIDE bullets 

#Procesos automáticos

* __No__ se inician explícitamente
* Usualmente están en una cola de espera

!SLIDE bullets

#"Daemons"

* Procesos de fondo que "nunca" mueren
* Usualmente inician al arranque y esperan que se los necesite
* Ejemplo: un web server (como `apache2`)

!SLIDE bullets

#Ciclo de vida

* Un proceso nuevo sale como copia de otro
* Esto se llama `fork`. 
* Si se quiere un proceso distinto, se hace un `exec`
* Ejemplo: el comando `pstree`
* Un proceso huérfano es un __zombie__.

!SLIDE bullets

#Información 

* El comando `ps` para ver información
* El comando `top`
* Estos comandos sólo leen archivos:
  `/var/run/utmp` y `/proc/*`

!SLIDE smbullets

#Atributos de un proceso

* `ps -af`
* `UID`: el usuario que lo inició. Tiene _los mismos_ permisos
* `PID`: un identificador del proceso
* `PPID`: identificador del padre
* `TTY`: la terminal donde está conectado
* __Truco__: `ps -ef | grep <NOMBRE>`


!SLIDE bullets

#Señales

* El comando `kill` puede enviarle "señales" a un proceso:
* `9`(__SIGKILL__): interrumpir el proceso, no importa qué
* `15`(__SIGTERM__): terminar cuando se pueda
* `2`: interrumpir, si quiere el proceso

!SLIDE bullets

#Terminando procesos

* Podemos matarlos con `CTRL+C`
* Si ya no están en la terminal, 
  pero sabemos el `PID`, `kill -9 <PID>`
* Cuando un proceso termina, retorna un código de terminación.

!SLIDE bullets

#Procesos y grupos

* Necesitan permisos que el usuario no tiene
* Usan _grupos_ especiales
* Ejemplo: `apache2`
