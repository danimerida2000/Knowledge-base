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
    * `const obj = {`

          `id: 12345,`

          `fn: function() {`

              `console.log(this.id);`

          `}`

      `};`

      `obj.fn(); // imprime 12345`
  * 



