# Snow-Crash
Snow-Crash is a Capture the Flag project at 42 school. The goal is to develop practical skills in information security and logical thinking.

Level00

Iniciamos maquina blablabla. Una vez esta todo bien configurado y nos hemos ubicado en el el home del user level00 lo que haremos sera buscar los archivos que pertenezcan al usuario flag00. Lo haremos utilizando el comando ```find / -user flag00 2>/dev/null```. Esto nos devolvera la ruta de una archivo y si hacemos cat a ese archivo nos aparece lo siguiente. ```cdiiddwpgswtgt```. Si probamos esta contraseña para el usuario flag00 no funciona. Bueno, porque esta encriptada y hay que desencriptarla :/ pero para nuestra suerte solo esta encriptada utilizando un algoritmo cesar pocho asique no necesitaremoss JohnTheRipper ni nada asi, en esta pagina podemos desencriptarlo https://www.dcode.fr/caesar-cipher o incluso con algun script propio se podria hacer facil. Conclusion, una vez desencriptamos nos devuelve ```nottoohardhere```. Es la contraseña del user flag00. Accedemos y hacemos uso del comando getflag.

FLAG00: x24ti5gi3x0ol2eh4esiuxias

Level01

cat /etc/passwd

aparece otra pass encriptada al lado del user flag01

![image](https://github.com/user-attachments/assets/54a0b7c0-677c-4a1e-92f2-d237be164388)

desencriptamos con johntheripper 

![image](https://github.com/user-attachments/assets/c63cc49d-f1ce-4a23-83e3-377c1f83e4ae)

la pass es: abcdefg

FLAG01: f2av5il02puano7naaf6adaaf

Level02

