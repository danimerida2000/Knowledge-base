# Constructor \(Class-Syntax\)

{% hint style="success" %}
* ES6+ tiene una palabra reservada llamada **class**, pero es importante no confundirlo de cómo lo maneja la programación orientada a objetos \(OOP\), es decir, que crea una cadena de prototipos que provee una herencia, y que es opuesto a la herencia clásica \(OOP\).
* **Class** crea una función que posteriormente se llamará con **new**, es muy similar a la función de constructor \(Constructor function\) que vimos en la sección anterior.
{% endhint %}

#### **Ejemplo:**

```javascript
class Employee {
  constructor(name) {
    this.name = name;
  }
  salary() {
    console.log(`Su salario es de $.12,000.00`);
  }
}

class Salesperson extends Employee {
  constructor(name) {
    super(name);
  }
  sell() {
    console.log(`Es vendido por ${this.name}`);
  }
}

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

{% hint style="info" %}
La palabra reservada **extends** hace que la herencia sea mucho más sencilla. La clase Salesperson extiende a Employee asegurará que el prototipo de Salesperson.prototype será Employee.prototype.
{% endhint %}

#### Comparación:

{% tabs %}
{% tab title="Class-Syntax" %}
```javascript
class Employee {
  constructor(name) {
    this.name = name;
  }
  salary() {
    console.log(`Su salario es de $.12,000.00`);
  }
}

class Salesperson extends Employee {
  constructor(name) {
    super(name);
  }
  sell() {
    console.log(`Es vendido por ${this.name}`);
  }
}

const smith = new Salesperson('Smith Peterson');

smith.sell(); // Es vendido por Smith Peterson
smith.salary(); // Su salario es de $.12,000.00
console.log(Object.getPrototypeOf(smith) === Salesperson.prototype); // true
console.log(Object.getPrototypeOf(Salesperson.prototype) === Employee.prototype); // true
```
{% endtab %}

{% tab title="Constructor function" %}
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
{% endtab %}

{% tab title="Functional" %}
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
{% endtab %}
{% endtabs %}

