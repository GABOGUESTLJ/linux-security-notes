The password for the next level is stored in a file somewhere under the **inhere** directory and has all of the following properties:

- human-readable
- 1033 bytes in size
- not executable
para resolver este problema lo primero que hacemos es ver todos los archivos


nos muestra una lista de directorios y dentro de esos directorios hay archivos, para encontrar nuestro archivo con la contraseña lo que debemos hacer es un find
el find que usaremos es este:
`find . -type f -size 1033c -readable ! -executable`
find nos sirve para encontrar el archivo
. el punto nos dice de encontrar en este directorio ya que previamente accedimos al directorio
-type f: el -type es para el tipo de archivos y el f de files
-size 1033c para encontrar el archivo con el tamaño solicitado
-readable: nos especifica que sea legible
! -executable: el signo de exclamación significa una negación por lo tanto significa que no sea ejecutable


![](../../images/Pasted%20image%2020260326194130.png)





![](../../images/Pasted%20image%2020260326210900.png)



(anotación útil sobre los tamaños a buscar)


![](../../images/Pasted%20image%2020260326233729.png)

