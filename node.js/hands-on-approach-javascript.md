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

### Herencia de prototipos

* Existen varios enfoques y variaciones de cadena de prototipos.
* Funcional:
  * Ejemplo:
    * `const employee = {`

          `salary: function() {`

              ``console.log(`Nombre: ${this.name} y gana $.3,000.00`);``

          `}`

      `};`

      `const salesperson = Object.create(employee, {`

          `sell: {`

              `value: function() {`

                  ``console.log(`Nombre del vendedor: ${this.name}`);``

              `}`

          `}`

      `});`

      `const smith = Object.create(salesperson, {`

          `name: {`

              `value: 'Smith Peterson'`

          `}`

      `});`

      `smith.sell(); // Nombre del vendedor: Smith Peterson` 

      `smith.salary(); // Nombre: Smith Peterson y gana $.3,000.00`

      `console.log(Object.getPrototypeOf(smith) === salesperson); // true`

      `console.log(Object.getPrototypeOf(salesperson) === employee); // true`

      * Describiendo la cadena de prototipos:
        * El prototipo de **`smith`** es **`salesperson`**.
        * El prototipo de **`salesperson`** es **`employee`**.
        * El prototipo de **`employee`** es **`Object.prototype`**.
      * Los pasos que realizó el runtime de javascript para **`smith.salary();`**
        * Verifica si `smith` tiene una propiedad `salary`; _no la tiene_.
        * Verifica si el prototipo de `smith` \(`salesperson`\) tiene una propiedad `salary`; _no la tiene_.
        * Verifica si el prototipo de `salesperson` \(`employee`\) tiene una propiedad `salary`; _**si la tiene**_.
  * El segundo argumento de **`Object.create`** es un objeto opcional conocido como **`Descriptor de propiedad` \(Properties descriptor\)** y contiene claves que se convertirán en el nombre de la clave del objeto creado que describe las características de las propiedades de otro objeto.
  * **`Object.getOwnPropertyDescriptor`** es utilizado para obtener un descriptor en cualquier objeto.
    *  `node - p "Object.getOwnPropertyDescriptor(global, 'process')"`

       `{`

           `get: [Function: get],`

           `set: [Function: set],`

           `enumerable: false,`

           `configurable: true`

       `}`



      * El descriptor puede utilizar un valor de una propiedad o get/set para crear una propiedad getter/setter.
      * Las propiedades que están asociadas con la metadata para las propiedades \(Como predeterminado están en false\):
        * **Writeable**: Determina si la propiedad puede reasignarse.
        * **Enumerable:**  Determina si la propiedad se enumerará, en la propiedad iterador como **`Object.keys`**.
        * **Configurable:** Establece si el descriptor en sí puede modificarse.



