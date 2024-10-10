![image](https://github.com/user-attachments/assets/37cbe494-9292-4e7b-92f4-c3717871228d)# Snow-Crash
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
