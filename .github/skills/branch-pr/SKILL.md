---
name: branch-pr
description: "Estrategias de ramificación GitFlow, preparación de PRs, trazabilidad de issues y filtros de revisión. Disparador: crear ramas o PRs."
license: Apache-2.0
metadata:
  author: gentle-ai-copilot
  version: "1.1"
---

# Habilidad: Ramas y Solicitudes de Extracción (GitFlow Obligatorio)

## Cuándo Usar

Cargar esta habilidad al:
- Crear ramas de trabajo o nombrar ramas en Git.
- Definir la rama base y la rama destino de una integración.
- Redactar descripciones de PRs en GitHub, GitLab o Bitbucket empresarial.
- Preparar lanzamientos (`release`) o parches urgentes (`hotfix`).

## Arquitectura de Ramas (GitFlow)

```
main       ●───────────────────────────────● (v1.0.0)─────────● (v1.0.1)───────● (v1.1.0)
            \                             /                   /                 /
hotfix       \                           /       ●───────────● (hotfix/1.0.1)  /
              \                         /       /             \               /
develop        ●───────────●───────────●───────●───────────────●─────────────●
                \         /             \                                   /
feature          ●───────● (feat/A)      \                                 /
                                          ●───────────────────────────────● (release/1.1.0)
```

## Reglas Obligatorias de Ramificación

1. **Ramas Principales Permanentes**:
   - `main`: Código en producción. Cero commits directos. Solo recibe merges de `release/*` y `hotfix/*`. Siempre lleva tags anotados (`vX.Y.Z`).
   - `develop`: Rama de integración activa. Cero commits directos. Base de partida para todas las ramas `feature/*` y `release/*`.

2. **Ramas Temporales y Convenciones de Nombres**:
   - **Funcionalidades (`feature/`)**:
     - *Origen*: `develop`
     - *Destino (PR)*: `develop`
     - *Nomenclatura*: `feature/<id-tarea>-<descripcion-corta>`
   - **Estabilización de Lanzamientos (`release/`)**:
     - *Origen*: `develop`
     - *Destino (PR)*: `main` Y de vuelta a `develop`
     - *Nomenclatura*: `release/v<X.Y.Z>`
     - *Acción al fusionar*: Crear tag `v<X.Y.Z>` en `main`.
   - **Correcciones Urgentes en Producción (`hotfix/`)**:
     - *Origen*: `main`
     - *Destino (PR)*: `main` Y de vuelta a `develop`
     - *Nomenclatura*: `hotfix/<id-incidente>-<descripcion-corta>`
     - *Acción al fusionar*: Crear tag `v<X.Y.Z+1>` en `main`.

3. **Trazabilidad de Requisitos y Auditoría Bancaria**:
   - Toda rama `feature` o `hotfix` debe incluir en su nombre y en el PR el identificador de la tarea ODD o ticket corporativo.
   - Prohibido fusionar código sin un ticket de origen y recibo de pruebas.

4. **Estructura de la Descripción del PR**:
   - **Tipo y Rama Base**: Indicar claramente el tipo GitFlow y rama base (`develop` o `main`).
   - **Resumen**: Qué necesidad de negocio o técnica cubre.
   - **Recibos de Verificación**: Evidencia de pruebas ejecutadas y ledger de revisión 4R.
   - **Seguridad**: Confirmación de cumplimiento bancario (cero fuga de PII/PCI, fallas seguras).

5. **Presupuesto de Tamaño**:
   - Mantener el diff del PR dentro de ~400 líneas modificadas. Si excede, dividir usando la habilidad `chained-pr` dentro de ramas feature.
