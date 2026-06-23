# Sistema de Facturación

Proyecto modular de Node.js para procesar una lista de productos con nombre, precio y cantidad, calculando subtotales por producto, total sin IVA, IVA del 19% y valor total a pagar, con entrada asíncrona desde consola y la función final implementada como función flecha.

---

## Requisitos Funcionales

- RF01 — El sistema debe solicitar al usuario cuántos productos desea ingresar.
- RF02 — Por cada producto debe solicitar: nombre, precio unitario y cantidad.
- RF03 — Debe existir una función `calcularSubtotalProducto(precio, cantidad)` que retorne `precio × cantidad` para cada producto.
- RF04 — Debe existir una función `calcularTotalSinIVA(productos)` que reciba el arreglo de productos con sus subtotales y retorne la suma de todos los subtotales.
- RF05 — Debe existir una función `calcularIVATotal(totalSinIVA)` que retorne el `19%` del total sin IVA.
- RF06 — La función `calcularTotalAPagar` debe estar implementada como **función flecha** y recibir `totalSinIVA` e `ivaTotal` para retornar su suma.
- RF07 — El sistema debe mostrar una tabla en consola con cada producto, su subtotal, y al final el resumen: total sin IVA, IVA y total a pagar.
- RF08 — Los valores monetarios deben mostrarse con formato de dos decimales.

## Requisitos No Funcionales

- RNF01 — El proyecto debe usar módulos ES6 (`import`/`export`) sin `require`.
- RNF02 — Cada función de cálculo debe residir en su propio archivo dentro de `billing/`.
- RNF03 — Las exportaciones deben centralizarse en el barril `billing/index.js`.
- RNF04 — La validación de entradas numéricas debe estar en `utils/isPositiveNumber.js` y la de texto no vacío en `utils/isNonEmptyString.js`; ambas reexportadas desde `utils/index.js`.
- RNF05 — `index.js` solo orquesta: entrada → validación → construcción del arreglo → cálculos → presentación.
- RNF06 — Las funciones de cálculo deben ser funciones puras sin efectos secundarios (sin `console.log`).
- RNF07 — `calcularTotalAPagar` debe ser obligatoriamente una función flecha (`const ... = (...) => ...`).
- RNF08 — `"type": "module"` en `package.json`.
- RNF09 — El código debe seguir convenciones de nombrado en camelCase y un concepto por archivo.

---

## Prompt de Desarrollo

Genera un proyecto Node.js con módulos ES6 (sin `require`, solo `import`/`export`) que implemente un sistema de facturación modular con lista de productos ingresada desde consola.

### Instrucciones para el prompt

El prompt debe generar exactamente la siguiente estructura limpia de archivos:

```
reto3/
├── package.json
├── index.js
├── utils/
│   ├── index.js
│   ├── isPositiveNumber.js
│   └── isNonEmptyString.js
└── billing/
    ├── index.js
    ├── calcularSubtotalProducto.js
    ├── calcularTotalSinIVA.js
    ├── calcularIVATotal.js
    └── calcularTotalAPagar.js
```

### Especificaciones por archivo

**`package.json`**
- Nombre: `sistema-facturacion`
- Versión: `1.0.0`
- `"type": "module"` para habilitar ES6.
- Script `start`: `node index.js`.
- Sin dependencias externas.

**`utils/isPositiveNumber.js`**
- Exporta `isPositiveNumber(valor)`.
- Retorna `true` si `parseFloat(valor)` produce un número válido y `> 0`.
- Retorna `false` en cualquier otro caso.

**`utils/isNonEmptyString.js`**
- Exporta `isNonEmptyString(valor)`.
- Retorna `true` si `valor` es una cadena con al menos un carácter no espaciado (`trim().length > 0`).
- Retorna `false` en cualquier otro caso.

**`utils/index.js`** *(archivo barril)*
- Reexporta `isPositiveNumber` desde `./isPositiveNumber.js`.
- Reexporta `isNonEmptyString` desde `./isNonEmptyString.js`.

**`billing/calcularSubtotalProducto.js`**
- Exporta `calcularSubtotalProducto(precio, cantidad)`.
- Retorna `precio * cantidad`.
- Función pura, sin `console.log`.

**`billing/calcularTotalSinIVA.js`**
- Exporta `calcularTotalSinIVA(productos)`.
- Recibe un arreglo de objetos `{ nombre, precio, cantidad, subtotal }`.
- Retorna la suma de todos los valores `subtotal` usando `reduce`.
- Función pura, sin `console.log`.

**`billing/calcularIVATotal.js`**
- Exporta `calcularIVATotal(totalSinIVA)`.
- Retorna `totalSinIVA * 0.19`.
- Función pura, sin `console.log`.

**`billing/calcularTotalAPagar.js`**
- Exporta `calcularTotalAPagar` como **función flecha**:
  `export const calcularTotalAPagar = (totalSinIVA, ivaTotal) => totalSinIVA + ivaTotal;`
- Cuerpo de una sola expresión, sin llaves ni `return` explícito.
- Función pura, sin `console.log`.

**`billing/index.js`** *(archivo barril)*
- Reexporta `calcularSubtotalProducto`, `calcularTotalSinIVA`, `calcularIVATotal` y `calcularTotalAPagar`.

**`index.js`**
- Importa las cuatro funciones desde `./billing/index.js`.
- Importa `isPositiveNumber` e `isNonEmptyString` desde `./utils/index.js`.
- Declara función `pregunta(rl, texto)` auxiliar que envuelve `rl.question` en una `Promise`.
- Declara función `main` marcada como `async`.
- Solicita la cantidad de productos a ingresar; valida que sea un entero positivo.
- Itera `n` veces solicitando nombre, precio y cantidad para cada producto:
  - Valida nombre con `isNonEmptyString`; si es inválido, vuelve a pedir.
  - Valida precio con `isPositiveNumber`; si es inválido, vuelve a pedir.
  - Valida cantidad con `isPositiveNumber`; si es inválido, vuelve a pedir.
  - Calcula el subtotal con `calcularSubtotalProducto`.
  - Agrega `{ nombre, precio, cantidad, subtotal }` al arreglo `productos`.
- Una vez completado el arreglo, encadena los cálculos:
  1. `totalSinIVA` ← `calcularTotalSinIVA(productos)`
  2. `ivaTotal` ← `calcularIVATotal(totalSinIVA)`
  3. `totalAPagar` ← `calcularTotalAPagar(totalSinIVA, ivaTotal)`
- Imprime la tabla de productos y el resumen final.
- Cierra la interfaz `readline` al finalizar.
- Llama a `main()` al final del archivo.

### Comportamiento esperado en consola

```text
=== Sistema de Facturación ===

¿Cuántos productos desea ingresar? 3

--- Producto 1 ---
Nombre   : Cuaderno
Precio   : 4500
Cantidad : 2

--- Producto 2 ---
Nombre   : Lápiz
Precio   : 800
Cantidad : 5

--- Producto 3 ---
Nombre   : Borrador
Precio   : 1200
Cantidad : 3

=== Factura ===
┌─────────────────────────────────────────────────┐
│ Producto        Precio    Cantidad    Subtotal   │
├─────────────────────────────────────────────────┤
│ Cuaderno        $4500.00     2        $9000.00   │
│ Lápiz            $800.00     5        $4000.00   │
│ Borrador        $1200.00     3        $3600.00   │
└─────────────────────────────────────────────────┘

Total sin IVA : $16600.00
IVA (19%)     :  $3154.00
Total a pagar : $19754.00
```

### Restricciones técnicas

- Prohibido usar `require`.
- `calcularTotalAPagar` debe ser función flecha de expresión única (sin `return` explícito).
- Las funciones de `billing/` deben ser puras: ninguna puede tener `console.log`.
- El arreglo `productos` se construye en `index.js` y se pasa a las funciones; no se define dentro de los módulos.
- Los barriles (`billing/index.js`, `utils/index.js`) solo reexportan, no definen lógica.
- La entrada de texto para el nombre debe aceptar espacios y caracteres especiales; solo se rechaza cadena vacía.
