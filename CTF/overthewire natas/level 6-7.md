Para resolver este nivel lo primero que ddebemos hacer es ejecutar un curl, lo ejecuto y me doy cuenta que una pista que nos dieron es que laas contraseñas suelen estar en una ![[Pasted image 20260415144801.png]]
entonces para resolver esto nos fijamos que en la url de la página web cambia dependiendo si ponemos en about o en home
![[Pasted image 20260415144912.png]]
con esto tenemos una pista de como progresar, simplemente vamos a hacer un curl, pero con la direccion cambiate y despues del = vamos a poner la direccion que nos suministró el comentario
![[Pasted image 20260415145051.png]]
y abajo nos da la flag
![[Pasted image 20260415145125.png]]
xcoXLmzMkoIP9D7hlgPlh9XD7OgLAe5Q

---

Para resolverlo a través de burpsuite, primero activaremos burpsuite y vamos a crear una petición dando click a la parte de la pagina donde dice about o home, solo para activar la petición
![[Pasted image 20260415152824.png]]
Ahora seleccionamos esta petticion y vamos a el apartado de repeater o ctrl+r
![[Pasted image 20260415152351.png]]
y nos vamos a dar cuenta que nos lanza info detallada sobre la petición, y para saber sobre que es lo que debemos hacer, o podemos hacerlo segun el curl, ya que nos dijo la dirección donde se encuentra la contraseña o le podemos dar a send y nos va a mostrar el código y vamos a ver la pista
![[Pasted image 20260415151940.png]]

![[Pasted image 20260415153109.png]]
Después de esto vamos a cambiar la petición, para editarla
![[Pasted image 20260415152311.png]]
Al editarla y darle send nuevamente podremos ver la contraseña sin censura 
![[Pasted image 20260415152335.png]]


