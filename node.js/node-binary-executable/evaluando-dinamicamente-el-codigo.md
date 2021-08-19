# Evaluando dinámicamente el código



Para evaluar una expresión e imprimir el resultado utilizamos el argumento **`-p`** o **`--print`**, ahora si solamente deseamos evaluar pero no imprimir el resultado usamos el argumento **`-e`** o **`--eval`**.

**Algunos ejemplos:**

* Convertir 2e5 milisegundos a minutos: **`node --print '2e5/(1e3*60)'`**.

![](../../.gitbook/assets/image%20%283%29.png)

* Comprobamos el ejemplo anterior pero con el argumento -e o --eval: **`node --eval '2e5/(1e3*60)'`**.

![](../../.gitbook/assets/image%20%284%29.png)

> Todos los módulos del Core de Node están accesibles dentro del contexto de evaluación del código.

