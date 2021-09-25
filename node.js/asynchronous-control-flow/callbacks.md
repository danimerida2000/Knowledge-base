# Callbacks

{% hint style="success" %}
* **Un callback** es una función que se llamará en algún momento al finalizar una tarea.
* El primer argumento de un callback por convención es un objeto error, comúnmente conocido como **`Errback`**.
{% endhint %}

## Ejecución paralela

#### Ejemplo:

Crearemos tres archivos de diferente tamaño.

{% tabs %}
{% tab title="smallFile.txt" %}
```bash
for i in {1..1000}; do echo 'test'; done >> smallFile.txt
```
{% endtab %}

{% tab title="MediumFile.txt" %}
```bash
for i in {1..10000}; do echo 'test'; done >> mediumFile.txt
```
{% endtab %}

{% tab title="BigFile.txt" %}
```bash
for i in {1..100000}; do echo 'test'; done >> bigFile.txt
```
{% endtab %}
{% endtabs %}

![Archivos creados](../../.gitbook/assets/image%20%2828%29.png)

Desarrollaremos un lector de archivos con ejecución paralela.

```javascript
const { readFile } = require('fs') // Módulo de gestión de archivos
const Path = require('path') // Módulo para trabajar con rutas de archivos y directorios.

const fileContent = (err, content) => {
  if(err){
    console.error(err)
    return
  }
  console.log(content.toString()) // Mostramos en pantalla el contenido del archivo
}

readFile(Path.join(__dirname, 'bigFile.txt'), fileContent)
readFile(Path.join(__dirname, 'mediumFile.txt'), fileContent)
readFile(Path.join(__dirname, 'smallFile.txt'), fileContent)
```

Si observamos el fragmento de código de la línea 12 a 14, primero imprimirá el contenido del archivo **smallFile.txt** y de último el contenido del archivo **bigFile.txt**, ya que la ejecución no es en serie, eso quiere decir, que no esperará que finalice de ejecutar la instrucción, si no continuará.

## Ejecución serial

Tomaremos como referencia el ejemplo anterior y lo adecuamos para mostrar la ejecución serial:

```javascript
const { readFile } = require('fs') // Módulo de gestión de archivos
const Path = require('path') // Módulo para trabajar con rutas de archivos y directorios.

const fileContent = (err, content) => {
  if(err){
    console.error(err)
    return
  }
  console.log(content.toString()) // Mostramos en pantalla el contenido del archivo
}

readFile(Path.join(__dirname, 'smallFile.txt'), (err, content) => {
  fileContent(err, content)
  readFile(Path.join(__dirname, 'mediumFile.txt'), (err, content) => {
    fileContent(err, content)
    readFile(Path.join(__dirname, 'bigFile.txt'), fileContent)
  })
})
```

