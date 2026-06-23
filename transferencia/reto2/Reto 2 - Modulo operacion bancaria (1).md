Actúa como un desarrollador de software Senior especializado en Node.js y arquitectura modular. Tu tarea es programar una aplicación de consola para evaluar el promedio de un estudiante.

Genera el código completo del proyecto cumpliendo estrictamente con las siguientes directivas, basándote en el contexto proporcionado y sin obviar ningún detalle:

1. Requisitos del Sistema (Contexto Obligatorio)
Requisitos Funcionales:

Captura de datos: El sistema debe solicitar y permitir al usuario ingresar tres calificaciones de forma independiente a través de la consola.
Actúa como un desarrollador de software Senior especializado en Node.js y arquitectura modular. Tu tarea es programar una aplicación de consola para simular un módulo de operaciones bancarias.

Genera el código completo del proyecto cumpliendo estrictamente con las siguientes directivas, basándote en el contexto proporcionado y sin obviar ningún detalle:

1. Requisitos del Sistema (Contexto Obligatorio)
Requisitos Funcionales:

Menú Interactivo y Ciclo: El sistema debe mostrar un menú de opciones (1. Depositar, 2. Retirar, 3. Consultar Saldo, 4. Salir) y utilizar un ciclo (while o do-while) para permitir múltiples operaciones continuas hasta que el usuario elija explícitamente la opción de salir.

Manejo de Estado (Saldo): El sistema debe inicializar un saldo base (ej. 0) y mantenerlo actualizado de forma persistente en memoria entre cada operación que el usuario realice.

Operación Depositar: Debe capturar un monto a ingresar, sumarlo al saldo actual y retornar el saldo actualizado.

Operación Retirar: Debe capturar un monto a retirar, validar que el monto no exceda el saldo disponible (evitar saldos negativos), restarlo y retornar el saldo actualizado o un mensaje de error por fondos insuficientes.

Operación Consultar: Debe mostrar en consola el saldo actual formateado correctamente.

Requisitos No Funcionales:

Entorno y Lenguaje: Desarrollo en JavaScript ejecutado bajo el entorno de servidor Node.js.

Manejo de dependencias: Gestión a través de npm con su respectivo archivo package.json.

Integración de librerías: Uso obligatorio de prompt-sync para la lectura interactiva y síncrona del menú en la consola.

Estándar de importación: Configuración del proyecto bajo ES6 Modules ("type": "module").

Arquitectura Modular: Cada operación bancaria (depositar, retirar, consultar) debe vivir en su propio archivo independiente.

Patrón Barril (Barrel Pattern): Se debe usar un archivo index.js en la carpeta de los módulos para centralizar y re-exportar las funciones hacia el archivo principal.

Calidad de código: Las operaciones deben construirse como funciones puras, recibiendo el saldo actual y el monto como parámetros, y retornando el nuevo saldo sin mutar variables globales directamente desde adentro de la función.

2. Entorno y Arquitectura Modular

Tecnología: Node.js + JavaScript (ES6).

Librería Externa: Utiliza obligatoriamente prompt-sync para pausar la ejecución y capturar la decisión del usuario.

Carpetas y Barriles: Crea una carpeta llamada operaciones. Dentro, crea un archivo para cada acción matemática/bancaria y un index.js que las exporte todas juntas hacia el controlador principal (app.js).

3. Reglas de Negocio y Lógica

Validación de Entradas: Antes de enviar el monto a las funciones de depositar o retirar, el sistema debe convertir el string capturado en un valor numérico (parseFloat) y validar que sea un número positivo válido (!isNaN y > 0).

Flujo de Control: Utiliza un bloque switch dentro del ciclo infinito para evaluar la opción ingresada por el usuario en el menú y ejecutar la función correspondiente. Utiliza break tanto para salir del switch como para romper el ciclo infinito cuando el usuario elija "Salir".

4. Entregables Requeridos

Estructura de directorios sugerida (mostrando claramente la carpeta y el archivo barril).

Contenido exacto del archivo package.json.

Código de los archivos modulares (depositar.js, retirar.js, consultar.js).

Código del archivo barril (index.js dentro de la carpeta del módulo).

Código del archivo principal (app.js o main.js) manejando la variable del saldo, el ciclo while, y las importaciones desde el barril.

Comandos de terminal para instalar la librería y ejecutar la simulación.