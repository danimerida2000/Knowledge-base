# Funciones

Una función es un objeto, que puede ser utilizado como cualquier otro valor.

**Ejemplos:**

* **Una función que retorna otra función:**
  * `function primera () {   return function segunda () {} }`
* **Una función transferida a otra función como argumento:**
  * `setTimeout(function () {`

        `console.log("Función como argumento");`

    `}, 100);`
* **Una función asignada a un objeto:**
  * **`This`** referencia al objeto en donde la función fue invocada \(contexto\), no al objeto al que se asignó la función.
    * `const obj = {`

          `id: 12345,`

          `fn: function() {`

              `console.log(this.id);`

          `}`

      `};`

      `obj.fn(); // 12345`

    * `const obj = {`

          `id: 1,`

          `fn: function() {`

              `console.log(this.id);`

          `}`

      `};`

      `const obj2 = {`

          `id: 2,`

          `fn: obj.fn`

      `};`

      `obj2.fn(); // 2`

      `obj.fn(); // 1`
* **El método `call` puede ser usado para setear un contexto:**
  * `function fn() {`

        `console.log(this.id);`

    `}`

    `const obj1 = {`

        `id: 1`

    `};`

    `const obj2 = {`

        `id: 2`

    `};`

    `fn.call(obj2); // 2`

    `fn.call(obj1); // 1`

    `fn.call({`

        `id: 'testing'`

    `}); // testing`
* **Funciones fat arrow o lambda:**
  * Cuando la definimos sin llaves, la expresión que sigue es la que retornaremos.
  * No tiene su propio contexto, cuando referenciamos un **`this`** buscará la función padre no-lambda.
    * `function fn() {`

          `return (offset) => {`

              `console.log(this.id + offset)`

          `}`

      `}`

      `const obj = {`

          `id: 999`

      `}`

      `const offsetter = fn.call(obj)`

      `offsetter(1) // 1000 (999 + 1)`
  * No tiene la propiedad prototype.
    * `function normalFunction() {}`

      `const fatArrowFunction = () => {}`

      `console.log(typeof normalFunction.prototype) // 'object'`

      `console.log(typeof fatArrowFunction.prototype) // 'undefined'`

