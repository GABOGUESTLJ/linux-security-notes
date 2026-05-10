Para resolver este nivel primero identificamos que es un formulario y nos deja ver el código fuente, veamos que es lo que tiene
``` php
<?  
  
$encodedSecret = "3d3d516343746d4d6d6c315669563362";  
  
function encodeSecret($secret) {  
    return bin2hex(strrev(base64_encode($secret)));  
}  
  
if(array_key_exists("submit", $_POST)) {  
    if(encodeSecret($_POST['secret']) == $encodedSecret) {  
    print "Access granted. The password for natas9 is <censored>";  
    } else {  
    print "Wrong secret";  
    }  
}  
?>
```
En este caso tenemos esto y lo que vamos a hacer es revisar paso a paso que es lo que tiene
primero nos damos cuenta que tiene una función llamada encodeSecret, nos dice que nos regresa bin2hex, string reverse y base64 codificado, para encontrar la contraseña original debemos revertir todo eso, en este caso hacemos
``` bash
echo"3d3d516343746d4d6d6c315669563362" xxd -r -p | rev | base64 -d
```
lo que hace esto es revertir aquel palabra con hex2bin ya que se usa la flag -r, se usa el rev para volver a poner el string normal y se decodifica el base64, entonces ahora el resultado que nos de, debemos ponerlo en el formulario con un post, en este caso lo que nos dio fue `oubWYf2kBq`
Y para hacer el post usamos el siguiente comando
``` bash
curl -v -u natas8:xcoXLmzMkoIP9D7hlgPlh9XD70gLAe5Q -d "secret=oubWYf2kBq&submit=submit" http://natas8.natas.labs.overthewire.org
```
Y la contraseña que nos dio fue esta: ZE1ck82lmdGIoErlhQgWND6j2Wzz6b6t

---
Para resolverlo en burpsuite, debemos hacer todo igual hasta este paso
``` bash
echo"3d3d516343746d4d6d6c315669563362" xxd -r -p | rev | base64 -d
```
Después de eso, vamos a copiar el texto que nos da y vamos a hacer el trabajo en burpsuite
Primero vamos a capturar la petición de envío del formulario, y vamos a seleccionar, send to Repeater
![](../../../images/Pasted%20image%2020260415191430.png)
Despues de eso, en Repeater![](../../../images/Pasted%20image%2020260415191508.png)
En la línea de secret vamos a pegar nuestro código y le damos a send, despúes de eso nos va a decir nuestra contraseña
![](../../../images/Pasted%20image%2020260415191552.png)
