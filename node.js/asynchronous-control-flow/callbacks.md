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



