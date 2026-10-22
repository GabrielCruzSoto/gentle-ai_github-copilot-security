---
name: work-unit-commits
description: "Planificar commits como unidades de trabajo revisables. Disparador: implementación, división de commits, PRs encadenados, mantener pruebas y docs con el código."
license: Apache-2.0
metadata:
  author: gentle-ai-copilot
  version: "1.0"
---

# Habilidad: Commits como Unidades de Trabajo

## Cuándo Usar

Cargar esta habilidad al decidir cómo estructurar, dividir o empaquetar commits antes de solicitar revisión o crear solicitudes de extracción (Pull Requests).

## Reglas Obligatorias

1. **Límite de 400 Líneas**:
   - El total de líneas modificadas (`adiciones + eliminaciones`) por unidad de trabajo debe mantenerse por debajo de 400 líneas.
   - Cambios de gran tamaño abruman al revisor, diluyen la atención y propician la introducción de errores ocultos.
2. **Co-ubicación de Pruebas y Documentación**:
   - Nunca separar la implementación de sus pruebas ni de su documentación en commits distintos.
   - Cada commit debe ser auto-verificable: el código, las pruebas que comprueban su comportamiento y las explicaciones de sus contratos deben viajar juntos.
3. **Cero Estados Intermedios Rotos**:
   - Cada commit en el historial de Git debe compilar, superar las pruebas y dejar el proyecto en un estado funcional y desplegable.
4. **Conventional Commits**:
   - Emplear convenciones estándar (`feat`, `fix`, `refactor`, `test`, `docs`, `chore`).
   - Utilizar resúmenes directos en modo imperativo.
5. **Cero Atribución de IA**:
   - Nunca inyectar banners generados por IA, cláusulas "Co-Authored-By" o firmas de herramientas en los commits.
6. **Prohibición Absoluta de Commits en Ramas Base (`prod`, `master`, `main`, `develop`)**:
   - Jamás realizar commits directos sobre ramas protegidas (`prod`, `production`, `master`, `main`, `develop`).
   - Todo commit debe efectuarse en una rama de soporte temporal (`feature/*`, `hotfix/*`, `release/*`) y fusionarse únicamente a través de un Pull Request (PR) aprobado.
