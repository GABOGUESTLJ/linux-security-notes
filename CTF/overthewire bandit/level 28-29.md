There is a git repository at `ssh://bandit28-git@bandit.labs.overthewire.org/home/bandit28-git/repo` via the port `2220`. The password for the user `bandit28-git` is the same as for the user `bandit28`.

From your local machine (not the OverTheWire machine!), clone the repository and find the password for the next level. This needs git installed locally on your machine.

Para resolver este nivel, primero clonamos el repositorio usando el git clone, despues de eso leemos el readme, pero nos damos cuenta que las credenciales no están completas,


![](../../images/Pasted%20image%2020260408212032.png)


entonces para resolver esto primero vemos el git log, para ver que nos dicen los registros 

![](../../images/Pasted%20image%2020260408212102.png)


yo aquí me doy cuenta de que hay un fix info leak, es decir que arreglaron algo, entonces voy a hacer uso del comando git show, que me va a servir para ver cual fue el cambio


![](../../images/Pasted%20image%2020260408212204.png)


y nos damos cuenta que aquí esta la contraseña
