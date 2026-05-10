The password for the next level is stored in the file **data.txt**, which contains base64 encoded data

para resolver este ejercicio nos dice que la contraseña está codificada dentro del archivo data, entonces para resolver este ejercicio aplicamos este comando
`cat data.txt | base64 -d` , que en lenguaje humano sería, el contenido de data.txt decodificalo, ya que si usamos base64 solo va a codificar el texto ya codificado, pero si usamos -d lo vamos a decodificar
![](../../../images/Pasted%20image%2020260328122419.png)

