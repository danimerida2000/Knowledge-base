# Herencia de prototipos

#### Existen varios enfoques y variaciones de cadena de prototipos:

{% page-ref page="funcional.md" %}

{% page-ref page="funciones-de-constructor.md" %}

{% page-ref page="constructor-class-syntax.md" %}

#### Después de revisar los temas que se describen anteriormente, comprenderemos el siguiente ejemplo:

{% tabs %}
{% tab title="Class-Syntax" %}
```javascript
const assert = require('assert');

class Leopard {
  constructor(name) {
    this.name = name;
  }
  hiss() {
    console.log(`${this.name}: hsss`);
  }
}

class Lynx extends Leopard {
  constructor(name) {
    super(name);
  }
  purr() {
    console.log(`${this.name}: prrr`);
  }
}

class Cat extends Lynx {
  constructor(name) {
    super(`${name} the cat`);
  }
  meow() {
    console.log(`${this.name}: meow`);
  }
}

const felix = new Cat('Felix');
felix.meow(); // Felix the cat: meow
felix.purr(); // Felix the cat: prrr
felix.hiss(); // Felix the cat: hsss

// Prototype checks...

const felixProto = Object.getPrototypeOf(felix);
const felixProtoProto = Object.getPrototypeOf(felixProto);
const felixProtoProtoProto = Object.getPrototypeOf(felixProtoProto);
assert(Object.getOwnPropertyNames(felixProto).length, 1);
assert(Object.getOwnPropertyNames(felixProtoProto).length, 1);
assert(Object.getOwnPropertyNames(felixProtoProto).length, 1);
assert(typeof felixProto.meow, 'function');
assert(typeof felixProtoProto.purr, 'function');
assert(typeof felixProtoProtoProto.hiss, 'function');
console.log('prototype checks passed!');

```
{% endtab %}

{% tab title="Constructor function" %}
```javascript
const assert = require('assert');

function Leopard(name) {
  this.name = name;
}

Leopard.prototype.hiss = function () {
  console.log(`${this.name}: hsss`);
};

function Lynx(name) {
  Leopard.call(this, name);
}

function inherit(proto) {
  function ChainLink() {}
  ChainLink.prototype = proto;
  return new ChainLink();
}

Lynx.prototype = inherit(Leopard.prototype);

Lynx.prototype.purr = function () {
  console.log(`${this.name}: prrr`);
};

function Cat(name) {
  Lynx.call(this, `${name} the cat`);
}

Cat.prototype = inherit(Lynx.prototype);

Cat.prototype.meow = function () {
  console.log(`${this.name}: meow`);
};

const felix = new Cat('Felix');
felix.meow(); // Felix the cat: meow
felix.purr(); // Felix the cat: prrr
felix.hiss(); // Felix the cat: hsss

// Prototype checks...

const felixProto = Object.getPrototypeOf(felix);
const felixProtoProto = Object.getPrototypeOf(felixProto);
const felixProtoProtoProto = Object.getPrototypeOf(felixProtoProto);
assert(Object.getOwnPropertyNames(felixProto).length, 1);
assert(Object.getOwnPropertyNames(felixProtoProto).length, 1);
assert(Object.getOwnPropertyNames(felixProtoProto).length, 1);
assert(typeof felixProto.meow, 'function');
assert(typeof felixProtoProto.purr, 'function');
assert(typeof felixProtoProtoProto.hiss, 'function');
console.log('prototype checks passed!');

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



