# Herencia de prototipos

Existen varios enfoques y variaciones de cadena de prototipos.

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



      * El descriptor puede utilizar un valor de una propiedad o get/set para crear propiedades getter/setter.
      * Las propiedades que están asociadas con la metadata del objeto \(Como predeterminado están en false\):
        * **Writeable**: Determina si la propiedad puede reasignarse.
        * **Enumerable:**  Determina si la propiedad se enumerará, en la propiedad iterador como **`Object.keys`**.
        * **Configurable:** Establece si el descriptor en sí puede modificarse.
* Funciones de constructor \(Constructor Functions\)
  * Todas las funciones tienen prototipos.
  * El enfoque del constructor para crear una cadena de prototipos es definir propiedades en el objeto prototipo que después se llamará con new.
  * 

