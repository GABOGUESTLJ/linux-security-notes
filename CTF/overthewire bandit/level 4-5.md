La contraseña del siguiente nivel se almacena en la única que puede ser legible por humanos Archiva en el Directorio **Inhere**. Consejo: si tu terminal está dañado arriba, prueba el comando "reiniciar".

Pare resolver este nivel, lo que debemos hacer es revisar el directorio ![](../../../images/Pasted%20image%2020260325123231.png)
después de ver el directorio, vemos que tenemos más de un archivo y revisar todos los archivos uno por uno para ver cual es el que tiene el archivo nos resultaría contraproducente 
entonces hacemos uso del comando find, en este caso usamos el:
find `./*` , esto nos permite ver todos los archivos visibles y en un ejemplo que erramos ver los invisibles usamos el `./.*` 
![](../../../images/Pasted%20image%2020260325123733.png)
en este caso nos filtro solo un posible resultado que esta en ascii, digamos que tenemos mas de 1000 archivos, usamos el comando pero todavía nos quedan 50 con ascii y queremos filtrar solo los de asciii hacemos uso del comando grep para quitar el ruido visual del resto de archivos y filtrar solo los que necesitamos con el comando `file ./* | grep "ASCII text"`
y bueno en este caso ya solo usamos el cat sobre el archivo y nos da la contraseña
![](../../../images/Pasted%20image%2020260325124035.png)
