
Para resolver este nivel lo que debemos hacer es primero analizar que es lo que tenemos![[Pasted image 20260414164742.png]]
Nos damos cuenta que tenemos un formulario, con un input, que su nombre es secreto y submit que es submit, entonces nos interesa encontrar cual es el secreto, por suerte en este nivel tambien nos damos cuenta que nos deja una vista hacia el codigo fuente, que se encuentra en index-source.html, podriamos acceder a esa direccion con un curl -u user:host link/index-source.html, pero en este caso yo accedí desde la web, 
![[Pasted image 20260414165110.png]]
Nos da estas lineas de php, que nos dice que la contraseña esta en includes/secret.inc
![[Pasted image 20260414165150.png]]
Encontramos cual es el nombre del secret y lo que nos queda es hacer un post desde el formulario
![[Pasted image 20260414165247.png]]
Para hacer el post es algo interesante ya que usaremos la flag -d, y nuestra sintaxis para este caso de hacer el post sería secret=la contraseña que encontramos, ponemos un & ya que tenemos que poner otro parámetro mas que seria submit=submit entonces nos suelta la contraseña al final de todo
``` bash
url -v -u natas6:0RoJwHdSKWFTYR5WuiAewauSuNaBXned -d "secret=FOEIUWGHFEEUHOFUOIU&submit=submit" http://natas6.natas.labs.overthewire.org
```
y la contraseña es: bmg8SvU1LizuWjx3y7xkNERkHxGre0GS