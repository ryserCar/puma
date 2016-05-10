#XSS (abreviatura de Cross Site Scripting) 
Es una vulnerabilidad generalizada que afecta a muchas aplicaciones web. El peligro detrás del XSS es que permite a un atacante inyectar contenido en un sitio web y modificar la forma en que ese contenido se muestra, lo que obliga al navegador de la víctima ejecutar el código suministrado por el atacante durante la carga de la página.
En general, las vulnerabilidades XSS requieren algún tipo de interacción por parte del usuario, sea a través de ingeniería social o esperando a alguien visitar una página específica para desencadenar la vulnerabilidad. Es por ello que, a menudo, esta vulnerabilidad no se toma tan en serio por los desarrolladores, pero si no se corrige pronto, puede ser muy peligrosa.


##La Inyección de Vulnerabilidad XSS
Cualquier sitio web o aplicación puede tener varias entradas. Se extienden desde los campos de formulario hasta la propia URL, que se convertirá en datos a manejar por el código. Un ejemplo sencillo de los datos son los formularios con nombre, nombre del usuario, contraseña, o cualquier otra forma de entrada.
Cada uno de estos puntos de datos son considerados como entradas y pueden ser manipulados si el código no valida las entradas y salidas de desinfección adecuadamente. Cuando una entrada fue especialmente diseñada para contener una secuencia particular de caracteres para que el servidor o el navegador respondan de una forma deseada, esto se llama inyección.
Este tipo de inyección es conocido como Cross-Site Scripting (XSS): una manera de inyectar código que ejecutará acciones en el navegador por un sitio web. Esta acción puede ser abrasiva y notificar al usuario, o puede funcionar en segundo plano sin el conocimiento del usuario.
Tal vez la prueba del concepto (Proof of Concept – POC) más rudimentaria que se puede ver puede incluir el uso de una marca de script muy básica que genera un pop-up notificando de un fallo en la página. Esta secuencia de comandos es la siguiente:
```
    <script>alert(THIS IS AN XSS VULNERABILITY!!)</script>
```
A través de este ejemplo, se utiliza un par de etiquetas HTML que definen un bloque de Javascript. Dentro de esto, la llamada a la función que hace que la caja aparezca con la siguiente frase: __THIS IS AN XSS VULNERABILITY!!!__

##Tipos de XSS
No todas las vulnerabilidades XSS son las mismas, hay varios tipos y aquí le mostramos una visión general de alto nivel de cada uno de ellos, incluyendo sus modos de entrega, para proporcionar un contexto:
!(URL https://blog.sucuri.net/wp-content/uploads/2016/04/Sucuri-Blog-XSS-Types.png)

Referencia: [Tipos de XSS OWASP](URL https://www.owasp.org/index.php/Types_of_Cross-Site_Scripting)

###Causado por código en el lado del servidor (Java, PHP, .NET, etc.):
Los ataques XSS tradicionales:
1. Reflejado (No Persistente) – se produce cuando el payload retorna de nuevo al usuario mediante la apertura de un link a un sitio web vulnerable con una entrada cambiada.
2. Almacenado (Persistente) – se produce cuando el payload se almacena en el servidor y se recupera cada vez que un usuario solicita una página web.
###Causado por código en el lado del cliente (Javascript, Visual Basic, Flash, etc.):
También conocido como XSS DOM-based:
3. Reflejado (No Persistente)- el mismo que se produce en el lado del servidor, pero esta vez, el payload es posible debido al procesamiento del código por el navegador.
4. Almacenado (Persistente) – el mismo que se produce en el lado del servidor, pero esta vez, el payload es almacenado en la máquina del cliente, usando el almacenamiento del navegador.
###Causado por la infraestructura (navegador, plugins, servidores, etc.):
Muy raro, pero es el tipo más peligroso de XSS:
5. Infraestructura en el lado del cliente – se produce cuando la carga útil tiene alguna relación con la parte interna del navegador, como un filtro XSS u otra funcionalidad del núcleo.
6. Infraestructura en el lado del servidor – se produce cuando el servidor web es responsable de no hacer frente a las peticiones, lo que permite la modificación de los organismos de respuesta.
7. Red – se produce cuando no se puede interferir en la comunicación entre el cliente y el servidor e inyectar paquete (s) de red con payload.
###Causado por el usuario:
Ocurre a menudo en estafas
8. Auto-XSS – se produce cuando el usuario es responsable de la inyección del payload en el navegador para conseguir acceso para sí mismo, generalmente a través de la ingeniería social.

