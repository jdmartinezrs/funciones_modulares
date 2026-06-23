# Sistema de Cálculo Académico

Proyecto modular de Node.js para calcular el promedio de tres notas académicas y determinar si el estudiante aprobó o reprobó, con entrada asíncrona desde consola.

---

## Requisitos Funcionales

- RF01 — El sistema debe solicitar tres notas numéricas al usuario desde la consola.
- RF02 — Debe existir una función `calcularPromedio` que reciba tres notas y retorne el promedio.
- RF03 — El promedio debe calcularse como `(nota1 + nota2 + nota3) / 3`.
- RF04 — Si el promedio es mayor o igual a `3.0`, el sistema debe indicar que el estudiante **aprobó**.
- RF05 — Si el promedio es menor a `3.0`, el sistema debe indicar que el estudiante **reprobó**.
- RF06 — La determinación del estado (aprobó/reprobó) debe usar operadores lógicos y condicionales.
- RF07 — El sistema debe mostrar el promedio con dos decimales y el estado final en consola.

## Requisitos No Funcionales

- RNF01 — El proyecto debe usar módulos ES6 (`import`/`export`) sin `require`.
- RNF02 — La función `calcularPromedio` debe residir en `academic/calcularPromedio.js`.
- RNF03 — La función de evaluación de estado debe residir en `academic/evaluarEstado.js`.
- RNF04 — Las exportaciones deben centralizarse en el barril `academic/index.js`.
- RNF05 — La validación de que cada nota sea un número válido debe estar en `utils/isValidNote.js`.
- RNF06 — El barril `utils/index.js` debe reexportar la validación.
- RNF07 — `index.js` solo orquesta: entrada → validación → cálculo → evaluación → salida.
- RNF08 — El proyecto debe declarar `"type": "module"` en `package.json`.

---

## Prompt de Desarrollo

Genera un proyecto Node.js con módulos ES6 (sin `require`, solo `import`/`export`) que implemente un sistema de cálculo de promedio académico por consola.

### Instrucciones para el prompt

El prompt debe generar exactamente la siguiente estructura limpia de archivos:

```
reto2/
├── package.json
├── index.js
├── utils/
│   ├── index.js
│   └── isValidNote.js
└── academic/
    ├── index.js
    ├── calcularPromedio.js
    └── evaluarEstado.js
```

### Especificaciones por archivo

**`package.json`**
- Nombre: `sistema-calculo-academico`
- `"type": "module"`.
- Script `start`: `node index.js`.
- Sin dependencias externas.

**`utils/isValidNote.js`**
- Exporta `isValidNote(valor)`.
- Retorna `true` si el valor puede convertirse a número flotante válido entre `0.0` y `5.0`.
- Retorna `false` en cualquier otro caso.

**`utils/index.js`** *(archivo barril)*
- Reexporta `isValidNote` desde `./isValidNote.js`.

**`academic/calcularPromedio.js`**
- Exporta `calcularPromedio(nota1, nota2, nota3)`.
- Recibe tres números y retorna el promedio como `number`.

**`academic/evaluarEstado.js`**
- Exporta `evaluarEstado(promedio)`.
- Usa un condicional con operador lógico: si `promedio >= 3.0` retorna `"Aprobó"`, de lo contrario `"Reprobó"`.

**`academic/index.js`** *(archivo barril)*
- Reexporta `calcularPromedio` y `evaluarEstado`.

**`index.js`**
- Importa desde los dos barriles.
- Declara función `main` como `async`.
- Solicita las tres notas con `await` y `readline`.
- Valida cada nota con `isValidNote`; si es inválida, muestra error y vuelve a pedir.
- Convierte las notas a `parseFloat`.
- Calcula el promedio con `calcularPromedio`.
- Evalúa el estado con `evaluarEstado`.
- Muestra promedio (`.toFixed(2)`) y estado.

### Comportamiento esperado en consola

```text
=== Sistema de Cálculo Académico ===

Ingrese la nota 1 (0.0 - 5.0): 3.5
Ingrese la nota 2 (0.0 - 5.0): 2.8
Ingrese la nota 3 (0.0 - 5.0): 4.1

=== Resultado ===
Promedio : 3.47
Estado   : Aprobó
```

### Restricciones técnicas

- Prohibido usar `require`.
- La lógica de negocio no puede estar en `index.js`.
- `evaluarEstado` debe usar `>=` con el literal `3.0` como umbral.
- Los barriles solo reexportan, no definen lógica.
