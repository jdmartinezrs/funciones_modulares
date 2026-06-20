# Sistema de Facturación - Especificaciones

## Descripción del Algoritmo
Crea un programa que reciba una lista de productos (nombre, precio, cantidad) y calcule los diferentes componentes de una factura, incluyendo subtotal, IVA y total a pagar.

## Funcionalidades Requeridas

### 1. Función de Cálculo de Subtotal por Producto
- **Nombre sugerido**: `calcularSubtotalProducto`
- **Parámetros**: Precio del producto, cantidad
- **Retorno**: Subtotal del producto (precio × cantidad)
- **Descripción**: Debe calcular el subtotal para un producto específico multiplicando el precio por la cantidad

### 2. Función de Cálculo de Total sin IVA
- **Nombre sugerido**: `calcularTotalSinIVA`
- **Parámetros**: Lista/array de subtotales de productos
- **Retorno**: Suma total de todos los subtotales
- **Descripción**: Debe sumar los subtotales de todos los productos para obtener el total sin IVA

### 3. Función de Cálculo de IVA
- **Nombre sugerido**: `calcularIVA`
- **Parámetros**: Total sin IVA, porcentaje de IVA (19%)
- **Retorno**: Valor del IVA total
- **Descripción**: Debe calcular el IVA aplicando el porcentaje (19%) al total sin IVA

### 4. Función de Cálculo de Total a Pagar (DESAFÍO: Función Flecha)
- **Nombre sugerido**: `calcularTotalPagar` (implementar como función flecha)
- **Parámetros**: Total sin IVA, IVA total
- **Retorno**: Valor total a pagar (total sin IVA + IVA)
- **Descripción**: Debe sumar el total sin IVA y el IVA para obtener el valor total a pagar

## Conceptos a Aplicar
- Modularización del código en funciones separadas
- Retorno de valores entre funciones
- Manejo de arrays/listas de productos
- Cálculos matemáticos para facturación
- **Desafío adicional**: Implementación de funciones flecha
- Parámetros y argumentos
- Estructuras de datos para productos

## Criterios de Aceptación
- El programa debe recibir una lista de productos con nombre, precio y cantidad
- Debe calcular correctamente el subtotal por producto
- Debe calcular el total sin IVA sumando todos los subtotales
- Debe calcular el IVA aplicando el 19% al total sin IVA
- Debe calcular el valor total a pagar
- La función final debe implementarse como función flecha
- Cada cálculo debe estar en una función diferente
- Los resultados deben ser precisos y correctos

## Consideraciones Adicionales
- Valida que los precios y cantidades sean valores numéricos positivos
- Maneja correctamente el cálculo del porcentaje de IVA (19%)
- Considera el redondeo de valores monetarios si es necesario
- La función flecha debe seguir la sintaxis correcta del lenguaje
- El código debe ser legible y seguir buenas prácticas
- Usa nombres descriptivos para funciones y variables

## Estructura de Datos Sugerida
Cada producto puede representarse como:
- Objeto: `{ nombre: string, precio: number, cantidad: number }`
- Array/Lista de productos: `[ producto1, producto2, ... ]`

## Flujo del Sistema
1. Recibir o definir la lista de productos
2. Calcular el subtotal de cada producto
3. Sumar todos los subtotales para obtener el total sin IVA
4. Calcular el IVA (19% del total sin IVA)
5. Calcular el total a pagar (total sin IVA + IVA)
6. Mostrar los resultados de forma clara y organizada