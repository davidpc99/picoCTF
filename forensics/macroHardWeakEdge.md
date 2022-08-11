# MacroHard WeahEdge

Para la realización el ejercicio comenzamos analizando el tipo de fichero de 'Forensics is fun.pptm'

Nos sale "Forensics is fun.pptm: Microsoft PowerPoint 2007+" que se trata de un PowerPoint.

Mediante binwalk descubriremos si este archivo contiene otros ocultos:

![image](https://user-images.githubusercontent.com/71788370/184170562-5d923c62-d339-4ce6-87c3-ce319a496c6c.png)

Podemos ver como hay archivos ocultos en el mismo. Los obtendremos mediante el comando "unzip Forensics\ is\ fun.pptm", quedando el directorio de la siguiente forma:

![image](https://user-images.githubusercontent.com/71788370/184171228-cc7d3a1e-fc4c-463e-9d09-d69078ad2870.png)

Comenzamos buscando bandera buscando de forma recursiva en el directorio con el comando "grep -nr 'picoCTF*'", pero no se encuentra nada. Por ello, recorremos todos los directorios cpmprobando el contenido de los archivos con "strings" hasta que encontramos en "ppt/slideMasters" el archivo "hidden". Al hacerle un cat obtenemos:
Z m x h Z z o g c G l j b 0 N U R n t E M W R f d V 9 r b j B 3 X 3 B w d H N f c l 9 6 M X A 1 f Q

Parece ser información en base64, por lo que lo decodificaremmos en una página de internet como [esta](https://www.base64decode.org/), obteniendo finalmente la bandera picoCTF{D1d_u_kn0w_ppts_r_z1p5}.

