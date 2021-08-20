# Funciones de constructor

{% hint style="success" %}
* Todas las funciones tienen prototipos.
* El enfoque del constructor para crear una cadena de prototipos es definir propiedades en el objeto prototipo que después se llamará con _**new**_.
* Cada función tiene un objeto prototipo preexistente.
{% endhint %}

#### Ejemplo:

{% hint style="info" %}
Usaremos **Pascal Case** para las funciones que serán llamadas con _**new**_, ya que es una convención y es recomendable.
{% endhint %}

```javascript
function Employee(name) {
  this.name = name;
}

Employee.prototype.salary = function () {
  console.log(`Su salario es de $.12,000.00`);
};

function Salesperson(name) {
  Employee.call(this, name);
}

function inherit(proto) {
  function ChainLink() {}
  ChainLink.prototype = proto;
  return new ChainLink();
}

Salesperson.prototype = inherit(Employee.prototype);

Salesperson.prototype.sell = function () {
  console.log(`Es vendido por ${this.name}`);
};

const smith = new Salesperson('Smith Peterson');
smith.sell(); // Es vendido por Smith Peterson
smith.salary(); // Su salario es de $.12,000.00
console.log(Object.getPrototypeOf(smith) === Salesperson.prototype); // true
console.log(Object.getPrototypeOf(Salesperson.prototype) === Employee.prototype); // true
```

Descripción de la cadena de prototipos:

* El prototipo de **`smith`** es **`salesperson.prototype`**.
* El prototipo de **`salesperson`** es **`employee.prototype`**.
* El prototipo de **`employee`** es **`Object.prototype`**.

El uso del método **call** en una función permite que el objeto **this** de la función a la que se llama se establezca a través del primer argumento pasado a call.

Para el runtime que soporta ES6+, podemos obtener lo mismo con **Object.create**:

```javascript
function Salesperson(name) {
  Employee.call(this, name);
}

Salesperson.prototype = Object.create(Employee.prototype);

Salesperson.prototype.sell = function () {
  console.log(`Es vendido por ${this.name}`);
};
```

Node.js tiene una función llamada **util.inherits**:

```javascript
const util = require('util');

function Salesperson(name) {
  Employee.call(this, name);
}

Salesperson.prototype.sell = function () {
  console.log(`Es vendido por ${this.name}`);
};

util.inherits(Salesperson.prototype, Employee.prototype); // Object.setPrototypeOf(Salesperson.prototype, Employee.prototype)
```





