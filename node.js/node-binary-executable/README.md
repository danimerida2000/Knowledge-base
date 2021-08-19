---
description: >-
  Para ejecutar programas en javascript debemos utilizar el ejecutable binario
  de node, ejemplo: node index.js, en donde index.js es el archivo que deseamos
  ejecutar.
---

# Node binary executable

### Objetivos

* Conocer todos los argumentos en línea de comando de Node y runtime engine V8.
* Comprender la importancia de la ejecución de dichos comandos.



### Visualizar argumentos con --help

* Para visualizar todos los argumentos de node, es necesario ejecutar **`node --help`.**

![](../../.gitbook/assets/image%20%281%29.png)

* Ahora si deseamos conocer los argumentos del motor de ejecución V8 \(Runtime engine\), ejecutar **`node --v8-options`**.

![](../../.gitbook/assets/image%20%282%29.png)

### Revisando sintaxis

Para revisar la sintaxis sin ejecutar la aplicación, podemos ejecutar el comando **`node --check index.js`** o también **`node -c index.js`**, si todo está bien la consola se mostrará vacía, de lo contrario nos mostrará los errores.

Revisaremos con detalle los siguientes temas:

{% page-ref page="evaluando-dinamicamente-el-codigo.md" %}

{% page-ref page="precarga-de-modulos.md" %}

{% page-ref page="limite-de-pila-de-datos-stack-trace.md" %}





\*\*\*\*



