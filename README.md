# Snow-Crash
Snow-Crash is a Capture the Flag project at 42 school. The goal is to develop practical skills in information security and logical thinking.

Level00

Iniciamos maquina blablabla. Una vez esta todo bien configurado y nos hemos ubicado en el el home del user level00 lo que haremos sera buscar los archivos que pertenezcan al usuario flag00. Lo haremos utilizando el comando ```find / -user flag00 2>/dev/null```. Esto nos devolvera la ruta de una archivo y si hacemos cat a ese archivo nos aparece lo siguiente. ```cdiiddwpgswtgt```. Si probamos esta contraseña para el usuario flag00 no funciona. Bueno, porque esta encriptada y hay que desencriptarla :/ pero para nuestra suerte solo esta encriptada utilizando un algoritmo cesar pocho asique no necesitaremoss JohnTheRipper ni nada asi, en esta pagina podemos desencriptarlo https://www.dcode.fr/caesar-cipher o incluso con algun script propio se podria hacer facil. Conclusion, una vez desencriptamos nos devuelve ```nottoohardhere```. Es la contraseña del user flag00. Accedemos y hacemos uso del comando getflag.

Level01
