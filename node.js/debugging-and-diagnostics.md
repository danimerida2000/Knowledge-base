---
description: >-
  El proceso de depuración en Node.js debe empezar en modo Inspect que expone un
  protocolo remoto que puede ser conectado y permite diagnosticar a través de
  puntos de interrupción.
---

# Depuración y diagnóstico

### Objetivos

* Iniciar un proceso en modo inspect.
* Conectar un proceso en modo inspect para depurarlo.
* Comprender que son los breakpoints \(puntos de ruptura o interrupción\).

### Inicio de modo inspección

Node.js soporta el protocolo de depuración remota como chrome DevTools.

Para activar el modo inspección: **`node --inspect index.js`**

Activar el modo inspección pero iniciando con un breakpoint activo al inicio del programa: **`node --inspect-brk index.js`**

Si no utilizamos los flags anteriores, la aplicación se inicializará por completo y estará realizando tareas asíncronas antes de que pueda establecer los breakpoints.

**Ejemplo utilizando Chrome Devtools:**

\*\*\*\*









