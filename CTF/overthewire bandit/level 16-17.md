
Para este nivel primero nos pide saber cuales son los puertos abiertos en los que se puede escuchar y cuales son ssl y cuales no, primero vamos paso a paso para optimizar tiempo
primero hacemos un nmp -p 31000-32000 localhost para saber que puertos sirven, si no son muchos,
![[Pasted image 20260403183929.png]]
Verificando que no son muchos para que el tiempo de respuesta sea mas rapido usamos cada uno con el comando sV para ver informacion detallada de sobre donde corre y el localhost
![[Pasted image 20260403183947.png]]
Nos damos cuenta que hay puertos que tienen echo, es decir que nos va a regresar la misma contraseña que pongamos, entonces escogemos que tenga ssl y unknow que es la unia que no tiene echo
![[Pasted image 20260403184054.png]]
hacecmos un echo para que diga nuestra contraseña y usamos el comando ssl con el puerto que dijimos y ponemos -quiet para que vaya a la informacióon directa
![[Pasted image 20260403184134.png]]
finalmente nos da nuestra llave de identidad
y para usarla para el siguiente nivel la copiamos, creamos una copia en nuestro escritorio y le damos permisos con chmod
![[Pasted image 20260403184222.png]]