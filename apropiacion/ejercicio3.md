# Sistema Contador Secuencial

Proyecto modular de Node.js para contar desde 1 hasta un número dado, implementando primero una función tradicional con ciclo y luego su equivalente como función flecha, con entrada asíncrona desde consola.

---

## Requisitos Funcionales

- RF01 — El sistema debe solicitar un número entero positivo desde la consola.
- RF02 — Debe existir una función `contarHasta(n)` implementada como función tradicional con ciclo `for`.
- RF03 — La función debe imprimir en consola todos los números del `1` hasta `n` inclusive.
- RF04 — Debe existir una versión equivalente `contarHastaFlecha` implementada como función flecha (`=>`).
- RF05 — Ambas implementaciones deben producir el mismo resultado.
- RF06 — El sistema debe ejecutar ambas versiones y mostrar sus resultados diferenciados en consola.

## Requisitos No Funcionales

- RNF01 — El proyecto debe usar módulos ES6 (`import`/`export`) sin `require`.
- RNF02 — La función tradicional debe residir en `counter/contarHasta.js`.
- RNF03 — La función flecha debe residir en `counter/contarHastaFlecha.js`.
- RNF04 — Las exportaciones deben centralizarse en el barril `counter/index.js`.
- RNF05 — La validación del número debe estar en `utils/isPositiveInt.js` y reexportarse desde `utils/index.js`.
- RNF06 — `index.js` solo orquesta: entrada → validación → ejecución de ambas funciones.
- RNF07 — `"type": "module"` en `package.json`.

---

## Prompt de Desarrollo

Genera un proyecto Node.js con módulos ES6 (sin `require`, solo `import`/`export`) que implemente un sistema contador secuencial con función tradicional y función flecha.

### Instrucciones para el prompt

El prompt debe generar exactamente la siguiente estructura limpia de archivos:

```
reto3/
├── package.json
├── index.js
├── utils/
│   ├── index.js
│   └── isPositiveInt.js
└── counter/
    ├── index.js
    ├── contarHasta.js
    └── contarHastaFlecha.js
```

### Especificaciones por archivo

**`package.json`**
- Nombre: `sistema-contador-secuencial`
- `"type": "module"`.
- Script `start`: `node index.js`.

**`utils/isPositiveInt.js`**
- Exporta `isPositiveInt(valor)`.
- Retorna `true` si el valor es una cadena que representa un entero positivo (regex `/^\d+$/` y valor `> 0`).
- Retorna `false` en cualquier otro caso.

**`utils/index.js`** *(archivo barril)*
- Reexporta `isPositiveInt`.

**`counter/contarHasta.js`**
- Exporta `contarHasta(n)` como función tradicional (`function`).
- Usa un ciclo `for` para imprimir cada número del `1` al `n`.

**`counter/contarHastaFlecha.js`**
- Exporta `contarHastaFlecha` como función flecha (`const contarHastaFlecha = (n) => { ... }`).
- Usa un ciclo `for` internamente, misma lógica que la versión tradicional.

**`counter/index.js`** *(archivo barril)*
- Reexporta `contarHasta` y `contarHastaFlecha`.

**`index.js`**
- Importa ambas funciones desde `./counter/index.js` e `isPositiveInt` desde `./utils/index.js`.
- Función `main` asíncrona con `readline` y `await`.
- Solicita el número al usuario.
- Valida con `isPositiveInt`; si es inválido, vuelve a pedir.
- Convierte con `parseInt(..., 10)`.
- Ejecuta `contarHasta` mostrando un encabezado `"--- Función Tradicional ---"`.
- Ejecuta `contarHastaFlecha` mostrando un encabezado `"--- Función Flecha ---"`.

### Comportamiento esperado en consola

```text
=== Sistema Contador Secuencial ===

Ingrese un número entero positivo: 5

--- Función Tradicional ---
1
2
3
4
5

--- Función Flecha ---
1
2
3
4
5
```

### Restricciones técnicas

- Prohibido usar `require`.
- `contarHasta` debe usar `function` explícita (no flecha).
- `contarHastaFlecha` debe usar sintaxis `=>` obligatoriamente.
- Ambos ciclos deben ser `for`, no `while` ni recursión.
