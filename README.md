# Diseño de ingeniería admin

link frontend desplegado: https://frontend-core-7tveg0onm-xavi122323s-projects.vercel.app

link backend desplegado: https://corebackend.onrender.com

## Diagrama

![Diagrama core](https://github.com/Xavi122323/DisenioIngWebCore/assets/65315734/2b6b109a-9ad9-4dbd-b659-24dde459846b)

El sistema de inicio de sesión propuesto opera a través de un plugin denominado "devise". Este plugin facilita la gestión del acceso desde el backend, permitiendo cifrar las contraseñas y utilizar un JWT (Token Web JSON) que se intercambia entre el frontend y el backend para garantizar la integridad de los enlaces y asociar a cada usuario con su correspondiente token.

En nuestro diagrama, el proceso inicia con el registro del usuario. El frontend recibe el correo electrónico y la contraseña, los transmite al backend, donde se verifica su validez. Si son válidos, se almacenan en la base de datos, se asocian con un token JWT, y el frontend guarda dicho token localmente. Si se realiza una solicitud para volver al inicio de sesión, el token se elimina, tanto en el backend como en el frontend.

En el caso de iniciar sesión (sign in), las credenciales del usuario se envían desde el frontend al backend. Luego, se verifica su autenticidad en el backend. Si son válidas, se envía el token de vuelta al frontend, donde se almacena localmente en el inicio de sesión. Con este proceso completado, se permite el acceso a la aplicación y la realización de las operaciones correspondientes.

A través del backend, se codifica en el token tanto el identificador del usuario como su rol. Esto se realiza porque el token se emplea para verificar estos parámetros, y es nuestro controlador de sesiones el encargado de autenticar las credenciales, en este caso, el correo electrónico y la contraseña. Esta implementación nos posibilita gestionar roles dentro de nuestro sistema de inicio de sesión, lo que permite la especialización de los usuarios y la restricción de sus funciones.


