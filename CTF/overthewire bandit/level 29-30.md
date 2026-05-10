
Para resolver este nivel, hacemos lo mismo que las anteriores veces, clonamos el repositorio de github  usando el git clone, despues de eso, leemos el readme
![](../../../images/Pasted%20image%2020260408212828.png)
Dice que no hay una contraseña n producción, intento hacer un git show, pero no hay nada en contraseñas![](../../../images/Pasted%20image%2020260408212904.png)
Entonces decido irme a otras ramas para saber si no subieron la contraseña en una rama colateral
usando el comando `git branch -a` (para ver todas las ramas)![](../../../images/Pasted%20image%2020260408213047.png)
y ahi mismo decido cambiar a otra rama que es la dev con `git checkout [ruta]` y hago un git show para ver si esta la contraseña
![](../../../images/Pasted%20image%2020260408213152.png)

