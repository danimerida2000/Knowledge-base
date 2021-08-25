# Inicializando paquetes

### Comando npm

**`npm help`** muestra la lista de comandos disponibles:

```text
➜  ~ npm help

Usage: npm <command>

where <command> is one of:
    access, adduser, audit, bin, bugs, c, cache, ci, cit,
    clean-install, clean-install-test, completion, config,
    create, ddp, dedupe, deprecate, dist-tag, docs, doctor,
    edit, explore, fund, get, help, help-search, hook, i, init,
    install, install-ci-test, install-test, it, link, list, ln,
    login, logout, ls, org, outdated, owner, pack, ping, prefix,
    profile, prune, publish, rb, rebuild, repo, restart, root,
    run, run-script, s, se, search, set, shrinkwrap, star,
    stars, start, stop, t, team, test, token, tst, un,
    uninstall, unpublish, unstar, up, update, v, version, view,
    whoami

npm <command> -h  quick help on <command>
npm -l            display full usage info
npm help <term>   search for help on <term>
npm help npm      involved overview

Specify configs in the ini-formatted file:
    /Users/danimerida2000/.npmrc
or on the command line via: npm <command> --key value
Config info can be viewed via: npm help config

npm@6.14.14 /opt/homebrew/Cellar/node@12/12.22.5/lib/node_modules/npm
```

El argumento **`-h`** nos muestra la referencia de ayuda de un comando:

```text
➜  ~ npm install -h

npm install (with no args, in package dir)
npm install [<@scope>/]<pkg>
npm install [<@scope>/]<pkg>@<tag>
npm install [<@scope>/]<pkg>@<version>
npm install [<@scope>/]<pkg>@<version range>
npm install <alias>@npm:<name>
npm install <folder>
npm install <tarball file>
npm install <tarball url>
npm install <git:// url>
npm install <github username>/<github project>

aliases: i, isntall, add
common options: [--save-prod|--save-dev|--save-optional] [--save-exact] [--no-save]
```

{% hint style="success" %}
Un paquete \(aplicación/servicio\) es una carpeta con un archivo **package.json.**
{% endhint %}

El comando **`npm init`** es utilizado para crear el archivo package.json.

#### Ejemplo:

```bash
➜  package-test npm init
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help init` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
package name: (package-test) project-test
version: (1.0.0) 0.1.0
description: Project test
entry point: (index.js) app.js
test command:
git repository:
keywords:
author: Danilo Mérida
license: (ISC) MIT
About to write to /Users/danimerida2000/Downloads/package-test/package.json:

{
  "name": "project-test",
  "version": "0.1.0",
  "description": "Project test",
  "main": "app.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Danilo Mérida",
  "license": "MIT"
}


Is this OK? (yes)
```

```bash
➜  package-test cat package.json
{
  "name": "project-test",
  "version": "0.1.0",
  "description": "Project test",
  "main": "app.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Danilo Mérida",
  "license": "MIT"
}
```

{% hint style="info" %}
Si deseamos que obtenga los valores predeterminados, usamos el flag -y \(**`npm install -y`**\)
{% endhint %}



