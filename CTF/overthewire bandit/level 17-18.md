There are 2 files in the homedirectory: **passwords.old and passwords.new**. The password for the next level is in **passwords.new** and is the only line that has been changed between **passwords.old and passwords.new**

Para resolver este nivel lo que hice fue hacer uso del comando diff, nos dice que la contraseña esta en el archivo new pero y es la unica linea que ah cambiado entre el new y el old, entonces 


![](../../images/Pasted%20image%2020260403230555.png)


hago uso de este comando, hago diff, pongo el old y diferenciar del new que es en el que esta, usando el grep con > ya que es la única linea diferente 