---
description: >-
  El proceso de depuración en Node.js debe empezar en modo Inspect que expone un
  protocolo remoto que puede ser conectado y permite diagnosticar a través de
  puntos de interrupción.
---

# Depuración y diagnóstico

### Objetivos

* Iniciar un proceso en modo inspect.
* Conectar un proceso en modo inspect para depurarlo.
* Comprender que son los breakpoints \(puntos de ruptura o interrupción\).

### Inicio de modo inspección

Node.js soporta el protocolo de depuración remota como chrome DevTools.

Para activar el modo inspección: **`node --inspect index.js`**

Activar el modo inspección pero iniciando con un breakpoint \(Inspect Break mode\) activo al inicio del programa: **`node --inspect-brk index.js`**

Si no utilizamos los flags anteriores, la aplicación se inicializará por completo y estará realizando tareas asíncronas antes de que pueda establecer los breakpoints.

**Ejemplo utilizando Chrome Devtools:**

Vamos a crear un pequeño programa con el algoritmo recursivo de fibonacci.

![](../.gitbook/assets/image%20%2811%29.png)

Ejecutamos en modo inspección:

> Después de ejecutar el comando **`node --inspect-brk index.js`**, el protocolo de depuración remota utiliza WebSockets \(ws://\), y así es como Chrome detectará que el depurador está escuchando automáticamente.

![](../.gitbook/assets/image%20%2812%29.png)

Abrimos Chrome e ingresamos a chrome://inspect/\#devices:

![](../.gitbook/assets/image%20%289%29.png)

Click en inspect y nos abrirá una instancia DevTools que está conectada con el proceso de Node:

![](../.gitbook/assets/image%20%2810%29.png)

Para mayor información acerca de otras herramientas para depurar: [https://nodejs.org/en/docs/guides/debugging-getting-started/](https://nodejs.org/en/docs/guides/debugging-getting-started/)

Si deseamos que haga una pausa en excepciones detectadas, debemos dar click en **"Pause on caught exceptions":**

> Está funcionalidad es útil para localizar excepciones dentro del código, ya que nos muestra la pila de llamadas \(Call Stack\).

![](../.gitbook/assets/image%20%2815%29.png)

Agreguemos un breakpoint y veamos el comportamiento del call stack:

> Después de agregar el breakpoint con un click sobre la línea que deseamos evaluar, y damos click en el primer botón \(azul\), se reanudará la ejecución del programa e iniciará la trazabilidad de ejecución en el panel de call stack.

![](../.gitbook/assets/image%20%2813%29.png)

En algunos casos se puede agregar un breakpoint directamente en el código, utilizando el flag **`--inspect,`** y agregándole en el código la declaración **`debugger`** \(línea 5\):

> **No es buena práctica utilizar esta estrategia por el impacto de rendimiento.**

![](../.gitbook/assets/image%20%2814%29.png)











