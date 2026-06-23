# Prompt — Reto 4: Análisis de Números

## Rol

Actúa como un desarrollador JavaScript experto con enfoque pedagógico.
Resuelve el siguiente reto académico siguiendo estrictamente todas las restricciones indicadas.

---

## Enunciado

Crea un programa en JavaScript que reciba un número entero y determine:

- Si es **par o impar**.
- Si es **positivo, negativo o cero**.
- Si es **primo**.

---

## Restricciones de implementación

### Estructura de funciones

| Función                   | Responsabilidad                                      | Retorno esperado                                        |
|---------------------------|------------------------------------------------------|---------------------------------------------------------|
| `esParOImpar(n)`          | Determinar la paridad del número                     | `"Es par"` / `"Es impar"`                              |
| `esPositivoONegativo(n)`  | Determinar el signo del número                       | `"Es positivo"` / `"Es negativo"` / `"Es cero"`        |
| `esPrimo(n)`              | Determinar si el número es primo                     | `"Es primo"` / `"No es primo"`                         |
| `analizarNumero(n)`       | Función principal: invocar las tres anteriores       | String con los tres resultados compilados               |

### Reglas obligatorias

1. Cada validación debe estar en su **propia función independiente**.
2. Las funciones de validación deben **retornar strings descriptivos**, no booleanos.
3. La función principal `analizarNumero(n)` debe **llamar a las tres funciones** y retornar un resumen completo usando template literals.
4. Usar **estructuras condicionales** (`if`, operador ternario) según corresponda.
5. El algoritmo de primalidad debe iterar solo hasta `√n` para optimizar.
6. Considerar los casos especiales: `0`, `1` y números negativos.

### Validación de entrada

Implementar una función `validarEntero(raw)` que rechace cualquier entrada inválida **antes** de llamar a `analizarNumero`. Debe cubrir:

| Tipo de entrada       | Ejemplo     | ¿Aceptado? |
|-----------------------|-------------|------------|
| Entero positivo       | `17`        | ✅ sí      |
| Entero negativo       | `-4`        | ✅ sí      |
| Cero                  | `0`         | ✅ sí      |
| Solo letras           | `abc`       | ❌ no      |
| Mezcla número + letra | `12abc`     | ❌ no      |
| Decimal               | `3.14`      | ❌ no      |
| Caracteres especiales | `@#!`       | ❌ no      |
| Espacios internos     | `1 2`       | ❌ no      |
| Campo vacío           | `""`        | ❌ no      |

Usar la expresión regular `/^-?\d+$/` para validar que la entrada sea estrictamente un entero.

---

## Casos especiales a considerar

- **`0`** → par, cero (ni positivo ni negativo), no primo.
- **`1`** → impar, positivo, **no primo** (por definición matemática estándar).
- **Negativos** → nunca primos (los primos se definen en enteros positivos mayores que 1).
- **`2`** → par, positivo, primo (único primo par).

---

## Ejemplo de salida esperada

```js
analizarNumero(17);
// → "Número 17: Es impar. Es positivo. Es primo."

analizarNumero(0);
// → "Número 0: Es par. Es cero. No es primo."

analizarNumero(-5);
// → "Número -5: Es impar. Es negativo. No es primo."
```

---

## Conceptos que debe aplicar la solución

- Modularización en funciones con responsabilidad única.
- Retorno de valores entre funciones.
- Estructuras condicionales múltiples.
- Algoritmo de primalidad optimizado (`√n`).
- Operadores aritméticos (`%`) y de comparación.
- Validación de entrada con expresión regular.
- Template literals para el mensaje final.

---

## Entregables esperados

- [ ] Código JS con las 5 funciones (`validarEntero`, `esParOImpar`, `esPositivoONegativo`, `esPrimo`, `analizarNumero`).
- [ ] `README.md` con descripción, tabla de funciones, código fuente, casos de prueba y casos especiales.
- [ ] Interfaz visual interactiva que muestre los resultados de las tres validaciones por separado, indique el nombre de la función invocada, muestre el mensaje completo de `analizarNumero`, rechace entradas inválidas con mensaje de error descriptivo e incluya historial de análisis.

---

*Reto académico — SENA, Tecnología en Análisis y Desarrollo de Software.*