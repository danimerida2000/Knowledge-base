---
description: >-
  Node.js es un entorno de javascript impulsado por eventos con ejecución
  asíncrona y está diseñado para construir aplicaciones de red escalables.
---

# Echemos un vistazo

## **Instalación**

* No es recomendable instalar node.js con un package manager como apt \(Debian/Ubuntu\), brew en macOs, Chocolatey en Windows, ya que tienden a cambiar la ubicación de archivos o carpetas binarias, y configuración no estandarizada, eso puede ocasionar problemas de compatibilidad.
* Otro problema significativo es la instalación de módulos globales \(npm\) que requieren el uso de _**sudo**_ \(Root privileges\), eso no es ideal para el ambiente de un programador, ya que estaríamos otorgando privilegios a librerías de terceros que podrían vulnerar nuestra seguridad.
* La recomendación para instalarlo es descargarlo desde la página web o utilizar un version manager \(NVM\).

### MacOS y Linux

1. Para está instalación asumo que utilizas Bash, Sh, o Zsh, también es necesario tener instalado curl.
2. Instalar nvm: **curl -o- ht‌tps://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh \| bash**
3. Para verificar si la instalación fue exitosa, ejecuta lo siguiente: **command -v nvm** 
4. Para instalar la última versión LTS \(Long-term support\) ejecuta lo siguiente: **nvm install --lts**
5. Si en algún momento deseas desinstalar la versión de node, ejecuta lo siguiente: nvm uninstall --lts, para información detallada de nvm, puedes consultar [https://github.com/nvm-sh/nvm](https://github.com/nvm-sh/nvm).
6. Para verificar la versión de node: **node -v** o también **node --version**



