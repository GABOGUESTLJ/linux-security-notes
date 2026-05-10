The password for the next level is stored **somewhere on the server** and has all of the following properties:

- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

para resolver este ejercicio, hacemos algo parecido al ejercicio anterior, pero een este caso nos dice que puede estar en cualquier parte del servidor, no necesariamente en una carpeta, entonces para construir el comando lo que hago es
find (para encontrar lo que buscamos) /(como puede estar en cualquier lugar revisamos desde la carpeta raíz) - type f(necesariamente para un archivo f(file)) -size 33c(para el peso de 33bytes) -group bandit6(para el grupo que nos especifica de bandit 6) -user bandit7(para el usuario que nos especifica) 2>/dev/null
(
para explicar este ultimo comando tenemos que tener en cuenta que para la toma de errores existen 3 diferentes numeros
0 (stdin) = entrada de teclado
1 (stdout) =la salida, es decir lo que queremos ver
2 (stderr) = la salida de errores
entonces para construir el comando debemos de tener en cuenta que si ejecutamos el comando sin esta linea nos va a soltar muchos errores ya que no tenemos permiso para entrar a esos archivos


![383](../../images/Pasted%20image%2020260326232655.png)


entonces para construir el comando lo que hacemos es 
2(para filtrar los errores) >(para dirigirlos hacia la ruta) /dev/null(esta es una ruta que lleva a una especie de vacio que lo que entra se borra)
entonces traducirlo a idioma humano sería
la lista de errores dirígelas hacia un lugar donde no las vea, por lo tanto solo nos quedaría un resultado visible
)



![](../../images/Pasted%20image%2020260326232034.png)




![](../../images/Pasted%20image%2020260326233237.png)


