- `PWD`= muestra donde está localizado el usuario 
	![](../../../images/Pasted%20image%2020260316133823.png)
- `ls` = muestra los archivos![](../../../images/Pasted%20image%2020260316134016.png)
- `cd` = cambia de directorio
	- `cd ..` = Sale de la carpeta actual a la anterior![](../../../images/Pasted%20image%2020260316134047.png)
- `mkdir` = crea directorios
		Para crear ficheros que no existan dentro de otros fiecheros se usaa el -p antes del definir la ruta![](../../../images/Pasted%20image%2020260321105358.png)
- `cat` o `touch`= crean archivos
	- Con nano se puede ingresar al editor de texto de ese archivo
	- Con Echo se puede escribir antes de crear el archivo, por ejemplo
	  `echo"Hola mundo" > practica.txt`![](../../../images/Pasted%20image%2020260316134601.png)
- `man [comando]`= nos brinda una guía del comando
- `rm` = Elimina archivos
	- Ejemplo= `rm prac.txt`![639](../../../images/Pasted%20image%2020260316134823.png)
	- Para eliminar ficheros se usa el -r
	- ![](../../../images/Pasted%20image%2020260321105503.png)
	- en el ejemplo anterior como solo se define la ruta de origen y no una subruta se elimina todo el contenido de la ruta
- Rutas absolutas y relativas
	- Absoluta= es trazar la ruta a la que nos vamos a dirigir desde el directorio raíz, 
		ejemplo= `/home/carpeta1/carpeta2/carpeta3`, siempre va iniciar con una barra
	- Relativo = es trazar la ruta a la que nos vamos a dirigir desde el directorio en que ya estamos, por ejemplo, ya nos encontramos en carpeta 1= `/carpeta2/carpeta3`, puede iniciar con la palabra, no necesariamente con una barra siempre y cuando este el dentro del directorio
	- Para pasar de un directorio a otros directorios anteriores se puede hacer `cd../../..`, **cada doble punto significa una carpeta anterior**
	- Para crear carpetas con un espacio en el nombre se deben usar las comillas dobles![](../../../images/Pasted%20image%2020260316141845.png)
	- Cursores: con CTRL + R se puede hacer una búsqueda recursiva de instrucciones que hemos realizado
	- Comando **history**: lo que hace este comando es mostrar el historial de instrucciones, para ver que es lo que hemos hecho
	- ! numero: esto lo usamos después del **history** para ejecutar x instrucción con ese numero que nos muestre el comando
	- mv: este comando sirve para mover archivos a otros directorios, por ejemplo:![](../../../images/Pasted%20image%2020260321110612.png)
	- Lo que podemos ver en este ejemplo es que se necesitan dos parametros
	- mv [archivo] [ruta] , en este caso podemos decir que la ruta debe ser absoluta
	- con mv tambien se pueden cambiar los nombres de los ficheros![](../../../images/Pasted%20image%2020260321110943.png)
	- con el argumento mv [nombre original] [nombre editado]
	- tambien se pueden mover directorios
	- ![](../../../images/Pasted%20image%2020260321111332.png)
	- ==**comando sort:**== el comando sort permite ordenar  el contenido de un texto, por default va a ordenar alfabéticamente y con el argumento `-n` va a ordenar numéricamente , el comando es `sort archivo.txt` , para ordenar inversamente se hace con el argumento -r, `sort -r archivo.txt`, para eliminar los elementos duplicados se usa el comando -u, `sort -u archivo.txt > archivo_sin_duplicar.txt`, para guardar la lista ordenada se usa el comando, `sort archivo.txt > archivo_ordenado.txt` ,  para ordenar por columnas especificas se usa el `-k`, por ejemplo, tenemos![48](../../../images/Pasted%20image%2020260327195515.png), y queremos filtrar solo la edad , lo que hacemos es `sort -k 2 archivo.txt`, ya que lo que buscamos es la segunda columna
	- ==**Comando uniq:**== lo que hace este comando es eliminar lineas duplicadas de un archivo
	- los argumentos más comunes son:
	  - `-c`: Muestra el número de ocurrencias de cada línea duplicada.
    
	- `-d`: Muestra solo las líneas que están duplicadas.
    
	- `-u`: Muestra solo las líneas que son únicas (no duplicadas).
    
	- `-i`: Ignora las diferencias entre mayúsculas y minúsculas al comparar líneas.
	  
	- Su sintaxis es `uniq lista.txt`
	- se recomienda usar el sort antes del uniq para tener todo ordenado antes de eliminar archivos, `sort archivo.txt | uniq
	- ==**Comando strings:**== el comando strings busca caracteres imprimibles de archivos binarios
	- su sintaxis es: `strings archivo.bin`, esto permite mostrarlo por consola, para guardarlo dentro de un archivo, lo que hacemos es `strings archivo.bin > archivo.txt`, 
	- ==**Comando base64:**== este comando sirve para codificar y decodificar 
	- ![](../../../images/Pasted%20image%2020260327201519.png)
	- y para decodificar un archivo se usa el parámetro -d
	- ![](../../../images/Pasted%20image%2020260327201623.png)
	- **==Comando tr:==** el comando tr sirve para remplazar caracteres y eliminación de caracteres, se puede usar el argumento `-d` para eliminar caracteres especificos, para eliminar los caracteres repeticos se usa el arumento `-s`, 
	- ejemplos:
	- echo "hola mundo" | tr 'a-z' 'A-Z' : este comando imprime "HOLA MUNDO"
	- echo "hola mundo" | tr -d 'o' : este comando imprime "hla mund"
	- echo "hola mundo" | tr 'ao' '12' : este comando imprime "h2l1 mund2"
	- echo "holaa mundooo" | tr -s 'ao' : este comando imprime "hola mundo"
	- para el comando tr tenemos tambien un caso especial que es rotar las letras, es decir sustituir tantas posiciones en el alfabeto, si queremos moverlas 13 posiciones, lo que debemos hacer es construir el comando
		- `tr 'A-Za-z'`(este primero es el tr y dice, todas las letras mayúsculas y minúsculas) 'N-ZA-Mn-za-m' (dice que inicie por la letra N hasta la Z y después que siga con la A hasta la M e incluyendo los casos de las minusculas)
- ==Comando tar:== este comando sirve para juntar distintos archivos en uno solo  
-  existen diferente argumentos que se les puede poner como son
#### Acciones principales

	- c : Crea un nuevo archivo de un archivo, es decir un paquete
	- t : Lista el contenido de un archivo, para saber que hay dentro
	- x : Sirve para extraer el contenido de un tar
#### Modificadores para comprimir

	- z: Sirve para filtrar archivos gzip, util para archivos .tar.gz o .tgz
	- j: Sirve para filtrar archivos bzip2, util para archivos. tar.bz2
#### Modificadores de control

	- v : Muestra en pantalla la lista de archivos que se estan procesando 
	- f : Indica que el siguiente argumento es el nombre del archivo(es de suma importancia ponerlo al final de las instrucciones y es el mas importante)
	- C : cambia a un directorio especifico antes de realizar la operación

notas extra:
el bzip2 comprime mas los archivos pero usan mas recursos
el usar gzip comprime los archivos pero si tienes mas de un archivo comprime uno a uno, por ejemplo a.gzip, b.gzip
si se usa tar solo, lo que haria es crear un archivo con n archivos que se solicitaron peor tendria el peso sumado de todos eso archivos
para solucionar eso se haria un tar czf archivo_comprimido.gz

Comando xxd: Este archivo sirve para ver el contenido de un archivo hexadecimal
tiene diferentes argumentos,
`xdd archivo`, muestra el archivo en columnas 
-c : define cuantos bytes se muestran por linea : xxd -c 8 archivo
-l : solo muestra los primeros bytes del archivo: xxd -l 32 arcchivo (se usa por lo general para ver   su encabezado)
-g : agrupa los bytes, por defecto es 2: xxdd -g 1 archivo : ff 00 a1
-p: No muestra columnas extra, solo muestra el codigo hexadecimal
-b: En lugar de hexadecimal lo muestra en binario
-i : genera una salida en formato de matriz en lenguaje C
-r : revierte un hexadecimal a binario(util para transformar una cadena de hexadecimal a por ejemplo "hola mundo")
==-p -r==: Hace la combinacion de p y r , lo que hace es solo mostrar el mensaje sin las columnas de descripcion extra y en lenguaje plano

### 🔹Comando SSH
El comando ssh se usa para conectarse de forma segura a un equipo o a un servidor de forma remota a través de la red su sintaxis es `ssh usuario@host`, de forma predeterminada el puerto ssh funciona en el puerto 22, existen diferentes argumentos:
`-p`: este argumento sirve para especificar el puerto
`-v`: Explica detalladamente la conexión, que es lo que pasa dentro de esta, lo que es la autenticación, intercambio de keys y la red, se puede obtener una explicación mas detallada con los comandos `-vv` y -`vvv`
`-i:` Este comando es muy importante ya que es como una llave de identidad, que al ponerla en el servidor al que vas a conectarte te deja ingresar sin más, esta supone un reto matematico que solo el archivo de identidad podrá resolver, su sintaxis es, `ssh -i key_file user@host -p port`, hay veces que el archivo key_file debe tener permisos restrictivos

### 🔹Comando SCP
El comando scp se usa para copiar archivos y directorios usando la encriptación y la autenticación de ssh para la seguridad, su sintaxis es `scp[args] /origen/de/destino`, existen diferentes argumentos:
`-P`(con mayuscula): este argumento especifica el puerto al que se va a conectar
`-i`: Sirve para lo mismo que con ssh, una llave para poder ingresar sin necesidad de una contraseña
`-r`: Se usa para copiar carpetas enteras con todo su contenido
#### Casos de uso:
	Dato extra: los dos puntos sirven para dividir, para saber que antes se esta hablando de una maquina y despues de otra
- Subir un archivo de la pc a un servidor
  `scp -P [port] [archivo] user@host : /ruta/de/destino`
- Subir un archivo del servidor a una pc, mas bien descargar el archivo del servidor
  `scp -P [port] user@host [archivo] : /ruta/de/destino`
- Uso de la llave de identidad para subir un archivo
  `scp -P [port] -i key_file [archivo] user@host : /ruta/de/destino`

### 🔹Comando umask
 El comando umask es un comando que define que permisos no se le van a otorgar a un archivo al momento de ser creador, para esto debemos tener en cuenta que los archivos cuentan con tres propiedades las cuales son, Write(escribir), leer(read), ejecutar(execute), estos tienen diferentes valores en el resultado octal
 Read, tiene el valor de 4
 Write, tiene el valor de 2
 Execute, tiene el valor de 1
 También para definir su valor octal que el máximo es 777, se tiene que tener en cuenta que representa cada posición del número, el primero representa el usuario, el segundo representa el grupo, y el tercero representa los usuarios externos
 Entonces para calcular el resultado del valor octal que le pondremos a nuestro archivo con umask, lo que debemos hacer es restar desde el valor octal máximo que sería 7
 En un ejemplo que queremos el valor octal de un archivo que tenga el permiso de editar, leer y ejecutar para el administrador, leer y ejecutar para el grupo y para los usuarios externos solo el poder ejecutar, lo que debemos hacer es lo siguiente
 User: (7)-(4+2+1) o 7-7=0
 Group:7-(4+1) o 7-5=2
 Others:7-1=6
 El valor de ese archivo sería 026, rwxr-w--x
 su sintaxis es `umask [valor]`

### 🔹Comando chmod
El comando chmod sirve para editar los permisos de un archivo ya creado, sigue los mismos principios de los permisos octales, solo que a diferencia de umask que se restan los valores, en este comando se suman, teniendo el mismo principio de
 Read, tiene el valor de 4
 Write, tiene el valor de 2
 Execute, tiene el valor de 1
 y que el número de permisos máximos es 777
 En un ejemplo que queremos el valor octal de un archivo que tenga el permiso de editar, leer y ejecutar para el administrador, leer y ejecutar para el grupo y para los usuarios externos solo el poder ejecutar, lo que debemos hacer es lo siguiente
 User: 4+2+1=7
 Group: 0+4+1=5
 Others: 0+0+1 =1
 El valor seria 751, rwxr-w--x
 Su sintaxis es `chmod [valor]` o  también `chmod+x` si se le quiere dar permiso de ejecución a un archivo o para evitar borrar un archivo por error y forzarlo, se puede hacer el uso de `chmod u-w` ya que dice que al usuario se le resta la posibilidad de escribir, ósea editarlo

### 🔹Comando cat
Es el comando que se usa por lo general para mostrar el contenido de un archivo, pero también se usa para concatenar archivos es decir unirlos, también para añadir contenido a un archivo, sus usos y su sintaxis:
1. Para concatenar archivos
   `cat [file1] [file2] > [combined_file]`
2. Para añadir contenido de un archivo a otro sin borrar lo anterior, el >> sirve para añadir algo nuevo y no sobrescribir, en este caso se añade la data nueva después del contenido del archivo1
   `cat [new_data] >> [file1]`
3. Crear un nuevo archivo desde la terminal
   `cat > [new_file]`
#### Argumentos
`-n`: enumera todas las líneas, se suele usar para saber donde esta el error de un script
`-A`: Muestra caracteres invisibles como lo son los saltos de líneas o tabuladores
`-s`: Comprime las líneas en blanco consecutivas en una sola

### 🔹Comando netcat
El comando netcat sirve para transferir archivos y escuchar en un puerto pero a diferencia de ssh es menos seguro y cualquiera puede interceptar estos datos, pero es más rapido, es usado en casos como archivos grandes pero no privados, puede ser usado en conexiones udp y tcp
#### Modos de operación
- Modo cliente(conectar)
  Su uso es conectarse a un servidor para que el servidor escuche y de n información, su sintaxis es: `nc [host] [port]`
- Modo servidor(escuchar)
  Su uso es para nosotros recibir la información, quedamos escuchando hasta que nos llegue la información, su sintaxis es
  `nc -l -p [port]`
#### Argumentos
`-l`: abre un puerto en nuestra maquina para recibir conexiones
`-p`: indica al puerto que nos vamos a conectar
`-z`: Solo verifica el puerto que está abierto sin enviar datos
`-v`: Nos da información detallada sobre la conexión, por ejemplo si la conexión se logro o si el puerto esta cerrado
`-u`: Usa el protocolo udp, en vez del tcp que es el estándar, el udp se usa sin conectar pero es mas propenso a ser inseguro
#### Casos de uso
- Transferencia de archivos
	- En la pc que envía
	  `nc -l -p [port] > [file]`
	- En la pc que recibe
	  `nc [IP] [port] < [file]`
- Escaneo de puertos
  `nc -zv [ip] [port 1]-[port n]`

### 🔹Comando install
El comando install sirve para copiar archivos pero permitiendo definir sus atributos de seguridad en un solo comando, a diferencia del cp, el cp cuando copia deja los mismos atributos de seguridad cuando se copia, con el install se pueden cambiar desde ahí mismo
#### Atributos
-m: Define los permisos en forma octal
-o: Define quien es el dueño(owner)
-g: Define el grupo
-d: Crea un directorio si no existe
#### Sintaxis
Su sintaxis es: i`nstall [atributos] [archivo] [destino]`
#### Ejemplos
Para copiar un archivo y modificar sus permisos, vamos a hacer un ejemplo con cp y uno con install
- Con cp
  `mkdir /dirección/definida`
  `cp file.sh /direccion/definida`
  `chmod 750 /direccion/definida/file.sh`
- Con install
  `install -m 750  -d /direccion/definida/` (así se crea una carpeta con permisos)
  `install -m 750 file.sh /direccion/definida` (se copia el archivo con permisos), para renombrar el archivo en el proceso se puede hacer de la distinta manera, 
  `install -m 750 file.sh /direccion/definida/file2.sh`

### 🔹Comando nmap
Este comando sirve para analizar puertos, para saber cuales estan abiertos y saber su información
sintaxis `nmap [arg] [port]`, si se usa el comando nmap solo, escanea los 1000 puertos mas comunes y en total existen 65535
#### Argumentos
-p: Sirve para analizar un puerto
-sV: Sirve para saber que programa corre dentro del puerto
-v: Da la información en tiempo real mientras escanea
-A: Detecta sistemas operativos, versiones y lanza scripts de diagnostico
#### Ejemplos
`nmap localhost` (dice que puertos estan abiertos en el servidor actual)
`nmap -p [port] -sV [host]` ( sirve para saber que corre detrás de un puerto)
`nmap -p [ port 1]-[port n] [host]` ( sirve para buscar backdoors)

### 🔹Comando OpenSSL s_client
Este comando a diferencia de netcat que es un tunel sin seguridad y rapido para el transporte de datos, es una libreria que se encarga de la seguridad de los archivos https y las keys rsa, las keys rsa constan de un sistema de criptografía que se basan en una llave privada y una publica, su dificultad de resolución se basa en la factorización de números gigantes 
#### Sintaxis
`openssl s_client -connect [host]:[port] [flags]`

### 🔹Comando diff
El comando diff permite ver aquel linea que es igual entre dos archivos
su sintaxis es, `diff [file1] [file2]`
El comando diff, nos da 3 opciones
"<" este nos da la primera linea del codigo
"---" Nos da los guiones es decir el intermedio entre los dos archivos
">" Nos da la linea que es diferente
para encontrar solo la linea diferente sin tanto ruido visual hacemos. 
`diff [file1] [file2] | grep ">"`

### 👁️SETUID
SetUid, es un permiso especial en los archivos de sistemas unix, igual que rwx, read,write,execute es una flag que puede cambiarse para los distintos usuarios, es algo parecido a sudo su, ya que le da permisos de administrador, en los permisos octales se vería de tal manera, si tenemos un owner con todos los permisos, grupo con ningún permiso y extras tampoco, 4700, ya que setuid tiene un 4 por defecto con casilla extra, cuando no esta el setuid por defecto se pone un 0, seria un rws------
### 👁️SETGID
A diferencia del setuid, es casi lo mismo pero este no es para el owner, es para el grupo, por lo tanto digamos en un ejemplo queremos darle permisos, escritura, lectura y ejecución al owner, lectura, ejecución y administrador al grupo y para los extra ni un permiso, quedaría tal que así 2750, rwxr-s---, ==como dato extra, la s sobrescribe la x ya que es ejecutar pero con permisos extra==

### 👁️Controles de trabajo
Los controles de trabajo son muy utiles para gestionar diferentes procesos
#### Controles
&: Este comando sirve para que el proceso siga corriendo de fondo después de ser ejecutado
CTRL-Z: Este comando sirve para pausar un proceso
jobs: Muestra los procesos corriendo en segundo plano
bg: Reanuda un proceso que se pauso con CTRL-Z
fg: Trae un proceso de fonddo para que se pueda interactuar con este
kill %1/kill%n: Mata el n numero de la lista de jobs
### 🔹Comando tmux
El comando tmux sin duda es un comando muy util, permite correr un proceso en dos terminales diferentes para hacer diferentes acciones dentro del mismo proceso
#### Comandos
Los comandos de tmux funcionan con el CTRL+B
Entonces el primero CTRL+B y despues usar el %, crea una terminal a los costados
CTRL+B y despues ", crea una terminal abajo, para saltar entre las consolas se usa el cotrl+B y despues las flechas, para ampliar el tamapño de esa terminal se usa el CTRL+B+flechas

### 🔹Comando crontab
El comando cron ejecuta scripts en intervalos de tiempo específicos
#### argumentos
-l: lista las tareas programadas
-e: edita el archivo
-r: remover todas las tareas del usuario
#### Como funciona?
Cada línea en un archivo crontab sigue orden de 5 asteriscos:
`***** [Comando a ejecutar]`
A continuación se explica cada uno de estos asteriscos
![](../../../images/Pasted%20image%2020260405134223.png)
#### Ejemplos
`*****`: Cada minuto de cada hora de cada día de cada mes
`00***`: Cada medianoche de cada día de cada mes, ya que dice, en el minuto 0 de la hora 0
`15****`: Cada cuarto de hora de la hora, es decir 1:15, 2:15, 3:15, ya que dice siempre al minuto 15
`*/15***`: Cada 15 minutos ya que dice, cualquier minuto pero cada 15 minutos de cada hora
`0 9-15 ***`: Cada hora a partir de las 9:00 hasta las 15.00
`*/5 9 ***`: Se traduce a cada 5 minutos desde las 9:00 hasta las 9:55

#### Directorios de almacenamiento
`/etc/crontab` : Archivo prinicipal
/etc/cron.d/ : Archivos de configuraciones de aplicaicones
/etc/cron.daily/ y /etc/cron.hourly/ : Aquellos que se ejecutan por intervalo
/var/spool/cron/crontabs/: Donde se guardan fisicamente los archivos de cada usuario

### El Concepto de Hash (MD5, SHA, etc.)
Un hash no es una contraseña, es una huella digital hecha por cálculos matemáticos, es fácil convertir una frase a Hash pero no viceversa, si es md5 siempre va a tener 32 caracteres
![](../../../images/Pasted%20image%2020260405141429.png)
Sus usos en la ciberseguridad es comprar el hash de un archivo descargador con el hash original para saber si este fue alterado por un atacante, sirve también para ocultar nombres de rutas

### Grep
`grep` es la herramienta definitiva para buscar patrones de texto dentro de archivos o salidas de comandos. Su lógica se basa en: **"Si coincide, muéstramelo"**.
#### Sintaxis
`grep [opciones] "patrón" [archivo]`
#### Flags
- **`-i` (Ignore Case):** Ignora mayúsculas y minúsculas. 
- **`-r` (Recursive):** Busca dentro de todos los archivos de una carpeta y sus subcarpetas.
- **`-v` (Invert Match):** Muestra las líneas que **NO** coinciden con el patrón.
- **`-n` (Line Number):** Muestra el número de línea donde encontró la coincidencia.
- **`-l` (Files with matches):** Solo muestra el nombre de los archivos que contienen el texto, no el texto en sí.
- **`-w` (Word):** Busca la palabra exacta (evita que "ana" coincida con "banana").
#### Trucos con grep
Grep puede buscar en diferentes archivos si se separan con un espacio
`grep "secreto" archivo1.txt archivo2.txt /etc/passwd`
#### Usos de comodines
- **`.`**: Coincide con cualquier carácter.
- **`.*`**: Coincide con absolutamente todo en una línea.
- **`^`**: Busca al inicio de la línea (Ej: `grep "^admin"`).
- **`$`**: Busca al final de la línea (Ej: `grep "error$"`).