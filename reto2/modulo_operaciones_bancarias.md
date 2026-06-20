# Módulo de Operaciones Bancarias - Especificaciones

## Descripción del Algoritmo
Diseña un sistema que permita simular operaciones bancarias básicas como depositar dinero, retirar dinero y consultar saldo, con mantenimiento del saldo entre operaciones.

## Funcionalidades Requeridas

### 1. Función de Deposito
- **Nombre sugerido**: `depositar`
- **Parámetros**: Saldo actual, monto a depositar
- **Retorno**: Nuevo saldo actualizado
- **Descripción**: Debe recibir el saldo actual y el monto a depositar, sumar el monto al saldo y retornar el nuevo saldo

### 2. Función de Retiro
- **Nombre sugerido**: `retirar`
- **Parámetros**: Saldo actual, monto a retirar
- **Retorno**: Nuevo saldo actualizado (o mensaje de error si no hay fondos suficientes)
- **Descripción**: Debe verificar si hay saldo suficiente, restar el monto del saldo y retornar el nuevo saldo

### 3. Función de Consulta de Saldo
- **Nombre sugerido**: `consultarSaldo`
- **Parámetros**: Saldo actual
- **Retorno**: Mensaje con el saldo actual
- **Descripción**: Debe mostrar el saldo actual de la cuenta

### 4. Función Principal con Ciclo
- **Nombre sugerido**: `sistemaBancario`
- **Parámetros**: Saldo inicial
- **Retorno**: No retorna valor (muestra mensajes)
- **Descripción**: Debe permitir múltiples operaciones hasta que el usuario decida salir

## Conceptos a Aplicar
- Modularización del código en funciones separadas
- Mantenimiento de estado (saldo) entre operaciones
- Estructuras de ciclo (while/for) para operaciones repetitivas
- Condicionales para validación de fondos
- Parámetros y argumentos
- Interacción continua con el usuario

## Criterios de Aceptación
- El sistema debe permitir depositar dinero correctamente
- El sistema debe permitir retirar dinero validando fondos suficientes
- El sistema debe permitir consultar el saldo en cualquier momento
- El saldo debe mantenerse actualizado entre operaciones
- El sistema debe permitir realizar múltiples operaciones
- El usuario debe poder salir del sistema cuando lo decida
- Cada operación debe estar en una función diferente

## Consideraciones Adicionales
- Valida que los montos ingresados sean valores numéricos positivos
- Maneja casos de retiro con fondos insuficientes
- Muestra mensajes claros para cada operación
- El saldo inicial puede ser 0 o un valor definido
- El código debe ser legible y seguir buenas prácticas
- Usa nombres descriptivos para funciones y variables

## Flujo del Sistema
1. Inicializar saldo (puede ser 0)
2. Mostrar menú de operaciones (Depositar, Retirar, Consultar, Salir)
3. Según la opción seleccionada, ejecutar la función correspondiente
4. Actualizar saldo según la operación realizada
5. Repetir el ciclo hasta que el usuario decida salir