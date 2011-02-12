!SLIDE 
# Administración de usuarios

!SLIDE smbullets 
# Cuentas de usuario

* Linux es multisuario
* Se identifican por su id de login
* Existe el super-usuario
* `/etc/passwd`, `/etc/sudoers`
* `who`, `finger`,  `whoami`
* El archivo `/etc/sudoers`
* `echo 'usuario ALL=(ALL) ALL' >> /etc/sudoers`

!SLIDE bullets

* Crear usuarios: `useradd`
* Cambiar de usuario: `su`
* Borrar: `userdel`
* Cambiar contraseña: `passwd`
* ¿Qué hace el comando `usermod`?
* ¿Y el comando `chown`?


!SLIDE smbullets

#Grupos de usuarios

* Linux crea grupos para tareas especiales
* `/etc/group`
* Cada usuario tiene su propio grupo
* Puede pertenecer a otros
* `id`, `groups`
* El grupo `root`

!SLIDE bullets

* Crear grupos: `groupadd`
* Borrar: `groupdel`
* ¿Qué hace el comando `groupmod`?
* ¿Y el comando `newgrp`?
* ¿Y el comando `chgrp`?


!SLIDE bullets

#Permisos sobre archivos

* __¿Quiénes?__ Usuario (`u`), grupo (`g`), otros (`o`)
* __¿Qué__ : lectura (`r`), escritura (`w`), ejecución (`x`), nada (`-`)
* Para poder entrar a un directorio __¡también debe ser ejecutable!__

!SLIDE bullets

#Códigos numéricos para permisos

* __4__ : equivale a lectura
* __2__: escritura
* __1__: ejecución
* se pueden combinar (sumándolos)


!SLIDE bullets

#El comando `chmod`

* `chmod MODO ARCHIVOS`
* Puede usar números: `chmod 400 archivo`
* ¿Qué hacen 500 (dir), 600, 644, 660, 700, 755 (dir), 775, 777?
* ¿Qué hace el comando `umask`?

!SLIDE 

# Un ejemplo completo


!SLIDE code small

    sudo useradd -m -s /bin/bash jgalt
    sudo passwd jgalt
    su jgalt
    cd 
    cat > hola << EOF
    #!/usr/bin/python
    print "hola mundo\n"*3
    EOF
    chmod 750 hola
    exit
    sudo groupadd grupo
    sudo usermod -a -G grupo jgalt
    sudo usermod -a -G grupo lfborjas
    



