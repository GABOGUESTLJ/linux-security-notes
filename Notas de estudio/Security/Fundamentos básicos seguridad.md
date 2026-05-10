### Protocolos de red
### 🛜Las 4 capas del modelo TCP/IP --- Protocolos comunes

#### 📲Capa 4 Aplicación (servicio y datos)
##### Conexión y transferencia
- **SSH(Secure shell - puerto 22)**
	SSH establece una conexión entre el dispositivo de un usuario y una maquina lejana, utiliza encriptación para codificar los datos que atraviesan la conexión, usa la tunelización para transferir datos, funciona envolviendo paquetes de datos con información adicional,
	SSH se ejecuta sobre el conjunto de protocolo TCP/IP, es seguro ya que incorpora un proceso llamado criptografía de llave publica, dispone una clave publica que todo el mundo puede tener y una clave privada que solo tiene el usuario, cuando estas dos se relacionan entre si, dan acceso al usuario
- **FTP/SFPT/TFTP(21/22/69)**
	- **FTP(file transfer protocol)-puerto 21**
		El protocolo FTP funciona bajo la modalidad cliente servidor, donde el usuario(cliente) se conecta a un servidor remoto, el FTP tradicional no es seguro ya que transmite los datos en texto plano, se recomienda usar variantes seguras como FTPS o SFPT
	- **SFTP-puerto 22**
		Se basa en ssh y su mismo sistema, es mas fácil de configurar en firewalls, a diferencia de ssh que es un protocolo de transferencia y controla el servidor, este es un gestor de archivos que funciona sobre el protocolo ssh.
	- **TFTP-puerto 69**
		Es una versión simplificada del FTP, diseñada para ser muy ligera y rápida, a diferencia de FTP que usa TCP, TFTP usa UDP, esto lo hace más rápido pero no garantiza que los datos lleguen correctamente y también recalcar que su seguridad es inexistente debido a que no cifra los datos ni requiere usuario ni contraseña, por eso solo se debe usar en redes locales controladas
- **SMB(Server message block - puerto 445)**
	Hace uso del modelo cliente servidor, usa el protocolo RCP, permite el acceso compartido a archivos, impresoras y la comunicación entre procesos IPC y en LAN, en sistemas actuales su puerto es TCP 445 y en versiones antiguas con NetBios, se usa el UDP 137/138 y TCP 139, es fundamental para entornos Windows, pero es peligroso si se expone a internet.
	En cuestión de seguridad el puerto 445 ha sido objetivo de malware, por ejemplo **WannaCry/EternalBlue**, se recomienda bloquearlo en el firewall para evitar accesos desde internet y habilitar la firma SMB para proteger contra ataques de retransmisión.
	Es usada entre windows y linux a través de samba que es un sistema de que permite compartir archivos e impresoras entre sistemas Linux/Unix y windows
- SSL-VPN(443)
	Es un tipo de VPN que usa el protocolo SSL/TLS para crear un canal cifrado entre un usuario remoto y la red interna de una organización, a diferenncia de IPsec que trabaja desde la capa de internet, ssl/tls vive en la capa de aplicación, lo que hace que utilice el navegador web para autenticar el usuario y luego encapsular la información en paquetes HTT
##### Infraestructura y resolución
- DNS
	  DNS o Domain Name System funciona traduciendo nombres de dominios a direcciones IP numéricas que las maquinas utilizan para conectarse a la web sin recordar números complejos
- DHCP
	  DHCP o Dynamic Host Configuration Protocol, es un sistema que asigna automáticamente direcciones de IP, sub mascaras de red, puertas de enlace y DNS a dispositivos, Los pasos son, el cliente busca un servidor DHCP, el servidor ofrece una IP, el cliente acepta la oferta y por ultimo el servidor confirma y registra la IP, cabe aclarar que la ip asignada no es permanente, la cual tras pasar un cierto tiempo se renueva
##### Gestión y directorio
- SNMP(dispositivos)
		(Simple network management protocol) es un protocolo estándar que esta diseñado para monitorear, gestionar y supervisar el rendimiento de dispositivos de red, por ejemplo, routers, switches, servidores e impresoras,  funciona a través de UDP, tiene distintas versiones como lo son snmpv1 hasta la v3, la v3 es la más segura por ahora ya que tiene cifrado haxadecimal
- LDAP(identidad)
		(Lightway Directory Acces Protocol) es un protocolo de software abierto que permite gestionar buscar y autenticar usuarios, equipos y recursos dentro de una red
##### Correo
- SMTP(envío)
	  (Simple mail transfer protocol) Es el puerto estándar para enviar correos a través de internet, solo sirve para el envio de estos mismos, se encarga de transferir el mensaje desde la aplicación al servidor de correo
- POP3(recepción)
	  El protocolo pop3 lo que hace es recibir el correo y se descarga en el disco local para que se pueda ver sin conexión a internet y elimina los mensajes del servidor una vez descargados
- IMAP(recepción)
	  El protocolo IMAP lo que hace es recibir el correo pero este no se descarga si no que se guarda en la nube y permite ver reflejado en el servidor instantáneamente, cuando se borra o se edita
##### Web y bases de datos
- HTTP(80)
	  Significa(Hypertext transfer protocol) es el conjunto estándar utilizado en internet para trasmitir información entre un navegador(cliente web) a un servidor, como se dice anteriormente, este protocolo usa el modelo cliente servidor, permite el intercambio de HTML, imágenes, videos y otros recursos, usa métodos de petición de una API REST, que son get, post, put, delete
- HTTPS(443)
	  Significa(Hypertext transfer protocol Secure) es la versión segura de http ya que cuenta con protocolos de encriptación ssl(Secure Socket Layer)/tls(Transport Layer Security) para cifrar los datos enviados entre un navegador y un sitio web, evita ataques mitm donde los datos robados aparecen como caracteres sin sentido  
  
#### 📲Capa 3 Transporte (conexión)
##### TCP
	TCP(Transmission Control Protocol), es un estandar de comunicación en internet
	que garantiza la entrega fiable, ordenada y segura entre dispositivos, usa lo 
	que es un triple handshake, usa los siguientes pasos que son syn, syn-ack, ack
	Syn:Sincroniza
	Syn-Ack: el cliente responde
	Ack: Recibe
	Se utiliza antes del protocolo de enlace TLS para garantizar una conección
	 segura
##### UDP
	UDP(User Diagram Protocol) Es un protocolo de red que transmite los datos 
	enfocado en la rapidez más que en la fiabilidad, no necesita establecer una 
	conexión previa ni necesita hacer un handshake a diferencia de tcp, lo que 
	reduce drasticamente su latencia, es ideal para streaming, juegos en linea y 
	VoIP, es decir llamadas de voz, etc, un ejemplo para el VoIP es discord, 
	discord usa UDP para VoIP para llamadas, uno de los ataques mas comunes en UDP 
	son los ataaques DoS, ya que no hay quien verifique los datos

#### 📲Capa 2 Internet (direccionamiento y rutas)
##### IP
Es un protocolo sin conexión y no confiable, su única función es el direccionamiento y el enrutamiento, no necesita conexión, ya que sin importar si el objetivo está listo, va a enviar el paquete, no confiable hace referencia a que si un paquete se daña en el camino el protocolo simplemente lo descarga
- ### IPV4
  Da direcciones decimales de 32 bits ej (192.168.1.1), depende de NAT para compartir una IP pública lo que complica las conexiones punto a punto
- ### IPV6
  Da direcciones hexadecimales de 128 bits ej (2001:db8::1), estas se crean así ya que no hay mas direcciones ipv4, fue diseñada con IPsec, permite la autoconfiguración con (SLAAC) lo que significa que los dispositivos pueden generar su propia dirección IP sin necesidad de un servidor DHCP a diferencia de ipv4 que necesitaba ser configurada manualmente
- ### Anatomía de una dirección IP
  La subnet mask y CIDR son lo mismo pero expresado de diferentes formas, la IP se divide en **Red** y **Host**.
  Las IPs se pueden dividir en partes más pequeñas que es el subneting mask, el CIDR es la forma de dividir estas, dividirlas es fácil, dependiendo de en cuantas partes se pueda dividir, por ejemplo tenemos una ip: 255.255.255.0/24, primero tenemos que tener en cuenta que se puede dividir hasta un máximo de una dirección IPV4 son 32 bits, 255 es el valor máximo de un octeto pero dos de estas no son usables que son el 0 y el 255, el 0 que usa para referirse a la IP en si y el 255 que sirve para hacerse notar, es decir tenemos 254 disponibles, podemos ver cuantas podremos usar, con una formula fácil, primero de base ponemos el 2 y de exponente la resta de 32-[cuantos ya estaan ocupados, en este caso /24] que sería 2^8= 256, entonces podemos usar 254, en el caso que tengamos una IP:
  255.255.255.252/30 podríamos decir que solo tenemos dos IPs usables, esto sirve bastante en el ámbito de port scanning ya que en este caso no tenemos que escanear todo el rango, solo dos maquinas
- ### IPs especiales
  - 127.0.0.1:(Localhost/loopback)
	  - Muchos servicios como db o admin panel se configuran solo para ser accesibles solo por locahost
	  - En ataque muchas veces si se compromete una máquina si se revisa el localhost que seria 127.0.0.1 y el puerto 8080 esta libre se puede usar ssh para llevar ese puerto a otra maquina y encontrar la web, ya que este puerto lo suelen usar los devs para hacer practicas cuando el puerto 80 está ocupado, este es como un http alternativo pero no cifrado
  - 0.0.0.0(Unespecified Address)
	  -  Son todas las direcciones IP de la máquina local
	  - Si un servidor esta escuchando en esta dirección significa que es accesible desde la red local, es una backdoor
  - 192.254.X.X(Automatic Private IP Adressing)
	  - Es una IP que se asigna automáticamente cuando no encuentran un servidor DHCP
	  - Significa que esa máquina está aislada o el DHCP no tiene salida a internet, pero se puede atacar si te pones manualmente una IP en ese mismo rango.
  - IPs privadas
	  - 172.16.0.0 hasta 172.31.255.255 (Común en Docker/Contenedores)
	  - 192.168.0.0 hasta 192.168..255.255 (Usado en redes domésticas)
- ### Conceptos extra
  - TTL
	  - Es un valor que determina cuanto tiempo puede permanecer un paquete de datos en una red antes de ser descartado, su función principal es evitar que los paquetes circulen indefinidamente, optimizando el trafico de red, también usa DNS para definir la caducidad de un registro en el caché.
	  - Se puede saber el sistema operativo solo con un ping, por ejemplo
		  - TTL=64 El objetivo es linux o macos
		  - TTLJ=128 El objetivo es windows
		  - TTL=254 Es un objetivo en un Router/Switch
  - Gateway(Puerta de enlace)
	  - Traduce protocolos y gestiona el trafico de datos, mueve la información entre redes, permite el flujo de datos para que sistemas incompatibles puedan comunicarse
	  - Conecta una red LAN a una red WAN, a menudo se integra con firewalls para proteger las redes internas de amenazas externas
	  - En ataques de red local, se trata de convencer a la red local que es el gateway quien se quiere comunicar y que envíen todo el tráfico antes de que salga a internet
  - NAT(Network Address Translation)
	  - Permite que múltiples dispositivos en una red privada compartan una sola dirección ip publica para acceder a internet
	  - En ataques es vital entender el NAT, para el port forwarding, ya que si el objetivo esta detrás de un NAT, no se puede atacar directamente desde fuera, por lo cual necesitamos que se conecte a nosotros usando Reverse Shell

## 🚧 En progreso
##### IPsec

##### ICMP

#### 📲Capa 1 Acceso a red (Enlace físico y lógico)
##### ARP

#####  Protocolos de la capa 2 (Ethernet, WI-FI)


### Arquitectura
- Infraestructura 
- Proxy
- Infraestructura de nube


## Preguntas frecuentes/ a contestar

- cómo funcionan los servidores realmente
- cómo se administran sistemas sin entorno gráfico
- cómo se conectan máquinas en un data center
- qué rol cumple realmente un firewall en una arquitectura de red
- cómo se despliegan aplicaciones en infraestructura real
- qué significa escribir código mantenible
- y por qué entender los sistemas es más importante que saber herramientas