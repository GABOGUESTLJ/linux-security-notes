The password for the next level is stored in the file **data.txt** and is the only line of text that occurs only once

Para resolver este ejercicio lo que se debe de haecr es hacer uso del comando sort y el comando uniq, entonces para construir este comando debeos hacer esto
sort data.txt | uniq -u que en lenguaje humano sería, analiza este archivo, y las lineas repetidas elimínalas 
![](../../../images/Pasted%20image%2020260328120250.png)
