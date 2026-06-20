# Análisis de Números - Especificaciones

## Descripción del Algoritmo
Crea un programa que reciba un número entero y realice múltiples validaciones: determinar si es par o impar, positivo o negativo, y si es primo.

## Funcionalidades Requeridas

### 1. Función de Validación Par/Impar
- **Nombre sugerido**: `esParOImpar`
- **Parámetros**: Número entero
- **Retorno**: Mensaje "Es par" o "Es impar"
- **Descripción**: Debe determinar si el número es divisible por 2 y retornar el resultado correspondiente

### 2. Función de Validación Positivo/Negativo
- **Nombre sugerido**: `esPositivoONegativo`
- **Parámetros**: Número entero
- **Retorno**: Mensaje "Es positivo", "Es negativo" o "Es cero"
- **Descripción**: Debe determinar si el número es mayor, menor o igual a cero y retornar el resultado

### 3. Función de Validación de Número Primo
- **Nombre sugerido**: `esPrimo`
- **Parámetros**: Número entero
- **Retorno**: Mensaje "Es primo" o "No es primo"
- **Descripción**: Debe determinar si el número solo es divisible por 1 y por sí mismo (excepto el 1 que no se considera primo)

### 4. Función Principal
- **Nombre sugerido**: `analizarNumero`
- **Parámetros**: Número entero a analizar
- **Retorno**: Mensaje con todos los resultados del análisis
- **Descripción**: Debe llamar a las funciones de validación y mostrar un resumen completo con todos los resultados

## Conceptos a Aplicar
- Modularización del código en funciones separadas
- Retorno de valores entre funciones
- Estructuras condicionales múltiples
- Algoritmos matemáticos (validación de números primos)
- Operadores aritméticos y de comparación
- Parámetros y argumentos
- Lógica de programación matemática

## Criterios de Aceptación
- El programa debe recibir un número entero
- Debe determinar correctamente si el número es par o impar
- Debe determinar correctamente si el número es positivo, negativo o cero
- Debe determinar correctamente si el número es primo o no
- Cada validación debe estar en una función diferente
- La función principal debe mostrar todos los resultados de forma organizada
- Las validaciones matemáticas deben ser precisas

## Consideraciones Adicionales
- Valida que el input sea un número entero
- Considera el caso especial del número 0 (par, no positivo ni negativo, no primo)
- Considera el caso especial del número 1 (no primo por definición matemática)
- Considera números negativos para la validación de primos (generalmente no se consideran primos)
- El código debe ser legible y seguir buenas prácticas
- Usa nombres descriptivos para funciones y variables

## Algoritmo para Números Primos
Un número es primo si:
- Es mayor que 1
- Solo es divisible por 1 y por sí mismo
- Para validarlo: intentar dividirlo por todos los números desde 2 hasta la raíz cuadrada del número
- Si alguna división es exacta, no es primo

## Flujo del Sistema
1. Recibir el número entero a analizar
2. Validar si es par o impar
3. Validar si es positivo, negativo o cero
4. Validar si es primo o no
5. La función principal compila todos los resultados
6. Mostrar un resumen completo con todas las validaciones