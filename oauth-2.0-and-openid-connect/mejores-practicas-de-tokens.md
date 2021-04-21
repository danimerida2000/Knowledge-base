# Mejores prácticas de tokens

**Algunos puntos importantes a considerar:**

* La firma \(signature\) debe revelarse sólo a los servicios que lo necesitan.
* No agregar datos sensitivos al payload, ya que es fácil decodificar el token.
* Solamente agregar el mínimo de claims, con esto mejoraremos el rendimiento y seguridad de la información que vamos a exponer.
* Utilizar la estrategia de expiración en el token.
* Almacenar y reutilizar nuestros tokens evitaremos  realizar peticiones innecesarias \(round trips\) y evitar que nuestra aplicación sufra de ataques.
* Siempre utilizar HTTPS que es un protocolo seguro y encriptado para transferir datos a través de SSL/TLS,  ya que los tokens pueden ser interceptados y comprometidos.



