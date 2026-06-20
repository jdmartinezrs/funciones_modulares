# Sistema de Cálculo Académico - Especificaciones

## Descripción del Algoritmo
Crea un programa modularizado que permita registrar el nombre y tres notas de un estudiante y determinar si aprueba o reprueba.

## Funcionalidades Requeridas

### 1. Función de Cálculo de Promedio
- **Nombre sugerido**: `calcularPromedio`
- **Parámetros**: Tres notas (numéricas)
- **Retorno**: Valor promedio de las tres notas
- **Descripción**: Debe recibir las tres notas del estudiante y retornar el promedio calculado

### 2. Función de Determinación de Estado
- **Nombre sugerido**: `determinarEstado`
- **Parámetros**: Promedio calculado
- **Retorno**: Mensaje de "Aprueba" o "Reprueba"
- **Descripción**: Debe evaluar si el promedio cumple con el criterio de aprobación establecido

### 3. Función Principal
- **Nombre sugerido**: `mostrarResultado`
- **Parámetros**: Nombre del estudiante, promedio, estado
- **Retorno**: Mensaje final con nombre y resultado
- **Descripción**: Debe mostrar un mensaje completo que incluya el nombre del estudiante y su resultado académico

## Conceptos a Aplicar
- Modularización del código en funciones separadas
- Retorno de valores entre funciones
- Estructuras condicionales para la lógica de aprobación
- Parámetros y argumentos
- Interacción con el usuario para entrada de datos

## Criterios de Aceptación
- El programa debe registrar el nombre del estudiante
- El programa debe solicitar y procesar tres notas
- El cálculo del promedio debe ser correcto
- La determinación de aprobación/reprobación debe funcionar correctamente
- El mensaje final debe mostrar claramente el nombre y resultado del estudiante
- Cada funcionalidad debe estar en una función diferente
- Las funciones deben comunicarse mediante retorno de valores

## Consideraciones Adicionales
- Define el criterio de aprobación (ej. promedio >= 3.0 o >= 60%)
- Valida que las notas ingresadas sean valores numéricos válidos
- El código debe ser legible y seguir buenas prácticas de programación
- Usa nombres descriptivos para funciones y variables