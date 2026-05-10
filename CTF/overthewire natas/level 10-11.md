Para resolver este nivel lo que debemos tener en cuenta son algunos puntos claves, como lo son el XOR, como se usa para criptografía, ataque de texto plano, serialización de datos y un poco de php
Para empezar tendremos que tener en cuenta el código fuente, nos dice que tenemos un array llamado $defaultdata y nos da una pista clave de como resolverlo con lo que respecta al texto plano
``` php
$defaultdata = array( "showpassword"=>"no", "bgcolor"=>"#ffffff");  
  
function xor_encrypt($in) {    $key = '<censored>';    $text = $in;    $outText = '';    // Iterate through each character    for($i=0;$i<strlen($text);$i++) {    $outText .= $text[$i] ^ $key[$i % strlen($key)];  
    }  
  
    return $outText;  
}
```
también tenemos la parte de la cookie, donde vemos que esta está codificada a partir de data que sería nuestro array de arriba, base64, xor, y json encode
``` php
function saveData($d) {    setcookie("data", base64_encode(xor_encrypt(json_encode($d))));  
}
```
entonces para empezar a resolver este nivel debemos tener en cuenta primero esto, para resolverlo debemos seguir un orden con el xor
digamos que tenemos estas variables hipotéticas
``` php
$array_original = "nuestro primer array que nos dice que el password está en no"
$cookie_original = "Cookie que sacamos desde el web browser con el f12 en el navegador que tendremos que desencriptarla con base64 -d"
```
Para resolver esto tenemos que hacer uso del XOR
``` php
$array_original ^ $cookie_original = $key
```
Tenemos que tener en cuenta una propiedad del XOR que nos dice:
A^ B = C
C^ B = A
Entonces vamos a usar está lógica para encontrar nuestra key
Como segundo paso teniendo nuestra key, vamos a conseguir la nueva cookie teniendo en cuenta una nueva variable
``` php
$array_alterado = "Lo mismo que nuestro primer array pero cambiando el valor de no por yes, para poder acceder"
// Y vamos a hacer uso de la propiedad que mencioné anteriormente
$array_alterado ^ $key = $nueva_cookie;
```
Con eso vamos a conseguir nuestra nueva cookie, y ahora nos falta el ultimo paso y más importante, como recordaremos, en saveData, el código nos dice que tras estar con el json_encode y XOR encrypt, tambien tenia base64, asi que tendremos que ejecutar base64 sobre nuestra nueva cookie
``` php 
// vamos a hacer uso del base4
$cookie_final = base64_encode($nueva_cookie);
```
Entonces, teniendo la base de lo que vamos a hacer, tendremos que hacer un pequeño script en php para ejecutar todo esto, el script que yo hice quedo así
``` php
<?php
$json_original = json_encode(array("showpassword"=>"no","bgcolor"=>"#ffffff"));
$cookie_original = base64_decode("HmYkBwozJw4WNyAAFyB1VUcqOE1JZjUIBis7ABdmbU1GIjEJAyIxTRg=");
$key_completa = "";
for ($i=0; $i<strlen($json_original); $i++){
        $key_completa .= $json_original[$i] ^ $cookie_original[$i % strlen($cookie_original)];
}
$key_real = "eDWo";
echo "la key real es:" . $key_real;
echo "la key completa es: ". $key_completa;
// segundo paso, averiguar la nueva cookie
$new_cookie = "";
$json_alterado = json_encode(array("showpassword"=>"yes","bgcolor"=>"#ffffff"));
for($i=0; $i<strlen($json_alterado); $i++){
        $new_cookie .= $json_alterado[$i] ^ $key_real[$i % strlen($key_real)];
}
echo "la nueva cookie es: ". $new_cookie;
// base64 a la nueva cookie
$cipher_cookie = base64_encode($new_cookie);
echo "la ultima cookie es: ". $cipher_cookie;
?>
```
### Como puntos importantes para el código
Primero me gustaría mencionar el uso del % y como fue de gran ayuda para solucionar el problema del ataque de texto plano
Teniendo en cuenta que la key es "`eDWo`" y que el for inicia desde el caracter 0

| Paso(i) | Operación                   | Resultado                    |
| ------- | --------------------------- | ---------------------------- |
| 0       | $0 \div 4 = 0$, sobra **0** | `key` -> e                   |
| 1       | $1 \div 4 = 0$, sobra **1** | `key `-> D                   |
| 2       | $2 \div 4 = 0$, sobra **2** | `key` -> W                   |
| 3       | $3 \div 4 = 0$, sobra **3** | `key` -> o                   |
| 4       | $4 \div 4 = 1$, sobra **0** | `key` -> e                   |
| 5       | $5 \div 4 = 1$, sobra **1** | `key` -> D(vuelve a empezar) |
Otro punto que también me gustaría mencionar es el hecho de los espacios en los arrays de uso, un problema que tuve al hacer este ejercicio fue que el uso de los espacios cuando copie y pegue directamente el valor del array es que al ser un carácter, al momento de compararlo con la clave ya generada nos da un error de compatibilidad ya que se suman dos o tres espacios mas y eso cambia completamente la contraseña, entonces para resolver eso tuve que quitar los espacios
### Uso del curl para obtener la información
Esto es de lo más simple hasta el momento, solo es hacer un curl como los de siempre pero con la flag de  --cookie data= valor
``` bash
curl -u natas11:UJdqkK1pTu6VLt9UHWAgRZz6sVUZ3lEk --cookie "data=HmYkBwozJw4WNyAAFyB1VUc9MhxHaHUNAic4Awo2dVVHZzEJAyIxCUc5" http://natas11.natas.labs.overthewire.org
```

### Resolución en el navegador
![[Pasted image 20260422125836.png]]
### Password
``` bash
The password for natas12 is yZdkjAYZRd3R7tq7T5kXMjMJlOIkzDeB
```
