
Para resolver este nivel que nos sacaba instantaneamente lo que tenemos que hacer es esperar a que la terminal nos muestre un indicio de --more-- que significa que esta usando un programa paginador, esto se logra faci, reduciendo la ventana del terminal a una sola linea, despues de esto, solo presionar la letra v para abrir el editor vim, como pista tenemos que en el ejercicio anterior nos dijo que ste shell no es comun, no tiene /bin/bash, asi que nuestro trabajo es ese, al estar en vim, lo que debemos hacer es
`:set shell=/bin/bash` y despues ejecutamos el comando `:shell`
y seguido de eso tenemos acceso a el shell de bandit26, el resto es simple, tenemos un archivo bandit27-do que tiene permisos de administrador para bandit27, entonces para acceder a la carpeta de contraseñas de bandit lo que debemos de hacer es `./bandit27-do cat etc/bandit_pass/bandit27`


![](../../images/Pasted%20image%2020260406174854.png)


