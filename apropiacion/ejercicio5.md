# Sistema Detector de Número Primo

Proyecto modular de Node.js para determinar si un número es primo, aplicando modularización estricta con funciones separadas para validación, conteo de divisores y presentación de resultado, con entrada asíncrona desde consola.

---

## Requisitos Funcionales

- RF01 — El sistema debe solicitar un número entero positivo desde la consola.
- RF02 — Debe existir una función `validarNumero(n)` que verifique que la entrada sea un entero mayor a `1`.
- RF03 — Debe existir una función `contarDivisores(n)` que retorne la cantidad total de divisores del número.
- RF04 — Debe existir una función `esPrimo(n)` que use el resultado de `contarDivisores` para determinar si el número es primo (exactamente 2 divisores: `1` y él mismo).
- RF05 — Debe existir una función `mostrarResultado(n, primo)` que imprima en consola el veredicto final.
- RF06 — El sistema debe mostrar claramente si el número **es primo** o **no es primo**.

## Requisitos No Funcionales

- RNF01 — El proyecto debe usar módulos ES6 (`import`/`export`) sin `require`.
- RNF02 — Cada función debe residir en su propio archivo dentro de `prime/`.
- RNF03 — Las exportaciones deben centralizarse en el barril `prime/index.js`.
- RNF04 — La validación de entrada desde consola debe estar en `utils/isValidInput.js` y reexportarse desde `utils/index.js`.
- RNF05 — `index.js` solo orquesta: entrada → validación → lógica → presentación.
- RNF06 — El nombrado de funciones y archivos debe ser descriptivo y en camelCase.
- RNF07 — Las funciones de lógica deben ser puras (sin `console.log` excepto `mostrarResultado`).
- RNF08 — `"type": "module"` en `package.json`.

---

## Prompt de Desarrollo

Genera un proyecto Node.js con módulos ES6 (sin `require`, solo `import`/`export`) que implemente un detector de números primos con diseño modular y separación de responsabilidades.

### Instrucciones para el prompt

El prompt debe generar exactamente la siguiente estructura limpia de archivos:

```
reto5/
├── package.json
├── index.js
├── utils/
│   ├── index.js
│   └── isValidInput.js
└── prime/
    ├── index.js
    ├── validarNumero.js
    ├── contarDivisores.js
    ├── esPrimo.js
    └── mostrarResultado.js
```

### Especificaciones por archivo

**`package.json`**
- Nombre: `sistema-detector-primo`
- `"type": "module"`.
- Script `start`: `node index.js`.

**`utils/isValidInput.js`**
- Exporta `isValidInput(valor)`.
- Retorna `true` si el valor es una cadena que representa un entero positivo mayor a `1` (regex `/^\d+$/` y `parseInt > 1`).
- Retorna `false` en cualquier otro caso.

**`utils/index.js`** *(archivo barril)*
- Reexporta `isValidInput`.

**`prime/validarNumero.js`**
- Exporta `validarNumero(n)`.
- Retorna `true` si `n` es un entero mayor a `1`, `false` en caso contrario.
- Función pura sin `console.log`.

**`prime/contarDivisores.js`**
- Exporta `contarDivisores(n)`.
- Itera desde `1` hasta `n` y cuenta cuántos valores dividen exactamente a `n` (módulo `=== 0`).
- Retorna el conteo como `number`.
- Función pura sin `console.log`.

**`prime/esPrimo.js`**
- Importa `contarDivisores` desde `./contarDivisores.js`.
- Exporta `esPrimo(n)`.
- Retorna `true` si `contarDivisores(n) === 2`, `false` en caso contrario.
- Función pura sin `console.log`.

**`prime/mostrarResultado.js`**
- Exporta `mostrarResultado(n, primo)`.
- Si `primo` es `true`: imprime `"El número ${n} SÍ es primo."`.
- Si `primo` es `false`: imprime `"El número ${n} NO es primo."`.

**`prime/index.js`** *(archivo barril)*
- Reexporta `validarNumero`, `contarDivisores`, `esPrimo` y `mostrarResultado`.

**`index.js`**
- Importa desde `./prime/index.js` y `./utils/index.js`.
- Función `main` asíncrona con `readline` y `await`.
- Solicita el número al usuario.
- Valida con `isValidInput`; si es inválido, vuelve a pedir.
- Convierte con `parseInt(..., 10)`.
- Verifica con `validarNumero`; si falla, muestra error y termina.
- Evalúa con `esPrimo`.
- Muestra el resultado con `mostrarResultado`.

### Comportamiento esperado en consola

```text
=== Detector de Número Primo ===

Ingrese un número entero mayor a 1: 17

El número 17 SÍ es primo.

---

Ingrese un número entero mayor a 1: 12

El número 12 NO es primo.
```

### Restricciones técnicas

- Prohibido usar `require`.
- `esPrimo` debe importar y usar `contarDivisores` internamente (composición real).
- Solo `mostrarResultado` puede tener `console.log`; las demás funciones de `prime/` son puras.
- El barril `prime/index.js` reexporta todas las funciones sin redefinirlas.
- Buenas prácticas: nombres descriptivos, sin abreviaciones, un concepto por archivo.
