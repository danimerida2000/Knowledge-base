---
description: >-
  Cualquier tipo de aplicación (web, nativa, etc) que confié en las APIs en el
  backend para poder acceder a recursos protegidos debe solicitar algún tipo de
  access token o api key.
---

# Mejores prácticas de ¿cómo manejar tokens?

### **Algunos puntos importantes a considerar:**

* La firma \(signature\) debe revelarse sólo a los servicios que lo necesitan.
* No agregar datos sensitivos al payload, ya que es fácil decodificar el token.
* Solamente agregar el mínimo de claims, con esto mejoraremos el rendimiento y seguridad de la información que vamos a exponer.
* Utilizar la estrategia de expiración en el token.
* Almacenar y reutilizar nuestros tokens evitaremos realizar peticiones innecesarias \(round trips\) y evitar que nuestra aplicación sufra de ataques de tipo XSS \(cross-site scripting\).
* Siempre utilizar HTTPS que es un protocolo seguro y encriptado para transferir datos a través de SSL/TLS,  ya que los tokens pueden ser interceptados y comprometidos.

### Autenticación basada en cookies \(token-based authentication\)

* Las aplicaciones tradicionales usualmente utilizan esta estrategia.
* Si la aplicación está en el mismo dominio que la API que estamos invocando.
* Como recomendación seteamos el ID token, no el access token.

### Autenticación basada en token \(token-based authentication\)

* Todas las peticiones al API que estamos invocando, el token se transfiere en el header como Authorization, por lo regular el estándar es JSON web token.

### Refresh token

* Flujos en donde se obtienen el refresh token
  * Authorization code
  * Authorization code con PKCE \(Proof Key for Code Exchange\)
  * Resource Owner password
  * Device authorization
* Hay que tener ciertas consideraciones con el acceso offline, ya que no debería de retornar el refresh token en el payload.



