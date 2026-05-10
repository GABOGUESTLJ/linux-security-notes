``` bash
Username: natas5
URL:      http://natas5.natas.labs.overthewire.org
```
Para resolver este nivel lo que vamos a hacer es empezar a analizar las cookies, vamos a iniciar sesión, y ver que nos dice como primer paso y vamos a usar el verbose para obtener mas info, es decir el -v
![](../../../images/Pasted%20image%2020260414161629.png)
Nos da esta cookie, nos dice que esta cookie que es el loggin nos da 0 que es falso, lo que vamos a hacer es cambiar su valor a 1 para que nos de verdadero, vamos a hacer uso de la flag -b que viene de bun, lo que hace es enviar datos al servidor por medio de las cookies
![](../../../images/Pasted%20image%2020260414162005.png)
hacemos uso del flag y nos da la contraseña que es: ==0RoJwHdSKWFTYR5WuiAewauSuNaBXned==
También se puede editar desde el web browser
![](../../../images/Pasted%20image%2020260414162428.png)
