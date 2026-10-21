---
name: branch-pr
description: "Estrategias de ramificación, preparación de PRs, trazabilidad de issues y filtros de revisión. Disparador: crear ramas o PRs."
license: Apache-2.0
metadata:
  author: gentle-ai-copilot
  version: "1.0"
---

# Habilidad: Ramas y Solicitudes de Extracción (PR)

## Cuándo Usar

Cargar esta habilidad al:
- Nombrar o crear ramas de Git.
- Redactar descripciones de PRs en GitHub, GitLab o Bitbucket empresarial.
- Preparar cambios para auditoría y revisión en equipo.

## Reglas y Estándares

1. **Nomenclatura de Ramas**:
   - `feat/<id-issue>-<descripcion-corta>`
   - `fix/<id-issue>-<descripcion-corta>`
   - `refactor/<id-issue>-<descripcion-corta>`
2. **Vinculación y Trazabilidad de Requisitos**:
   - Toda rama y PR debe vincularse directamente a una tarea o ticket de issue aprobado.
   - La normativa bancaria exige trazabilidad de procedencia para cualquier código fusionado.
3. **Estructura de la Descripción del PR**:
   - **Resumen**: Declaración directa del problema resuelto.
   - **Contexto y Arquitectura**: Explicación de alto nivel de las modificaciones técnicas.
   - **Recibos de Verificación**: Comandos de prueba o resultados de la suite que acreditan el funcionamiento.
   - **Seguridad y Cumplimiento**: Confirmación de no exposición de PII, validación de entradas y diseño seguro por defecto.
4. **Presupuesto de Tamaño**:
   - Mantener el diff del PR bajo 400 líneas salvo excepción expresa debidamente justificada.
