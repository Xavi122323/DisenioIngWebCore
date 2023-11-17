# Diseño de ingeniería admin

link frontend desplegado: https://frontend-core-7tveg0onm-xavi122323s-projects.vercel.app

link backend desplegado: https://corebackend.onrender.com

## Diagrama

![Diagrama core](https://github.com/Xavi122323/DisenioIngWebCore/assets/65315734/2b6b109a-9ad9-4dbd-b659-24dde459846b)

El sistema de inicio de sesión propuesto opera a través de un plugin denominado "devise". Este plugin facilita la gestión del acceso desde el backend, permitiendo cifrar las contraseñas y utilizar un JWT (Token Web JSON) que se intercambia entre el frontend y el backend para garantizar la integridad de los enlaces y asociar a cada usuario con su correspondiente token.

En nuestro diagrama, el proceso inicia con el registro del usuario. El frontend recibe el correo electrónico y la contraseña, los transmite al backend, donde se verifica su validez. Si son válidos, se almacenan en la base de datos, se asocian con un token JWT, y el frontend guarda dicho token localmente. Si se realiza una solicitud para volver al inicio de sesión, el token se elimina, tanto en el backend como en el frontend.

En el caso de iniciar sesión (sign in), las credenciales del usuario se envían desde el frontend al backend. Luego, se verifica su autenticidad en el backend. Si son válidas, se envía el token de vuelta al frontend, donde se almacena localmente en el inicio de sesión. Con este proceso completado, se permite el acceso a la aplicación y la realización de las operaciones correspondientes.

A través del backend, se codifica en el token tanto el identificador del usuario como su rol. Esto se realiza porque el token se emplea para verificar estos parámetros, y es nuestro controlador de sesiones el encargado de autenticar las credenciales, en este caso, el correo electrónico y la contraseña. Esta implementación nos posibilita gestionar roles dentro de nuestro sistema de inicio de sesión, lo que permite la especialización de los usuarios y la restricción de sus funciones.

## Explicación de validación por back-end

En la primera iteración del backend, se realiza una validación inicial que aborda aspectos cruciales y fundamentales para el funcionamiento de la aplicación. Al establecer dos roles iniciales, usuario y administrador, se busca restringir las acciones de los usuarios a la capacidad de ingresar servidores y editarlos en caso de inconsistencias. Por otro lado, se limita la capacidad de eliminar (delete) a los administradores, asegurando así la consistencia de la información.

En futuras iteraciones, se contempla la creación de un tercer rol, el de DBA (Administrador de Base de Datos). Este rol se encargaría de la carga de información, restringiendo aún más las capacidades del usuario para enfocarse exclusivamente en el análisis de datos. Además, se planea que el administrador tenga la capacidad de gestionar los roles de los usuarios para controlar de manera más efectiva sus permisos.

Esta estructura es esencial para el núcleo del sistema por varias razones:

1. Centraliza la carga de información para aliviar al usuario de esa responsabilidad, garantizando consistencia y validez de los datos.
2. Permite una administración eficiente de roles con un control exhaustivo para prevenir alteraciones no autorizadas de la información.
3. Facilita una interacción mejorada de los usuarios con el sistema.
   
La implementación actual del login valida tanto las credenciales como el token en el backend, lo cual mejora la seguridad durante el inicio de sesión. El token almacenado contiene únicamente la información mínima necesaria, como el ID y el rol del usuario, para evitar comprometer la seguridad mientras se administran los accesos. Las credenciales se verifican a través del controlador de sesiones, y solo cuando se confirman las credenciales, se genera el token para acceder al sistema. Es por estas razones que el sistema de login se gestiona completamente desde el backend.
