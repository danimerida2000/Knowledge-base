---
description: La herencia en JavaScript se logra con una cadena de prototipos.
---

# Funcional

#### Ejemplo:

```javascript
const employee = {
  salary: function () {
    console.log(`Su salario es de $.12,000.00`);
  }
};
const salesperson = Object.create(employee, {
  sell: {
    value: function () {
      console.log(`Es vendido por ${this.name}`);
    }
  }
});
const smith = Object.create(salesperson, {
  name: {
    value: 'Smith Peterson'
  }
});
smith.sell(); // Es vendido por Smith Peterson
smith.salary(); // Su salario es de $.12,000.00
console.log(Object.getPrototypeOf(smith) === salesperson); // true
console.log(Object.getPrototypeOf(salesperson) === employee); // true
```

#### Describiendo la cadena de prototipos:

* El prototipo de **`smith`** es **`salesperson`**.
* El prototipo de **`salesperson`** es **`employee`**.
* El prototipo de **`employee`** es **`Object.prototype`**.

Los pasos que realizó el runtime de javascript para **`smith.salary();`**

1. [x] Verifica si `smith` tiene una propiedad `salary`; _**no la tiene**_.
2. [x] Verifica si el prototipo de `smith` \(`salesperson`\) tiene una propiedad `salary`; _**no la tiene**_.
3. [x] Verifica si el prototipo de `salesperson` \(`employee`\) tiene una propiedad `salary`; _**si la tiene**_.

{% hint style="info" %}
El segundo argumento de **`Object.create`** es un objeto opcional conocido como **`Descriptor de propiedades` \(Properties descriptor\)** y contiene claves que se convertirán en el nombre de la clave del objeto creado que describe las características de las propiedades de otro objeto.
{% endhint %}

**`Object.getOwnPropertyDescriptor`** es utilizado para obtener un descriptor en cualquier objeto:

```bash
node - p "Object.getOwnPropertyDescriptor(global, 'process')"
 {
     get: [Function: get],
     set: [Function: set],
     enumerable: false,
     configurable: true
 }
```

El descriptor puede utilizar un valor de una propiedad get/set.

Las propiedades que están asociadas con la metadata del objeto:

* **Writeable**: Determina si la propiedad puede reasignarse.
* **Enumerable:**  Default false; determina si la propiedad se enumerará, en la propiedad iterador como **`Object.keys`**.
* **Configurable:** Default false; establece si el descriptor en sí puede modificarse.

