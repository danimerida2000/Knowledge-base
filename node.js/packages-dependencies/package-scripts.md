# Package scripts

El atributo **`scripts`** que se encuentra en **package.json** puede ser utilizado para ejecutar comandos shell.

Los paquetes pueden ser asignados al campo **`bin`** en **package.json** qué será asociado a un namespace.

#### Ejemplo:

Instalaremos una dependencia llamada **standard** y la invocaremos en un script.

![](../../.gitbook/assets/image%20%2818%29.png)

Agregaremos código e instalaremos otra dependencia llamada **signale** para la gestión de logs.

![](../../.gitbook/assets/image%20%2817%29.png)

Un nuevo atributo en scripts llamado **lint** que invoca **standard**:

![](../../.gitbook/assets/image%20%2820%29.png)

Ejecutamos **npm run lint**:

![](../../.gitbook/assets/image%20%2821%29.png)

Le delegamos a **standard** para que corrija nuestro código automáticamente:

![](../../.gitbook/assets/image%20%2819%29.png)

Si observamos la imagen anterior, **standard** corrigió la mayoría de sugerencias de cambio en nuestro código, pero no pudo corregir la que definimos en la línea 3.

