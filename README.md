# Microservice-Notifications-Web  

Notifications es un servicio que esta pensado en como su nombre lo indica mostrar las notificaciones diferentes que reciben los usuarios del PORTAL EDUCATIVO PARA EL PROGRAMA DE INGENIERÍA DE SISTEMAS, esta desarollado en Vue.js el cual es un framework de JavaScript de codigo abierto, se trabajó mediante microservicios usando una arquitectura capas. Este servicio tiene como finalidad enseñar los diferentes tipos de notificaciones que pueda tener un usuario de nuestro portal, como lo son, inicio de sesión, registro, recordatorio de tutorias, mensajes entre compañeros, entre otros.

Link del aplicativo desplegado 
http://notifications-ufps.s3-website.us-east-2.amazonaws.com/

Se deben pasar los parametros id y api_token, un ejemplo seria asi
http://notifications-ufps.s3-website.us-east-2.amazonaws.com/?id=1&api_token=Pt3bCLQZ6nlBIotpkmYOjxt89UGqod30UthCAEMN6xOup7vQ5FTn3dSC19XOBW78EPS7eUyuqKPPlpfcH3Ks1LdkL1qf4GkLiewSP8MzhTA2fhmHvhIxxTwE5GvSsjy6UMR8rzuCO1DqRRvtpIvczm

## Project setup
```
1. Clonar el repositorio en su equipo, git clone https://github.com/Arquitectura-de-software-UFPS-2021-2/Microservice-Notifications-Service-Web.git
2. Para inicializar el proyecto en la consola de su editor digite el siguiente script "npm install"
3. Para compilar y recargar el desarrollo que se tiene en su consola digite "npm run serve"
4. Para compilar y minimizar para producción digite el siguiente script "npm run build"
```

### Desplegar 
Para desplegar el aplicativo puede hacerlo mediante amazon 

### Routes Config 
```
ENDPOINT ->  /notifications?id=1 ->  this id is an example but really is dinamic
Then the Vue.js Front returned the view from user
```
### Customize configuration
```
Para obtener otras configuraciones dirigirse a la siguiente pagina [Configuration Reference](https://cli.vuejs.org/config/).
```
## Front-end
```
El desarrollo del Front-end se realizó en Vue.js por medio de una biblioteca de interfaz de usuario la cual es Vuetify, con la cual se estructuraron las vistas que se trabajaron en el proyecto 
```
## Imagenes 
![arquitectura](https://user-images.githubusercontent.com/54825931/146826850-544ef371-293c-4c4a-9590-50303b88da18.jpeg)


En esta imagen podemos apreciar los tipos de notificaciones 
El primero que observamos es el que notifica que hay un nuevo curso en el cual nos inscribimos 
Seguido de este vemos la notificación de Registro exitoso, este sucede cuando se termina de hacer la inscripción en el portal educativo. 
Luego podemos apreciar un tipo de notificación que nos dice que hemos iniciado sesión si así ha ocurrido, esto para mantener la seguridad de que si es quien dice ser el que ha iniciado sesión. 
La cuarta notificación que observamos es un recordatorio, de asesorias que tenemos y nos muestra el docente que va a impartir la asesoria. 
El quinto tipo de notificación sucede cuando se ha agendado una asesoria. 
La siguiente notificación es un mensaje entre compañeros registrados en el portal.
La proxima notificación nos enseña las publicaciones recientes de los compañeros que se encuentran en el portal. 
De cada una de ellas se puede ver especificamente el mensaje que llega pulsando sobre la flecha que se encuentra en la parte final derecha de cada notificación

