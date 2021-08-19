---
description: >-
  Node.js es un entorno de javascript impulsado por eventos con ejecución
  asíncrona y está diseñado para construir aplicaciones de red escalables.
---

# Echemos un vistazo

## **Instalación**

* No es recomendable instalar node.js con un package manager como apt \(Debian/Ubuntu\), brew \(macOS\), Chocolatey \(Windows\), ya que tienden a cambiar la ubicación de archivos o carpetas binarias, y configuración no estandarizada, eso puede ocasionar problemas de compatibilidad.
* Otro problema significativo es la instalación de módulos globales \(npm\) que requieren el uso de _**`sudo`**_ \(Root privileges\), eso no es ideal para el ambiente de un programador, ya que estaríamos otorgando privilegios a librerías de terceros que podrían vulnerar nuestra seguridad.
* La recomendación para instalarlo es descargarlo desde la página web o utilizar un version manager \(NVM\).

### MacOS y Linux

Para esta instalación asumo que utilizas Bash, Sh, o Zsh, también es necesario tener instalado curl.

#### Instalar nvm:

```bash
curl -o- ht‌tps://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash
```

#### Para verificar si la instalación fue exitosa:

```bash
nvm -version
```

#### Para instalar la última versión LTS \(Long-term support\):

```bash
nvm install --lts
```

Si en algún momento deseas desinstalar la versión de node:

```bash
nvm uninstall --lts
```

{% hint style="info" %}
Para información detallada de nvm, puedes consultar [https://github.com/nvm-sh/nvm](https://github.com/nvm-sh/nvm).
{% endhint %}

#### Para verificar la versión de node:

```bash
node -v || node --version
```

### **Windows**

1. A diferencia de nvm para linux o macOS, en windows existe nvs \(Node version switcher\), para instalarlo es necesario descargar el instalador MSI: [https://github.com/jasongin/nvs/releases](https://github.com/jasongin/nvs/releases)
2. Ejecuta el archivo MSI y seguir los pasos para instalarlo.
3. Ejecuta en una terminal o command prompt para agregar la última versión LTS: **`nvs add lts`.**
4. Para activar la nueva versión, ejecuta lo siguiente:**`nvs use lts`.**
5. Para verificar la versión de node: **`node -v`.**



