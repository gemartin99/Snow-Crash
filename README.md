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

en la raiz del user vemos que solo hay un fichero .pcap 

![image](https://github.com/user-attachments/assets/82a6d9c7-bd3a-4c9c-bc3c-8b2a8d6a2921)

este fichero almacena datos capturados de una red. Este fichero suele ser generado por herramientas como WireShark, tcpdump etc. Yo utilizare wireshark para analizar el fichero. Para ello utilizare mi VM Kali linux. Entonces utilizaremos SCP para copiar el fichero de la maquina snowcrash a mi otra maquina virtual Kali Linux.

![image](https://github.com/user-attachments/assets/cff43b68-c9ac-44e3-b0e8-8a8448bc5f61)

Una vez tenemos el archivo en Kali pues abriremos Wireshark y analizamos el fichero, si nos fijamos en el paquete 43 aparece password. Lo que haremos sera darle click derecho en este paquete y le daremos a follow TCP stream para ver la secuencia entera

![image](https://github.com/user-attachments/assets/9049c234-6c9f-47dc-89d6-4ff7a5fbdb65)

Pues ya tendriamos la flag 

![image](https://github.com/user-attachments/assets/ccb105c7-8c58-4f2e-8ee6-f5c8395c4c26)

Peroooooo aqui hay que comentar algo , la contraseña no es con los . , eso son caracteres no printables que se ve asi por ser ASCII, si cambiamos los datos a C Arrays por ejemplo podemos ver exactamente los caracteres pero bueno que basicamente es la misma pass quitando los . 

![image](https://github.com/user-attachments/assets/f3c68cce-afeb-4837-8798-14481d42e75d)

La pass esta en Hexadecimal, si la analizamos vemos que los . eran caracteres eliminados, por lo que al escribir la pass se equivocaron y borraron algunos chars y eso nos despistaria. Bueno una vez tenemos la pass que es: ```ft_waNDReL0L``` entramos al user flag y hacemos el getflag.

FLAG02: kooda2puivaav1idi4f57q8iq

Level03

En la raiz del user vemos un programado llamado level03, si lo ejecutamos nos dice que lo explotemos. Pues para explotarlo necesitamos entender que hace para ello utilizaremos comandos como strings, ltrace o nm -u para obtener mas info sobre el programa

![image](https://github.com/user-attachments/assets/954f272e-a1ec-45c4-9677-cad12ffb4946)


![image](https://github.com/user-attachments/assets/e0e16194-fc99-4a37-982c-56197531038c)


![image](https://github.com/user-attachments/assets/a9c8f6d1-8637-48a7-867f-a59c25f27b82)

Bueno, una vez analizado el programa vemos que utiliza la funcion system y que ejecuta echo a traves del comando env. Pues yo aqui veo una vulneralidad muy potente. Lo que haremos sera sustituir el comando echo por una shell /bin/sh y cambiar la variable de env $PATH para que el nuevo echo aparezca ahi. 

Una vez nos funciona y lo explotamos verificamos el acceso con whoami y comprobamos que hemos escalado privilegios

![image](https://github.com/user-attachments/assets/4f3df830-5bca-45f3-af48-4d4b5ea8abde)

Flag03: qi0maab88jeaj46qoumi7maus

Level04


![image](https://github.com/user-attachments/assets/c6b11936-1c77-47d4-9736-46a567284574)


![image](https://github.com/user-attachments/assets/5c781066-6184-4dae-a08c-dc4a6d64c639)

obtiene el valor del parametro x de la solicitud HTTP (por ejemplo ?x=<valor>) y lo pasa a la funcion x, que ejecuta el comando echo con ese valor.


![image](https://github.com/user-attachments/assets/15aa2bed-7926-4b98-9361-0aa5efc2e539)


![image](https://github.com/user-attachments/assets/b3b276e1-9d2c-458d-bbf6-6e2688601e58)

Flag04: ne2searoevaevoem4ov4ar8ap

Level05

Como en el level00, entramos en el user y en la raiz no hay nada, pues vamos a buscar. Si buscamos los archivos creados por flag05 encontramos algo. 

![image](https://github.com/user-attachments/assets/86c1baa0-6689-4f9d-a222-87fcd0a28e77)

Lo que vemos es que hay un script que lo que hace es ejecutar todo lo que hay en la ruta /opt/openarenaserver/ y luego lo borra. Pues muy sencillo, crearemos un script que contenga el getflag en esa ruta para que lo ejecute y que nos almacene la flag en un fichero que este en otra ruta.

![image](https://github.com/user-attachments/assets/e940b193-c8e2-4690-851e-583e2ae18b5f)

Una vez se haya borrado el fichero y no lo encontremos en la ruta /opt/openarenaserver/ ya se habra ejecutado el script

![image](https://github.com/user-attachments/assets/f4afe45b-fc60-4066-9dd3-e6967a77a5ec)

Flag05: viuaaale9huek52boumoomioc

Level06

Entramos en el user y en la raiz vemos un programa y un fichero.php

![image](https://github.com/user-attachments/assets/72ba0388-bc2e-47ca-ac5a-77efe918864e)

Vamos a analizar detenidamente que hace el fichero .php ya que presenta vulnerabilidades

![image](https://github.com/user-attachments/assets/5e6e10f8-fbc5-4c99-b7b1-208713d04414)

Bueno viendo esto lo que entendemos es que la funcion x recibe 2 argumentos. Y el argv[1] (que sera lo que nosotros queramos) le hara una serie de remplazos y lo ejecutara. Es importante que entendamos que remplazos hara para que se ejecute lo que nosotros queramos. da palo explicarlo todo pero bueno que si hay algo entre [x ...] remplazara el contenido de dentro si hay un . por una x y un @ por y. Tambien remplazara los [ por ( y ] por ).

Sabiendo esto pues vamos a explotar el fallo.

![image](https://github.com/user-attachments/assets/df8a4fa2-6f39-4bf0-bdea-3a3abe785fdb)

flag06: wiok45aaoguiboiki2tuin6ub

Level07

Mas de lo mismo, muy parecido a un nivel anterior. Nos aparece un programa en la raiz del user, si lo ejecutamos se printa nuestros nombre de usuario. Vemos las strings legibles del programa con el comando strings y tambien nm -u para ver funciones que utiliza. Una vez analizado esto vemos que hay dos lineas , una que aparece LOGNAME y otra un echo sobre esa variable de entorno. Bueno sabiendo esto lo que haremos sera sustituir el valor de $LOGNAME para que el programa ejecute getflag.

![image](https://github.com/user-attachments/assets/7503f905-f43f-473a-909f-c113d33d53b1)

Flag07: fiumuikeil55xe9cu4dood66h

Level08

Otro lvl facilito. Aparece de nuevo un programa y un fichero llamado token que no tenemos permis para verlo ni nada. Hacemos strings sobre el programa para intentar analizarlo etc, este programa recibe un argumento y lo va a intentar leer y nos devuelve el contenido del fichero que le pasamos por argumento. Cada vez que le pasamos token nos dice que no tiene acceso, tanto si le pasamos el fichero token o cualquier string que contenga la palabra token. Por lo tanto, intuimos que la flag esta dentro de este fichero pero no lo podemos abrir ni hacer nada sobre él porque no tenemos permis y por otro lado sabemos que nuestro programa nos printa el contenido de un fichero pero siempre y cuando no sea o contenga la palabra "token", como tampoco podemos cambiar el nombre del file ni copiar y pegar su contenido lo que podemos hacer es un enlace simbolico para acceder al contenido de token sin ser el fichero token como tal. 

![image](https://github.com/user-attachments/assets/e21fbef0-4692-4615-b4a0-a5973e03332a)

Pass user flag08: quif5eloekouj29ke0vouxean

Flag08: 25749xKZ8L7DkSCwJkT9dyv6f

Level09

![image](https://github.com/user-attachments/assets/2d1cff9f-c0c1-4b93-ba29-9dd79f665b8e)

![image](https://github.com/user-attachments/assets/5c000b3b-b483-412f-9d33-3c8533725fc8)

```
#include <stdio.h>

int main(int argc, char **argv)
{
    int i = 0;
    char arg;

    while (argv[1][i])
    {
        arg = argv[1][i];
        printf("%c", arg - i);
        i++;
    }
    printf("\n");

    return 0;
}
```

![image](https://github.com/user-attachments/assets/d7fedc1d-245e-4335-933a-75f56df9f47d)

Pass user flag09: f3iji1ju5yuevaus41q1afiuq

Flag09: s5cAJpM8ev6XHw998pRWG728z

