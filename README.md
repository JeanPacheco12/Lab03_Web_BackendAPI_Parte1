# Lab 9 - Backend API (Parte 1: Paginación y Metadatos)

Este lab es la primera parte del desarrollo de una API REST para la gestión de propiedades inmobiliarias (**EstateHub API**). El objetivo principal de esta entrega fue la implementación de un sistema de paginación eficiente y la estructuración de respuestas con metadatos.

## Funcionalidades Implementadas

*   **Paginación con Skip/Take**: Se integró lógica en el repositorio para que Prisma realice consultas segmentadas, evitando la carga masiva de datos.
*   **Validación de Parámetros**: El controlador valida que `page` y `limit` sean números positivos, asignando valores por defecto (`page=1`, `limit=10`) si no se proveen.
*   **Estructura de Respuesta Estandarizada**: Las respuestas incluyen un objeto `meta` con:
    *   `total`: Conteo real de registros en la base de datos.
    *   `page`: Página actual consultada.
    *   `limit`: Cantidad de registros por página.
    *   `pages`: Total de páginas calculadas dinámicamente.

## Cambios Técnicos e Importantes de Archivos

1.  **Controller (`propertyController.ts`)**: Se añadió la lógica de extracción y validación de query params y el cálculo de `totalPages`.
2.  **Repository (`propertyRepository.ts`)**: Se actualizó la función `findAll` para ejecutar `prisma.property.findMany` y `prisma.property.count` de forma paralela usando `Promise.all`.
3.  **Routes (`propertyRoutes.ts`)**: Se actualizó la documentación de los endpoints para reflejar el soporte de paginación.

## Tecnologías Usadas
*   **Node.js & Express** (Framework backend)
*   **Prisma ORM** (Gestión de base de datos)
*   **SQLite** (Persistencia de datos)
*   **TypeScript** (Tipado estático)

## Enlace de la explicación de la parte 1 de este lab: []
