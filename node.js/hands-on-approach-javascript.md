---
description: >-
  El enfoque de esta sección se centra en la comprensión de los fundamentos de
  javascript.
---

# Enfoque práctico de javascript

### **Objetivos**

* Comprender los tipo de datos.
* Explicar el rol del scope de closure en el manejo de sesiones.
* Describir la herencia basada en javascript.

### **Tipos de datos**

Javascript es un lenguaje dinámico, y cuenta con 7 tipos primitivos:

* Null
  * Usualmente describe la ausencia de un objeto.
* Undefined
  * Es la ausencia de un valor definido.
  * Cualquier variable sin valor al inicializar.
  * Cualquier expresión que intente acceder a una propiedad inexistente.
  * Función sin una declaración **`return`**.
* Number
  * Es un formato de punto flotante de doble precisión.
  * Permite enteros y decimales que están dentro del rango -2^53-1 a 2^53-1.
* BigInt
  * No tiene límite inferior ni superior en números enteros.
* String
  * Pueden ser creados con comilla simple, doble o invertida.
  * Las cadenas \(String\) creadas a partir de las comilla invertidas \(backticks\) se llaman template literals o template strings, y pueden ser multilíneas y soportan interpolación \(string interpolation \[${expresión}\]\).
* Boolean
  * Tiene dos valores: **`true`** o **`false`**
* Symbol
  * Puede ser usado como una llave única en un objeto.
  * El método Symbol.for crea u obtiene un símbolo global.
* Los demás tipos de datos son objetos
  * Un objeto es un conjunto de claves y valores \(key, values\), y dentro del valor puede existir un tipo primitivo o un objeto incluyendo funciones.
  * La clave de un objeto se llama propiedad.
  * Un objeto podría tener como valor otro objeto y eso nos permite estructuras de datos anidadas \(nested\).
  * Todos los objetos tienen prototipos.
    * Un prototipo es una referencia implícita a otro objeto que se consulta en la búsqueda de propiedades.
    * La herencia en javascript funciona basada en prototipos. 

### Funciones

* Una función es un objeto, que puede ser utilizado como cualquier otro valor.
* **Ejemplos:**
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

        `obj.fn(); //` **`Imprime 12345`**

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

        `obj2.fn(); //` **`Imprime 2`**

        `obj.fn(); //` **`Imprime 1`**
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

      `fn.call(obj2); //` **`Imprime 2`**

      `fn.call(obj1); //` **`Imprime 1`**

      `fn.call({`

          `id: 'testing'`

      `}); //` **`Imprime testing`**
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

        `offsetter(1) //` **`Imprime 1000 (999 + 1)`**
    * No tiene la propiedad prototype.
      * `function normalFunction() {}`

        `const fatArrowFunction = () => {}`

        `console.log(typeof normalFunction.prototype) //` **`Imprime 'object'`**

        `console.log(typeof fatArrowFunction.prototype) //` **`Imprime 'undefined'`**



