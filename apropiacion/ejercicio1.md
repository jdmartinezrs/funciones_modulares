# Sistema de Saludo Personalizado

Proyecto modular de Node.js para generar saludos personalizados desde consola con entrada asíncrona y separación estricta de responsabilidades.

---

## Requisitos Funcionales

- RF01 — El sistema debe recibir un nombre como entrada desde la consola.
- RF02 — Debe existir una función `saludoPersonalizado` que reciba el nombre y retorne un mensaje de bienvenida estructurado.
- RF03 — El mensaje retornado debe incluir el nombre recibido como parte del texto.
- RF04 — El sistema debe mostrar el resultado en consola una vez generado.
- RF05 — La entrada del usuario debe ser leída de forma asíncrona mediante `readline`.

## Requisitos No Funcionales

- RNF01 — El proyecto debe usar módulos ES6 (`import`/`export`) sin `require`.
- RNF02 — La lógica de saludo debe estar en un módulo independiente (`greet/saludoPersonalizado.js`).
- RNF03 — Las exportaciones deben centralizarse mediante un archivo barril (`greet/index.js`).
- RNF04 — El archivo `index.js` solo orquesta el flujo: entrada → lógica → salida.
- RNF05 — El proyecto debe declarar `"type": "module"` en `package.json`.
- RNF06 — El código debe seguir convenciones de nombrado en camelCase.
- RNF07 — No deben existir dependencias externas; solo módulos nativos de Node.js.

---

## Prompt de Desarrollo

Genera un proyecto Node.js con módulos ES6 (sin `require`, solo `import`/`export`) que implemente un sistema de saludo personalizado por consola.

### Instrucciones para el prompt

El prompt debe generar exactamente la siguiente estructura limpia de archivos:

```
reto1/
├── package.json
├── index.js
└── greet/
    ├── index.js
    └── saludoPersonalizado.js
```

### Especificaciones por archivo

**`package.json`**
- Nombre del paquete: `sistema-saludo-personalizado`
- Versión: `1.0.0`
- `"type": "module"` para habilitar ES6.
- Script `start` que ejecute `node index.js`.
- Sin dependencias externas.

**`greet/saludoPersonalizado.js`**
- Exporta con `export` la función `saludoPersonalizado(nombre)`.
- Recibe un `string` con el nombre del usuario.
- Retorna el mensaje: `¡Bienvenido/a, ${nombre}! Nos alegra tenerte aquí.`

**`greet/index.js`** *(archivo barril)*
- Reexporta `saludoPersonalizado` desde `./saludoPersonalizado.js`.
- Sirve como punto único de importación del módulo `greet`.

**`index.js`**
- Importa `saludoPersonalizado` desde `./greet/index.js`.
- Crea una interfaz `readline` con `createInterface` de `node:readline`.
- Declara una función `main` marcada como `async`.
- Envuelve la pregunta de `readline` en una `Promise` para usar `await`.
- Pregunta al usuario: `Ingrese su nombre: `.
- Llama a `saludoPersonalizado` con el valor recibido.
- Imprime el resultado en consola.
- Cierra la interfaz `readline` al finalizar.
- Llama a `main()` al final del archivo.

### Comportamiento esperado en consola

```text
=== Sistema de Saludo Personalizado ===

Ingrese su nombre: María

¡Bienvenido/a, María! Nos alegra tenerte aquí.
```

### Restricciones técnicas

- Prohibido usar `require`.
- Prohibido usar librerías externas (`readline-sync`, `prompts`, etc.).
- Prohibido colocar lógica de negocio en `index.js`.
- El archivo barril `greet/index.js` debe reexportar, no redefinir.
