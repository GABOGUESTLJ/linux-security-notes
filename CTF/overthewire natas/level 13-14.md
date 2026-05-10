Para resolver este nivel tenemos que hacer un in band sql injection, se llama así ya que se recibe la respuesta en este caso la contraseña por el mismo canal por donde se envió
Primero analizo el código y me doy cuenta de esta línea de código
``` php
if(mysqli_num_rows(mysqli_query($link, $query)) > 0) {
```
y me doy cuenta del error, ya que el programador cometió el error de una hacer el intento de una verificación pero muy débil, ya que en este caso no verifica que la contraseña coincida, si se logra que la consulta sea verdadera siempre va a ser mayor a 0
Entonces para empezar a resolver este nivel vamos a analizar antes como se conforma la consulta de datos
``` php
 $query = "SELECT * from users where username=\"".$_REQUEST["username"]."\" and password=\"".$_REQUEST["password"]."\"";
```
Primer punto, me doy cuenta de que en esta consulta se van a usar las comillas dobles, entonces empecemos a hacer el inject
Para realizar este inject lo primero que hice fue poner el nombre de usuario que voy a buscar, que en este caso será natas15
`natas15" or "1"="1`, lo inserto en el campo con una contraseña cualquiera y la lógica me dice que si tiene una columna esta en lo correcto y me valida el bypass
#### Problemas que tuve al inicio
Un problema que tuve al inicio fue el hecho de que no entendía muy bien la parte de las comillas en el inject, pero en resumen están las comillas iniciales y finales y dentro pongo todo lo que debo de insertar pero sin que se llegue a cerrar la cadena de texto, sería algo así `(")natas15" or "1"="1(")`
