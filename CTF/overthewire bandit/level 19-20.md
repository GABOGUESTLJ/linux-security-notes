To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

Para este nivel debemos tener en cuenta el setuid, que es un estado de permiso absoluto, como nos damos cuenta cuando tiene uno?
Cuando hacemos ls-l y el owner tiene permisos rws, read,write,setuid, sobre todo cuando tena el s, en este caso accedemos desde el archivo bandit20-do, ya que tiene esos permisos de setuid y como owner el bandit20, entonces hacemos uso de este comando para tener la contraseña, recordando que las contraseñas de los bandit estan en bandit_pass
![](../../../images/Pasted%20image%2020260403232547.png)
