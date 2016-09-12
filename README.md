# Protocolos de Internet
_________________________________________________________________
### HTTP
_________________________________________________________________
#### Protocolo de Transferencia de Hipertexto
Es el protocolo de comunicación que permite las transferencias de información en la World Wide Web. Es un protocolo orientado a transacciones y sigue el esquema petición-respuesta entre un cliente y un servidor

> Última versión 	2.0
Puertos 	80/TCP

HTTP define la sintaxis y la semántica que utilizan los elementos de software de la arquitectura web (clientes, servidores, proxies) para comunicarse. HTTP es un protocolo sin estado, es decir, no guarda ninguna información sobre conexiones anteriores.

HTTP ha pasado por múltiples versiones del protocolo, muchas de las cuales son compatibles con las anteriores. El RFC 2145 describe el uso de los números de versión de HTTP. El cliente le dice al servidor al principio de la petición la versión que usa, y el servidor usa la misma o una anterior en su respuesta.

~~~


HTTP/1.0 (mayo de 1996)
    Esta es la primera revisión del protocolo que especifica su versión en las comunicaciones, y todavía se usa ampliamente, sobre todo en servidores proxy. Permite los métodos de petición GET, HEAD y POST.

HTTP/1.1 (junio de 1999)
    Versión más usada actualmente; Las conexiones persistentes están activadas por defecto y funcionan bien con los proxies. También permite al cliente enviar múltiples peticiones a la vez por la misma conexión (pipelining) lo que hace posible eliminar el tiempo de Round-Trip delay por cada petición. 
    
HTTP/2 (mayo de 2015)
    En el año 2012 aparecen los primeros borradores de la nueva versión de HTTP (HTTP/2). Esta nueva versión no modifica la semántica de aplicación de http (todos los conceptos básicos continúan sin cambios). Sus mejoras se enfocan en como se empaquetan los datos y en el transporte. Por ejemplo, añade el uso de una única conexión, la compresión de cabeceras o el servicio 'server push'
~~~
##### Métodos de petición
HTTP define una serie predefinida de métodos de petición que pueden utilizarse.

* HEAD Pide una respuesta idéntica a la que correspondería a una petición GET, pero en la petición no se devuelve el cuerpo.
* GET Pide una representación del recurso especificado
* POST Envía los datos para que sean procesados por el recurso identificado.
* PUT Sube, carga o realiza un upload de un recurso especificado (archivo)
* DELETE Borra el recurso especificado.borra
* TRACE Este método solicita al servidor que en la respuesta meta todos los datos que reciba en el mensaje de petición. 


### PROTOCOLO FTP
________________________
#### Protocolo de Transferencia de Archivos
____________________________________________________________________
Es un protocolo de red para la transferencia de archivos entre sistemas conectados a una red TCP (Transmission Control Protocol), basado en la arquitectura cliente-servidor. Desde un equipo cliente se puede conectar a un servidor para descargar archivos desde él o para enviarle archivos, independientemente del sistema operativo utilizado en cada equipo.

> Puertos 	20/TCP DATA Port
21/TCP Control Port

Un problema básico de FTP es que está pensado para ofrecer la máxima velocidad en la conexión, pero no la máxima seguridad, ya que todo el intercambio de información, desde el login y password del usuario en el servidor hasta la transferencia de cualquier archivo, se realiza en texto plano sin ningún tipo de cifrado, con lo que un posible atacante puede capturar este tráfico, acceder al servidor y/o apropiarse de los archivos transferidos.

Para solucionar este problema son de gran utilidad aplicaciones como SCP y SFTP, incluidas en el paquete SSH, que permiten transferir archivos pero cifrando todo el tráfico.

En el modelo, el intérprete de protocolo (IP) de usuario inicia la conexión de control en el puerto 21. Las órdenes FTP estándar las genera el IP de usuario y se transmiten al proceso servidor a través de la conexión de control. Las respuestas estándar se envían desde la IP del servidor hasta la IP de usuario por la conexión de control como respuesta a las órdenes
![ftp](https://vladi01.files.wordpress.com/2010/12/dibujo1.jpg)

### SMTP
____
#### Simple Mail Transfer Protocol
___
Protocolo para transferencia simple de correo, es un protocolo de red utilizado para el intercambio de mensajes de correo electrónico entre computadoras u otros dispositivos (PDA, teléfonos móviles, impresoras, etc). Fue definido en el RFC 2821 y es un estándar oficial de Internet.

El funcionamiento de este protocolo se da en línea, de manera que opera en los servicios de correo electrónico. Sin embargo, este protocolo posee algunas limitaciones en cuanto a la recepción de mensajes en el servidor de destino (cola de mensajes recibidos). Como alternativa a esta limitación se asocia normalmente a este protocolo con otros, como el POP o IMAP, otorgando a SMTP la tarea específica de enviar correo, y recibirlos empleando los otros protocolos antes mencionados (POP O IMAP).

> Puertos 	25/TCP
587/TCP (alternativo para clientes de correo)
465/TCP (SMTPS)

SMTP es un protocolo orientado a la conexión basado en texto, en el que un remitente de correo se comunica con un receptor de correo electrónico mediante la emisión de secuencias de comandos y el suministro de los datos necesarios en un canal de flujo de datos ordenado fiable, normalmente un protocolo de control de transmisión de conexión (TCP). Una sesión SMTP consiste en comandos originados por un cliente SMTP (el agente de inicio, emisor o transmisor) y las respuestas correspondientes del SMTP del servidor (el agente de escucha, o receptor) para que la sesión se abra y se intercambian los parámetros de la sesión. Una sesión puede incluir cero o más transacciones SMTP. Una transacción de SMTP se compone de tres secuencias de comando / respuesta

### POP
____
#### POST OFFICE PROTOCOL
_____
En informática se utiliza el Post Office Protocol (POP3, Protocolo de Oficina de Correo o "Protocolo de Oficina Postal") en clientes locales de correo para obtener los mensajes de correo electrónico almacenados en un servidor remoto, denominado Servidor POP. Es un protocolo de nivel de aplicación en el Modelo OSI.

Las versiones del protocolo POP, informalmente conocido como POP1 y POP2, se han quedado obsoletas debido a las últimas versiones de POP3. En general cuando se hace referencia al término POP, se refiere a POP3 dentro del contexto de protocolos de correo electrónico

> Función 	Obtención de mensajes de correo electrónico en clientes locales.
Puertos 	110/TCP
995/TCP (Cifrado)

POP3 está diseñado para recibir correo, que en algunos casos no es para enviarlo; le permite a los usuarios con conexiones intermitentes o muy lentas (tales como las conexiones por módem), descargar su correo electrónico mientras tienen conexión y revisarlo posteriormente incluso estando desconectados. Cabe mencionar que aunque algunos clientes de correo incluyen la opción de dejar los mensajes en el servidor, el funcionamiento general es: un cliente que utilice POP3 se conecta, obtiene todos los mensajes, los almacena en la computadora del usuario como mensajes nuevos, los elimina del servidor y finalmente se desconecta

![POP3](http://mundoplanotp2uminho.pbworks.com/f/1259439494/smtp_pop3_diagram.jpg)

##### Ventajas
____
~~~
La ventaja con otros protocolos es que entre servidor-cliente no se tienen que enviar tantas órdenes para la comunicación entre ellos. El protocolo POP también funciona adecuadamente si no se utiliza una conexión constante a Internet o a la red que contiene el servidor de correo
~~~

### TELNET
____
#### Telecommunication Network
____
Es el nombre de un protocolo de red que nos permite viajar a otra máquina para manejarla remotamente como si estuviéramos sentados delante de ella. También es el nombre del programa informático que implementa el cliente. Para que la conexión funcione, como en todos los servicios de Internet, la máquina a la que se acceda debe tener un programa especial que reciba y gestione las conexiones. 

> Función 	Protocolo cliente/servidor
Puertos 	23/TCP

Telnet sólo sirve para acceder en modo terminal, es decir, sin gráficos, pero es una herramienta muy útil para arreglar fallos a distancia, sin necesidad de estar físicamente en el mismo sitio que la máquina que los tenga. También se usaba para consultar datos a distancia, como datos personales en máquinas accesibles por red, información bibliográfica, etc.

Su mayor problema es de seguridad, ya que todos los nombres de usuario y contraseñas necesarias para entrar en las máquinas viajan por la red como texto plano (cadenas de texto sin cifrar). Esto facilita que cualquiera que espíe el tráfico de la red pueda obtener los nombres de usuario y contraseñas, y así acceder él también a todas esas máquinas.

### SFTP
___
El protocolo SFTP permite una serie de operaciones sobre archivos remotos. 

 SSH (Secure SHell, en español: intérprete de órdenes segura) es el nombre de un protocolo y del programa que lo implementa, y sirve paraacceder a máquinas remotas a través de una red. Permite manejar por completo la computadora mediante un intérprete de comandos, y también puede redirigir el tráfico de X para poder ejecutar programas gráficos si tenemos un Servidor X (en sistemas Unix y Windows) corriendo.
Además de la conexión a otros dispositivos, SSH nos permite copiar datos de forma segura (tanto archivos sueltos como simular sesiones FTPcifradas), gestionar claves RSA para no escribir claves al conectar a los dispositivos y pasar los datos de cualquier otra aplicación por un canal seguro tunelizado mediante SSH.

> SFTP utiliza el puerto 22 de TCP

### IMAP
____
#### Internet Message Access Protocol
____

IMAP: es un protocolo de red de acceso a mensajes electrónicos almacenados en un servidor. Mediante IMAP se puede tener acceso al correo electrónico desde cualquier equipo que tenga una conexión a Internet. IMAP tiene varias ventajas sobre POP, que es el otro protocolo empleado para obtener correo desde un servidor. Por ejemplo, es posible especificar en IMAP carpetas del lado servidor. Por otro lado, es más complejo que POP ya que permite visualizar los mensajes de manera remota y no descargando los mensajes como lo hace POP.

>Se conecta al servidor por el puerto 143 (TCP).

-Características: A diferencia del protocolo POP3, el correo no es descargado inmediatamente sino que es leido o consultado directamente en el servidor, Permite ver unicamente los encabezados del mensaje antes de decidir si abrirlo o eliminarlo, El servidor retiene el correo hasta que se solicite su eliminación, Puede consultarse el mismo correo desde diferentes computadoras ya que solo se lee lo que hay en el servidor, Permite operaciones avanzadas como creacion de carpetas y buzones en el servidor.


