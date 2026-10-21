---
name: chained-pr
description: "Dividir cambios grandes (>400 líneas) en PRs encadenados para proteger el foco de revisión. Disparador: funcionalidades extensas, ramas apiladas."
license: Apache-2.0
metadata:
  author: gentle-ai-copilot
  version: "1.0"
---

# Habilidad: PRs Encadenados (Chained PRs)

## Cuándo Usar

Cargar esta habilidad cuando la magnitud de una funcionalidad exceda el presupuesto de 400 líneas o cuando una migración arquitectónica importante deba entregarse incrementalmente sin romper la rama principal.

## Reglas Obligatorias

1. **División por Límites de Dominio, no por Capas Horizontales**:
   - Evitar dividir por capas técnicas (ej. PR 1: solo tablas/modelos, PR 2: solo servicios, PR 3: solo controladores).
   - Dividir verticalmente por sub-capacidades funcionales completas o primero por contratos/interfaces estables seguidos de su implementación concreta.
2. **Revisable en ≤ 45 Minutos**:
   - Cada PR de la cadena debe ser lo bastante reducido como para que un revisor humano pueda auditarlo con máxima concentración en menos de 45 minutos.
3. **Mapeo Explícito de Dependencias**:
   - Cada PR encadenado debe detallar en su descripción sus ramas dependientes:
     ```
     [PR Base #101] ➔ [PR Actual #102 📍] ➔ [Siguiente PR #103]
     ```
4. **Estrategia de Destino de Ramas**:
   - El PR #1 apunta a `main`.
   - El PR #2 apunta a la rama del PR #1.
   - Cuando el PR #1 se fusione, rebasar/reorientar el PR #2 hacia `main`.
