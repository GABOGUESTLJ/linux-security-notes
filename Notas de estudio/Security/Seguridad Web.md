### 🔹Web browser
El web browser es un interprete de código que recibe tres cosas principalmente, el html que es la estructura , el css que es el diseño y el js que es la lógica, esta se usa con el F12 en el navegador
#### Pestaña network
Mira los archivos que pide el servidor, a veces puede llegar a cargar archivos js y php que no debería

#### Pestaña Storage/Application
Aquí viene una parte muy importante que son las cookies, por ejemplo, si yo cambio una cookie que diga, user=user a user=admin voy a poder saltarme toda la seguridad
#### View Source (Ctrl+U)
Nos muestra el codigo HTML, donde se pueden ver ciertos comentarios que los programadores olvidan borrar

### 🔹cURL(Client URL)
Es un programa de línea de comandos que habla casi cualquier protocolo (HTTP, HTTPS, FTP, etc.), a diferencia del web browser el curl no ejecuta Js ni oculta headers, se puede usar cuando el navegador te bloquea, quieres automatizar o si un sitio web prohíbe el uso del click derecho, curl es mu eficaz para estos casos debido a que ignora el Js
#### Sintaxis general
`-u user:password : Para autenticación básica
`-I`: Para ver solamente los headers, el servidor te dice que software usa y si tiene vulnerabilidades conocidas
`-X POST -d "param=valor"` : Para enviar datos a un formulario sin usar el teclado
Su sintaxis es `curl [opciones] [url]`
`-b` : Sirve para enviar una cookie, se suele usar para escalar privilegios
`-c` : Sirve para guardar una cookie, se suele usar para mantener sesiones activas
### 🔹ZAP proxy/Burp Suite
Es una herramienta de manipulación de parámetros, se podría definir como un servidor intermediario por donde pasa toda la información antes de salir a internet.
#### Funciones
- Intercept
  Pausa la petición en el aire, se puede llegar a usar para cambiar el precio de un producto de un valor de $100 a $1 antes de que llegue al servidor.
- Repeater/Resend
  Se usa cuando por ejemplo se quiere probar 100 variaciones de una contraseña, no se recarga la pagina 100 veces, solo se captura la petición y se le da a "Enviar" cambiando solo la password
- Intruder/Fuzzer
  Automatiza el ataque y por ejemplo si se le llega a dar una lista de 1000 usuarios, este lo prueba todos en segundos

### 🔁OR-XOR/Cifrado de datos
#### OR
Para entender el comando XOR, tenemos que saber primero el comando OR
El comando OR=O
se define con el símbolo || , una forma rápida de ver el OR es con booleanos 1 para verdadero y 0 para falso, el Or se podría considerar como si al menos uno de los valores es 1 va a dar 1, pero si ambos son 0 va  a dar 0
0 || 0 = 0
1 || 0 = 1
1 || 1 = 1
0 || 1 = 1
#### XOR
El comando XOR se define con el símbolo ^, la forma mas fácil de distinguirlos sería, Si ambos valores son diferentes es True, si ambos valores son distintos es False
1^ 1 = 0 - T^ T = F
0^ 0 = 0 - F^ F = F
1^ 0 = 1 - T^ F = T
0^ 1 = 1 - F^ T = T
#### XOR en criptografía
La criptografía y xor funcionan de una manera muy interesante, XOR se puede usar con cualquier tipo de dato debido a que, los Strings se pueden transformar a un código binario, para empezar en la criptografía y XOR lo primero que debemos tener en cuenta es que el texto que nosotros cifremos debe ser comparado con una clave totalmente aleatoria y única, no se puede volver a repetir ya que para un atacante con resolver una vez el código para desencriptar le sería fácil vulnerar el mensaje, entonces se hace un XOR por cada 0 o 1 del código binario y la clave aleatoria
por ejemplo queremos encriptar el mensaje "hi", la manera más segura de hacerlo sería letra por letra, teniendo en cuenta estos conceptos empezamos
h=01101000 
i= 01101001 
hi=01101000 01101001 
clave aleatoria= 01101111 01110000 
![](../../../images/Pasted%20image%2020260419141122.png)
``` zsh
código encriptado = 0000011100011001
```
##### one time pad
Este tipo de forma de encriptar claves es muy solido pero tiene una desventaja que es que necesita claves igual de grandes que el mensaje a encriptar, aquel ejercicio que resolvimos es la forma de como funciona el one time pad, pero a pesar de que se ve muy fácil de vulnerar, se necesita saber la clave aleatoria y esta misma es aquella que la hace una defensa irrompible, ya que al ser aleatoria y de uso único es imposible dejar rastro de la clave  
##### Crib-Dragging
Es la forma de romper códigos mal cifrados de XOR, usando diccionarios de palabras comunes, siempre y cuando la clave del OTP no sea única y sea reutilizada se puede castigar vulnerándola con el crib dragging

### 🌟Magic bytes
Son los primeros bytes de un archivo utilizados para identificar su formato y tipo independientemente de su extensión, son firmas hexadecimales invisibles al abrir un archivo, 
#### Ejemplos comunes
- **PDF:** `%PDF` (Hex: `25 50 44 46`).
- **PNG:** `‰PNG` (Hex: `89 50 4E 47`).
- **ZIP:** `PK` (Hex: `50 4B 03 04`)
- JPG (Hex: `FF D8 FF E0`)
#### Base de dos conceptos fundamentales
##### Falsificación de archivos(Mime-type-spoofing):

##### Null Byte injection:
Este ataque consta de poner los caracteres %00 para truncar cadenas de texto y engañar a las aplicaciones, esto sirve en sistemas backend que vienen de C/C++ o Sistemas PHP antiguos sobre todo aunque todavía puede llegar a fallar en los actuales, 
Un ejemplo de este ataque es insertar un archivo `exploit.php%00.png`, este llega al servidor como un archivo php pero se hace pasar por un png para este mismo y para la validación, 
Otro ejemplo sería el Path traversal(lectura de archivos), por ejemplo, insertamos un `image.php?file=/etc/passwd%00` y este puede llegar a forzar a la aplicación a leer archivos del sistema en lugar de ir a la imagen,
Otro ejemplo sería para el famoso inject SQL, se puede llegar a usar un `%00 '1=1'` Para terminar una consulta de SQL prematuramente, 
De las mejores formas para mitigar este ataque es bloquear los caracteres problemáticos como %00, detectar y bloquear el %00 en request, usar lenguajes actualizados
## 🚧 En progreso
### Tipos de cifrado
- RSA
- OTP

### Como funciona TLS

- Como funciona su cifrado
