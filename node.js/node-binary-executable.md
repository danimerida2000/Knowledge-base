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

![](../.gitbook/assets/image%20%281%29.png)

* Ahora si deseamos conocer los argumentos del motor de ejecución V8 \(Runtime engine\), ejecutar **`node --v8-options`**.

![](../.gitbook/assets/image%20%282%29.png)

### Revisando sintaxis

Para revisar la sintaxis sin ejecutar la aplicación, podemos ejecutar el comando **`node --check index.js`** o también **`node -c index.js`**, si todo está bien la consola se mostrará vacía, de lo contrario nos mostrará los errores.

### Evaluando dinámicamente el código

Para evaluar una expresión e imprimir el resultado utilizamos el argumento **`-p`** o **`--print`**, ahora si solamente deseamos evaluar pero no imprimir el resultado usamos el argumento **`-e`** o **`--eval`**.

**Algunos ejemplos:**

* Convertir 2e5 milisegundos a minutos: **`node --print '2e5/(1e3*60)'`**.

![](../.gitbook/assets/image%20%283%29.png)

* Comprobamos el ejemplo anterior pero con el argumento -e o --eval: **`node --eval '2e5/(1e3*60)'`**.

![](../.gitbook/assets/image%20%284%29.png)

> Todos los módulos del Core de Node están accesibles dentro del contexto de evaluación del código.

### Precarga de módulos

Con el siguiente argumento `-r` o `--require` se puede precargar un módulo.

**Ejemplo:**

![](../.gitbook/assets/image%20%287%29.png)

La precarga de módulos son útiles cuando se utilizan módulos de consumo, como por ejemplo: el módulo dotenv.

### Límite de pila de datos \(Stack trace\)

Son generados por cualquier error, usualmente contiene los últimos 10 stack frames \(funciones que invocan\) en donde captura el error.

Si deseamos modificar el límite, habría que cambiar el flag **`--stack-trace-limit`**  y es parte del motor de runtime de javascript, V8, y también puede ser encontrado en el flag **`--v8-options`:**

![](../.gitbook/assets/image%20%288%29.png)

Si deseamos establecer el límite de stack trace a un número superior que la cantidad de call frames nos garantizará que se mostrará todo el stack de errores; ejemplo: **`node --stack-trace-limit=1000 index.js`**

> **Es recomendable utilizar esta sobreescritura en un ambiente de desarrollo, ya que en producción podría retener logs innecesarios.**

 



\*\*\*\*



