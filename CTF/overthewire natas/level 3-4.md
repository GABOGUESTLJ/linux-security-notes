
Para resolver este nivel nos damos cuenta que nos dice que no tenemos permitido ingresar a menos de haber venido de http://natas5.natas.labs.overthewire.org


![](../../images/Pasted%20image%2020260410150050.png)


Para resolver esto vamos a usar el referer, que se usa con el `curl -e`,  en si su sintaxis sería
`curl -u [user:password] -e "dirección de la que deberíamos venir" [dirección que estábamos intentando]`


![](../../images/Pasted%20image%2020260410150240.png)


La usamos y nos da la contraseña
La contraseña es: 0n35PkggAPm2zbEpOU802c0x0Msn1ToK