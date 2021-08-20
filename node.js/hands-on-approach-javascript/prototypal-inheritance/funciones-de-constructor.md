# Funciones de constructor

{% hint style="success" %}
Todas las funciones tienen prototipos.
{% endhint %}

{% hint style="success" %}
El enfoque del constructor para crear una cadena de prototipos es definir propiedades en el objeto prototipo que después se llamará con la palabra clave **`new`**.
{% endhint %}

#### Ejemplo:

```javascript
function employee(name) {
  this.name = name;
}

employee.prototype.salary = function () {
  console.log(`Su salario es de $.12,000.00`);
};

function salesperson(name) {
  employee.call(this, name);
}

function inherit(proto) {
  function ChainLink() {}
  ChainLink.prototype = proto;
  return new ChainLink();
}

salesperson.prototype = inherit(employee.prototype);

salesperson.prototype.sell = function () {
  console.log(`Es vendido por ${this.name}`);
};

const smith = new salesperson('Smith Peterson');
smith.sell(); // Es vendido por Smith Peterson
smith.salary(); // Su salario es de $.12,000.00
console.log(Object.getPrototypeOf(smith) === salesperson.prototype); // true
console.log(Object.getPrototypeOf(salesperson.prototype) === employee.prototype); // true

```

