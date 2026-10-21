# Guía de Flujo de Trabajo: GitFlow para Copilot y Banca

## 1. ¿Por qué GitFlow en Entornos Bancarios?

En la industria bancaria y financiera, el software en producción requiere **máxima estabilidad, trazabilidad y control de versiones auditables**.

GitFlow establece una clara separación de responsabilidades entre el trabajo en desarrollo activo, la estabilización de versiones y el código productivo validado:

- **Aislamiento**: Las funcionalidades en desarrollo nunca contaminan el código de producción.
- **Trazabilidad regulatoria**: Cada release y cada hotfix lleva un tag semántico inmutable (`vX.Y.Z`).
- **Control de accesos y auditoría**: Las ramas `main` y `develop` están protegidas; todos los cambios ingresan mediante Pull Requests revisados con evidencias 4R.

---

## 2. Mapa de Ramas en GitFlow

```
main        ──────────────────────────────● (v1.0.0)─────────● (v1.0.1)───────● (v1.1.0)
             \                           /                   /                 /
hotfix        \                         /       ●───────────● (hotfix/1.0.1)  /
               \                       /       /             \               /
develop         ●──────────●──────────●───────●───────────────●─────────────●
                 \        /            \                                   /
feature           ●──────● (feat/A)     \                                 /
                                         ●───────────────────────────────● (release/1.1.0)
```

### Ramas Principales (Permanentes)

| Rama | Propósito | Reglas |
|---|---|---|
| `main` | Código en producción oficial | Cero commits directos. Solo recibe fusiones de `release/*` y `hotfix/*`. Cada merge genera un tag (`vX.Y.Z`). |
| `develop` | Integración continua de features | Cero commits directos. Base de partida para `feature/*` y `release/*`. Recibe fusiones de `feature/*`, `release/*` y `hotfix/*`. |

---

## 3. Ramas de Soporte (Temporales)

### A. Ramas de Funcionalidad (`feature/*`)
- **Origen**: `develop`
- **Destino del PR**: `develop`
- **Nomenclatura**: `feature/<id-tarea>-<descripcion-corta>` (ej. `feature/ODD-101-transferencias-inmediatas`)
- **Flujo**:
  1. Crear la rama desde `develop`: `git checkout -b feature/ODD-101-transferencias develop`
  2. Redactar la especificación en `odd/tasks/ODD-101-transferencias.md`.
  3. Implementar con TDD estricto y commits bajo 400 líneas.
  4. Ejecutar la revisión 4R (`/review-4r`) y refutación si hay bloqueadores.
  5. Abrir Pull Request hacia `develop`.

### B. Ramas de Estabilización de Lanzamiento (`release/*`)
- **Origen**: `develop`
- **Destino del PR**: `main` **Y** `develop`
- **Nomenclatura**: `release/v<X.Y.Z>` (ej. `release/v1.2.0`)
- **Flujo**:
  1. Crear cuando `develop` contiene todas las features planificadas para la versión.
  2. En esta rama solo se permiten correcciones de errores menores, ajustes de documentación y auditoría final de seguridad bancaria (`/banking-security`).
  3. Al aprobarse:
     - Fusión a `main` con tag `v1.2.0`.
     - Fusión de vuelta a `develop` para sincronizar cualquier corrección hecha en la rama de release.
  4. Se elimina la rama de release.

### C. Ramas de Parche Urgente en Producción (`hotfix/*`)
- **Origen**: `main`
- **Destino del PR**: `main` **Y** `develop`
- **Nomenclatura**: `hotfix/<id-incidente>-<descripcion-corta>` (ej. `hotfix/INC-901-corregir-timeout-pasarela`)
- **Flujo**:
  1. Crear directamente desde el tag afectado en `main`: `git checkout -b hotfix/INC-901 main`
  2. Aplicar la solución mediante TDD (reproducción con prueba fallida previa).
  3. Ejecutar revisión 4R exprés enfocada en Riesgo (R1) y Resiliencia (R4).
  4. Al aprobarse:
     - Fusión a `main` con nuevo tag de parche (ej. `v1.2.1`).
     - Fusión de vuelta a `develop` para evitar regresiones futuras en la siguiente versión.
  5. Se elimina la rama de hotfix.

---

## 4. Integración con ODD y GitHub Copilot

1. **Antes de codificar**: El prompt `/orchestrator` y `/odd-spec` validan que la rama actual coincida con la convención `feature/*` o `hotfix/*`.
2. **Durante la codificación**: Los commits generados por `/work-unit-commit` se realizan sobre la rama de soporte sin tocar `develop` ni `main`.
3. **Antes del PR**: La habilidad `branch-pr` verifica la rama destino (`develop` para features, `main` + `develop` para releases/hotfixes) y la inclusión de recibos de prueba.
