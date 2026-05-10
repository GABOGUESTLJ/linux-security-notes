The password for the next level is stored in the file **data.txt** in one of the few human-readable strings, preceded by several ‘=’ characters.

Para resolver este nivel primero hay que tener en cuenta que el archivo original tiene algunos simbolos en binario, por lo tanto no es legible para los humanos y hay que hacer uso del comando strings y nos dice que para encontrar la contraseña entre todo eso, tiene simbolos de "=" a su lado, entonces para construir el comando yo lo hice de la siguiente manera
`strings data.txt | sort -r | uniq -u | grep " =="`, aunque tambien sirve solo con hacer el comando
`strings data.txt | grep "=="`
![[Pasted image 20260328121708.png]]
![[Pasted image 20260328121717.png]]
el primero lo hice yo por que no sabia si iban a haber repetidas y por eso el uniq y el sort para organizar.