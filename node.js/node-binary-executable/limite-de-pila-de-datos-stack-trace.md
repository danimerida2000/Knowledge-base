# Límite de pila de datos \(Stack trace\)



Son generados por cualquier error, usualmente contiene los últimos 10 stack frames \(funciones que invocan\) en donde captura el error.

Si deseamos modificar el límite, habría que cambiar el flag **`--stack-trace-limit`**  y es parte del motor de runtime de javascript, V8, y también puede ser encontrado en el flag **`--v8-options`:**

![](../../.gitbook/assets/image%20%288%29.png)

Si deseamos establecer el límite de stack trace a un número superior que la cantidad de call frames nos garantizará que se mostrará todo el stack de errores; ejemplo: **`node --stack-trace-limit=1000 index.js`**

> **Es recomendable utilizar esta sobreescritura en un ambiente de desarrollo, ya que en producción podría retener logs innecesarios.**

