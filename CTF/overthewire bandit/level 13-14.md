The password for the next level is stored in **/etc/bandit_pass/bandit14 and can only be read by user bandit14**. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Look at the commands that logged you into previous bandit levels, and find out how to use the key for this level.
Para resolver el ejercicio, lo que debemos hacer primero es crear una carpeta temporal, mktemp -d, despues de eso copiar el archivo sshkey.private a esa carpeta, en este caso se puede hacer con el cp, o el install, yo lo hice con cp y despues cambie los permisos en la carpeta temporal con chmod, despues de eso lo que hice fue usar el comando scp para mover ese archivo a mi equipo, lo que hice fue usar el pwd en la carpeta temporal para saber la ruta y poder copiarla a mi equipo


![](../../images/Pasted%20image%2020260402213456.png)


Después de eso, me pidió la contraseña de el nivel anterior para confirmar, la puse y al final se logró copiar el archivo de identidad para el siguiente nivel

![](../../images/Pasted%20image%2020260402213557.png)


