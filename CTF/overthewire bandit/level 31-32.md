There is a git repository at `ssh://bandit31-git@bandit.labs.overthewire.org/home/bandit31-git/repo` via the port `2220`. The password for the user `bandit31-git` is the same as for the user `bandit31`.

From your local machine (not the OverTheWire machine!), clone the repository and find the password for the next level. This needs git installed locally on your machine.

Para resolver este nivel ejecutamos el Readme y nos va a decir que hay que crear una key y hacer un push a la branch master
![](../../../images/Pasted%20image%2020260408215831.png)
Primero creamos la key con un nano key.txt y dentro ponemos el contenido
y hago un `git add -f key.txt` (el -f para que el gitignore nohaga problemas), pero al momento de hacer el commit nos da un problema ya que no tenemos un usuario de donde subirlo
![](../../../images/Pasted%20image%2020260408220051.png)
Entonces vamos a crear un usuario temporal, despues volver a subir el archiv y hacer un git commit con la informacion de lo que hicimos, despues de eso hacer un push
con `git push origin [branch de destino]`![](../../../images/Pasted%20image%2020260408220205.png)
y por ultimo nos va a dar la contraseña pero nos va a rechazar el push 
![](../../../images/Pasted%20image%2020260408220411.png)

