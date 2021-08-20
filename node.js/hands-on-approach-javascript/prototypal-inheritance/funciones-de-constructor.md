# Funciones de constructor

{% hint style="success" %}
Todas las funciones tienen prototipos.
{% endhint %}

{% hint style="success" %}
El enfoque del constructor para crear una cadena de prototipos es definir propiedades en el objeto prototipo que después se llamará con la palabra clave **`new`**.
{% endhint %}

#### Ejemplo:

{% hint style="info" %}
Usaremos **Pascal Case** para las funciones que serán llamadas con new, ya que es una convención y es recomendado.
{% endhint %}

```javascript
function Employee(name) {
  this.name = name;
}

Employee.prototype.salary = function () {
  console.log(`Su salario es de $.12,000.00`);
};

function Salesperson(name) {
  employee.call(this, name);
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
console.log(Object.getPrototypeOf(smith) === salesperson.prototype); // true
console.log(Object.getPrototypeOf(salesperson.prototype) === employee.prototype); // true
```



