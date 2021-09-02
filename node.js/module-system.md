---
description: >-
  Los módulos son unidades de código qué están compuestos por otros módulos; los
  paquetes son expuestos en módulos, un archivo podría considerarse un módulo,
  inclusive las librerías son módulos.
---

# Sistema de módulos

## Objetivos

* Aprender cómo se cargan los módulos.
* Conocer cómo crear módulos.
* Buscar la ruta de los módulos.
* Detectar si un módulo es el punto de entrada de una aplicación.

{% hint style="success" %}
La función **`require`** es transferido al namespace del paquete y busca la referencia dentro del directorio **node\_modules** y retorna el archivo principal del paquete.
{% endhint %}

## Creando un módulo

#### Ejemplo:

Desarrollaremos un módulo que imprima en pantalla según severidad, recibirá de argumento de entrada el tipo y el mensaje.

```javascript
const logging = (type, message) => {
  if (!type || !message) {
    throw new Error('Los atributos type y message son obligatorios');
  }
  switch (type) {
    case 'info':
      console.info(message);
      break;
    case 'error':
      console.error(message);
      break;
    case 'warning':
      console.warn(message);
      break;
    default:
      console.log(message);
  }
};

module.exports = {
  logging
};

```

![](../.gitbook/assets/image%20%2827%29.png)

En la imagen anterior podemos observar que cargamos nuestro módulo con **`require`,** podemos incluir la extensión \(.js\), pero no es necesario; la forma en que retornamos el contenido de nuestro archivo es a través de **`module.exports`**.

## Detectando el módulo principal

Si deseamos que nuestro módulo opere como un programa/servicio y que al mismo tiempo pueda ser cargado como módulo, utilizaremos dos alternativas: **`module.parent === null`** o **`require.main === module`**.

#### Ejemplo:

```javascript
const { logging } = require('./logModule');

if (require.main === module) {
  logging('info', 'Ejecutando como programa principal');
} else {
  const process = (message) => {
    logging('warn', message);
  };
  module.exports = process;
}
```

![](../.gitbook/assets/image%20%2822%29.png)

## Resolviendo la ruta de un módulo

Para determinar la ruta absoluta de cualquier módulo requerido utilizaremos el método **`resolve`** de la función **`require`**.

#### Ejemplo:

```javascript
console.log();
console.group('# Package resolution');
console.info("require('signale')", '=>', require.resolve('signale'));
console.groupEnd();
console.log();

console.group('# Directory resolution');
console.info("require('.');", '=>', require.resolve('.'));
console.groupEnd();
console.log();

console.group('# File resolution');
console.info("require('./logModule');", '=>', require.resolve('./logModule'));
console.groupEnd();
console.log();

console.group('# Core APIs resolution');
console.info("require('fs')", '=>', require.resolve('fs'));
console.groupEnd();
console.log();

```

![](../.gitbook/assets/image%20%2823%29.png)

