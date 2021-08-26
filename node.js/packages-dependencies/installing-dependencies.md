# Dependencias

## Instalando dependencias

{% hint style="success" %}
Para instalar una dependencia, ejecutar **`npm install nombre_paquete`**:
{% endhint %}

#### Ejemplo:

```javascript
➜  package-test npm install signale
npm WARN project-test@0.1.0 No repository field.

+ signale@1.4.0
updated 1 package and audited 24 packages in 1.785s
found 0 vulnerabilities
```

Se actualizó package.json:

```javascript
{
  "name": "project-test",
  "version": "0.1.0",
  "description": "Project test",
  "main": "app.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Danilo Mérida",
  "license": "MIT",
  "dependencies": {
    "signale": "^1.4.0"
  }
}
```

Echemos un vistazo a la carpeta **node\_modules** y veamos el árbol de dependencias:

```javascript
➜  package-test ls -lah node_modules
total 0
drwxr-xr-x  26 danimerida2000  staff   832B Aug 25 19:57 .
drwxr-xr-x   6 danimerida2000  staff   192B Aug 25 19:49 ..
drwxr-xr-x   6 danimerida2000  staff   192B Aug 25 19:29 ansi-styles
drwxr-xr-x   9 danimerida2000  staff   288B Aug 25 19:29 chalk
drwxr-xr-x   9 danimerida2000  staff   288B Aug 25 19:29 color-convert
drwxr-xr-x   9 danimerida2000  staff   288B Aug 25 19:29 color-name
drwxr-xr-x   6 danimerida2000  staff   192B Aug 25 19:29 error-ex
drwxr-xr-x   6 danimerida2000  staff   192B Aug 25 19:29 escape-string-regexp
drwxr-xr-x   6 danimerida2000  staff   192B Aug 25 19:29 figures
drwxr-xr-x   6 danimerida2000  staff   192B Aug 25 19:29 find-up
drwxr-xr-x   9 danimerida2000  staff   288B Aug 25 19:29 graceful-fs
drwxr-xr-x   6 danimerida2000  staff   192B Aug 25 19:29 has-flag
drwxr-xr-x  10 danimerida2000  staff   320B Aug 25 19:29 is-arrayish
drwxr-xr-x   7 danimerida2000  staff   224B Aug 25 19:29 json-parse-better-errors
drwxr-xr-x   6 danimerida2000  staff   192B Aug 25 19:29 load-json-file
drwxr-xr-x   6 danimerida2000  staff   192B Aug 25 19:29 locate-path
drwxr-xr-x   6 danimerida2000  staff   192B Aug 25 19:29 p-limit
drwxr-xr-x   6 danimerida2000  staff   192B Aug 25 19:29 p-locate
drwxr-xr-x   6 danimerida2000  staff   192B Aug 25 19:29 p-try
drwxr-xr-x   6 danimerida2000  staff   192B Aug 25 19:29 parse-json
drwxr-xr-x   6 danimerida2000  staff   192B Aug 25 19:29 path-exists
drwxr-xr-x   6 danimerida2000  staff   192B Aug 25 19:29 pify
drwxr-xr-x   6 danimerida2000  staff   192B Aug 25 19:29 pkg-conf
drwxr-xr-x   8 danimerida2000  staff   256B Aug 25 19:57 signale
drwxr-xr-x   6 danimerida2000  staff   192B Aug 25 19:29 strip-bom
drwxr-xr-x   7 danimerida2000  staff   224B Aug 25 19:29 supports-color
```

```javascript
➜  package-test npm ls
project-test@0.1.0 /Users/danimerida2000/Downloads/package-test
└─┬ signale@1.4.0
  ├─┬ chalk@2.4.2
  │ ├─┬ ansi-styles@3.2.1
  │ │ └─┬ color-convert@1.9.3
  │ │   └── color-name@1.1.3
  │ ├── escape-string-regexp@1.0.5
  │ └─┬ supports-color@5.5.0
  │   └── has-flag@3.0.0
  ├─┬ figures@2.0.0
  │ └── escape-string-regexp@1.0.5 deduped
  └─┬ pkg-conf@2.1.0
    ├─┬ find-up@2.1.0
    │ └─┬ locate-path@2.0.0
    │   ├─┬ p-locate@2.0.0
    │   │ └─┬ p-limit@1.3.0
    │   │   └── p-try@1.0.0
    │   └── path-exists@3.0.0
    └─┬ load-json-file@4.0.0
      ├── graceful-fs@4.2.8
      ├─┬ parse-json@4.0.0
      │ ├─┬ error-ex@1.3.2
      │ │ └── is-arrayish@0.2.1
      │ └── json-parse-better-errors@1.0.2
      ├── pify@3.0.0
      └── strip-bom@3.0.0
```

{% hint style="info" %}
Si existiese 2 versiones en el árbol de dependencias puede almacenar una carpeta node\_modules anidada.
{% endhint %}

## Dependencias de desarrollo

{% hint style="success" %}
* Hay que tomar en cuenta que no todas las dependencias son requeridas para producción, algunas librerías son utilizadas para el proceso de desarrollo.
* Cuando ejecutamos **`run npm`** solamente podremos ver el árbol de dependencias de producción.
{% endhint %}

Para instalar una dependencia de desarrollo, ejecutamos **`npm install --save-dev nombre_paquete`**.

#### Ejemplo:

```javascript
➜  package-test npm install --save-dev json-loader
npm WARN project-test@0.1.0 No repository field.

+ json-loader@0.5.7
added 1 package from 1 contributor and audited 25 packages in 2.697s
found 0 vulnerabilities
```

