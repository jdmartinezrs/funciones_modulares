# Sistema Calculadora de Compra

Proyecto modular de Node.js para calcular el valor total de una compra aplicando subtotal e IVA del 19%, con entrada asíncrona desde consola y separación estricta de responsabilidades.

---

## Requisitos Funcionales

- RF01 — El sistema debe solicitar la cantidad de unidades y el precio unitario desde la consola.
- RF02 — Debe existir una función `calcularSubtotal(cantidad, precio)` que retorne `cantidad × precio`.
- RF03 — Debe existir una función `calcularIVA(subtotal)` que retorne el `19%` del subtotal.
- RF04 — Debe existir una función `calcularTotal(subtotal, iva)` que retorne la suma de ambos.
- RF05 — El sistema debe mostrar en consola el subtotal, el IVA y el total a pagar con formato de moneda.
- RF06 — Los resultados de una función deben usarse como entrada de la siguiente (composición de funciones).

## Requisitos No Funcionales

- RNF01 — El proyecto debe usar módulos ES6 (`import`/`export`) sin `require`.
- RNF02 — Cada función de cálculo debe residir en su propio archivo dentro de `purchase/`.
- RNF03 — Las exportaciones deben centralizarse en el barril `purchase/index.js`.
- RNF04 — La validación de valores numéricos positivos debe estar en `utils/isPositiveNumber.js`.
- RNF05 — El barril `utils/index.js` debe reexportar la validación.
- RNF06 — `index.js` solo orquesta: entrada → validación → cálculos encadenados → salida.
- RNF07 — Las funciones de cálculo deben ser funciones puras sin efectos secundarios.
- RNF08 — `"type": "module"` en `package.json`.

---

## Prompt de Desarrollo

Genera un proyecto Node.js con módulos ES6 (sin `require`, solo `import`/`export`) que implemente una calculadora de compra modular con subtotal, IVA y total.

### Instrucciones para el prompt

El prompt debe generar exactamente la siguiente estructura limpia de archivos:

```
reto4/
├── package.json
├── index.js
├── utils/
│   ├── index.js
│   └── isPositiveNumber.js
└── purchase/
    ├── index.js
    ├── calcularSubtotal.js
    ├── calcularIVA.js
    └── calcularTotal.js
```

### Especificaciones por archivo

**`package.json`**
- Nombre: `sistema-calculadora-compra`
- `"type": "module"`.
- Script `start`: `node index.js`.

**`utils/isPositiveNumber.js`**
- Exporta `isPositiveNumber(valor)`.
- Retorna `true` si el valor puede convertirse a `parseFloat` y el resultado es `> 0`.
- Retorna `false` en cualquier otro caso.

**`utils/index.js`** *(archivo barril)*
- Reexporta `isPositiveNumber`.

**`purchase/calcularSubtotal.js`**
- Exporta `calcularSubtotal(cantidad, precio)`.
- Retorna `cantidad * precio`.
- Función pura, sin `console.log`.

**`purchase/calcularIVA.js`**
- Exporta `calcularIVA(subtotal)`.
- Retorna `subtotal * 0.19`.
- Función pura, sin `console.log`.

**`purchase/calcularTotal.js`**
- Exporta `calcularTotal(subtotal, iva)`.
- Retorna `subtotal + iva`.
- Función pura, sin `console.log`.

**`purchase/index.js`** *(archivo barril)*
- Reexporta `calcularSubtotal`, `calcularIVA` y `calcularTotal`.

**`index.js`**
- Importa las tres funciones desde `./purchase/index.js` e `isPositiveNumber` desde `./utils/index.js`.
- Función `main` asíncrona con `readline` y `await`.
- Solicita cantidad y precio; valida cada uno con `isPositiveNumber`.
- Encadena los cálculos: `subtotal → iva → total`.
- Muestra los tres valores con `toLocaleString('es-CO', { style: 'currency', currency: 'COP' })`.

### Comportamiento esperado en consola

```text
=== Calculadora de Compra ===

Ingrese la cantidad de unidades: 3
Ingrese el precio unitario: 25000

=== Resumen de Compra ===
Subtotal : $75.000,00
IVA (19%): $14.250,00
Total    : $89.250,00
```

### Restricciones técnicas

- Prohibido usar `require`.
- Las funciones de `purchase/` deben ser puras (sin `console.log` ni efectos secundarios).
- El encadenamiento `subtotal → iva → total` debe hacerse en `index.js`.
- El barril reexporta, no redefine.
