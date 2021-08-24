# Closure scope

{% hint style="success" %}
* Cuando una función está dentro de otra función, puede acceder tanto a su propio closure scope como al closure scope padre de la función externa.
* Las reglas de closure scope aplican también a las funciones fat arrow \(=&gt;\).
{% endhint %}

#### Ejemplos:

```javascript
function outerFunction() {
  let isEnabled = true;
  function getStatus() {
    console.log(isEnabled);
  }
  getStatus(); // imprime true
  isEnabled = false;
  getStatus(); // imprime false
}
outerFunction();
```

{% hint style="info" %}
* Si existiese una colisión con algún nombre de variable con la de un argumento de una función tomará la más cercana por prioridad de scope.
* Closure scope no puede ser accesible fuera de una función \(Provee una encapsulación de un estado privado\).
{% endhint %}

```javascript
function animal(type) {
  let id = 0;
  return (name) => {
    id += 1;
    return {
      id,
      type,
      name
    };
  };
}
const createDog = animal('dog');
const createCat = animal('cat');
const scott = createDog('Scott');
const firulais = createDog('Firulais');
const fifi = createCat('Fifi');
console.log(scott); // { id: 1, type: 'dog', name: 'Scott' }
console.log(firulais); // { id: 2, type: 'dog', name: 'Firulais' }
console.log(fifi); // { id: 1, type: 'cat', name: 'Fifi' }
```

{% hint style="info" %}
* La función _**animal**_ tiene una variable _**id**_ dentro de su scope, y toma el argumento _**type**_, y retorna una función con el id, tipo y nombre, ya que tiene acceso al closure scope de la función padre.
* La función _**animal**_ se invoca dos veces y es asignado a _**createDog**_ y _**createCat**_. Estas funciones tienen diferentes instancias de closure scope. Los objetos _**scott**_ y _**firulais**_ son instanciados por _**createDog**_.
{% endhint %}

El siguiente ejemplo es funcionalmente equivalente y al mismo nivel de composición que los ejemplos de herencia de prototipos:

```javascript
function employee() {
  const salary = () => {
    console.log(`Su salario es de $.12,000.00`);
  };
  return { salary };
}

function salesperson(name) {
  const sell = () => {
    console.log(`Es vendido por ${name}`);
  };
  return {
    ...employee(), // Spread operator (copy properties).
    sell
  };
}
const smith = salesperson('Smith Peterson');
smith.sell(); // Es vendido Smith Peterson
smith.salary(); // Su salario es de $.12,000.00
console.log(Object.getPrototypeOf(smith)); // {}
console.log(Object.getPrototypeOf(salesperson)); // [Function]
```

{% hint style="warning" %}
El ejemplo anterior no tiene una cadena de prototipos.
{% endhint %}

{% hint style="success" %}
* La principal ventaja al usar closure scope para componer objetos es que elimina la complejidad de los prototipos, contexto \(this\) y la necesidad de invocar la función con _**new**_.
* Es recomendable utilizar la composición de funciones en lugar de la herencia de prototipos y optimizar si es necesario.
{% endhint %}

