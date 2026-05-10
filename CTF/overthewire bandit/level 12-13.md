```
The password for the next level is stored in the file **data.txt**, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)
```
Para resolver este nivel algo largo vamos a hacer lo siguiente
- Crear un directorio temporal para manejar los datos con `mktemp -d`
- copiar el `data.txt` a ese directorio para empezar a trabajar
1. Vamos a hacer uso del comando xxd para archivos hexadecimales, `xxd -r data.txt > bin`(esto nos permite trabajar con un archivo mas normal, ya no hexadecimal)
2. Vamos a usar el comando file para ver cual es el estado de nuestro archivo
	![](../../../images/Pasted%20image%2020260331212629.png)
3. Al estar en gzip, para trabajar con este necesitamos convertir su extensión haciendo uso del mv, `mv bin bin.gz`
	![](../../../images/Pasted%20image%2020260331212712.png)
4. ahora lo extraemos con el comando gzip, `gzip -d bin.gz` y del archivo que sale vamos a hacer un file para saber sus propiedades
    ![](../../../images/Pasted%20image%2020260331212923.png)
5. Nos percatamos que tiene una extension bzip2, lo que hacemos es lo mismo que lo anterior solo cambiando su formato, mv `bin bin.bz2` y despues lo extraemos con el comando bzip2, `bzip2 -d bin.bz2`
   ![](../../../images/Pasted%20image%2020260331213142.png)
6. Ahora nos dice que tenemos un archivo tipo tar, para extraer este archivo hacemos lo mismo de renombrarlo, mv bin `bin.tar`, y lo extraemos con el comando tar, `tar -xf bin.tar` y al extraerlo nos dice que hay un archivo llamado data5 con formato tar, asi que vamos a tener que repetir lo de cambiar el formato
   ![](../../../images/Pasted%20image%2020260331213336.png)
7. hacemos uso del comando mv, `mv data5.bin data5.tar`, después de esto hacemos uso del comando tar, `tar -xf data5.tar`, 
   ![](../../../images/Pasted%20image%2020260331213453.png)
8. ahora tenemos un archivo llamado data6, en formato bzip2, hacemos uso del mv, 
   `mv data6.bin data6.bz2`, después de eso hacemos uso del comando bzip2, 
   `bzip2 -d data6.bz2`, después vemos que archivo nos dio y hacemos uso del file para ver sus propiedades
   ![](../../../images/Pasted%20image%2020260331213731.png)
9. Ahora tenemos otro archivo llamado data6, pero esta vez en formato tar, hacemos lo mismo que lo anterior solo que cambiando la extensión, `mv data6 data6.tar`, `tar -xf data6.tar` y vemos que archivo nos soltó y hacemos uso del file
   ![](../../../images/Pasted%20image%2020260331213916.png)
10. El uso de este comando nos suelta el archivo data8.bin, con propiedad de archivo gzip, entonces hacemos uso del mv del gzip, `mv data8.bin data8.gz`, `gzip -d data8.gz`, y hacemos uso del ls para ver que archivo tenemos y cual es su formato
    ![](../../../images/Pasted%20image%2020260331214140.png)
11. Tenemos al fin un archivo ASCII que es texto normal, probablemente sea la contraseña, asi que hacemos uso del cat para saber si es y en efecto, es la contraseña
    ![](../../../images/Pasted%20image%2020260331214231.png)