# AGENTS.md — Harnés de Gentle AI para Copilot

## Visión General
Este repositorio alberga el **Harness de Gentle AI para Copilot**, diseñado específicamente para entornos corporativos y bancarios que utilizan **VS Code + GitHub Copilot** con cero herramientas o procesos residentes de terceros.

---

## Índice de Roles y Prompts de Copilot (`.github/prompts/`)

| Archivo de Prompt | Rol | Disparador y Propósito Principal |
|---|---|---|
| `orchestrator.prompt.md` | Orquestador Maestro | Ciclo de vida completo de funcionalidades, coordinación arquitectónica y continuidad de trabajo |
| `odd-spec.prompt.md` | Especialista en Especificaciones ODD | Creación y actualización de tareas en `odd/tasks/<funcionalidad>.md` |
| `tdd-cycle.prompt.md` | Ingeniero de TDD Estricto | Aplicación rigurosa del ciclo Rojo -> Verde -> Refactorización |
| `review-4r.prompt.md` | Revisor 4R | Barridos de revisión técnica bajo Riesgo, Legibilidad, Confiabilidad y Resiliencia |
| `review-refuter.prompt.md` | Refutador Adversarial | Verificación e impugnación con pruebas de hallazgos críticos de revisión |
| `banking-security.prompt.md` | Auditor de Seguridad Bancaria | OWASP Top 10, prevención de fuga de PII/PCI y reglas de seguridad financiera |
| `work-unit-commit.prompt.md` | Especialista en Unidades de Trabajo | Formateo de commits convencionales atómicos bajo 400 líneas |

---

## Subagentes Nativos de GitHub Copilot (`.github/agents/`)

Copilot en VS Code detecta automáticamente estos subagentes en `.github/agents/*.agent.md`. Permiten delegación aislada en contextos independientes con herramientas acotadas:

| Subagente | Archivo | Rol y Ámbito | Herramientas |
|---|---|---|---|
| `Revisor-Riesgo` | `review-risk.agent.md` | Subagente R1: seguridad, OWASP, PII/PCI, autorización | `read`, `search` |
| `Revisor-Legibilidad` | `review-readability.agent.md` | Subagente R2: complejidad cognitiva, SRP, nombres limpios | `read`, `search` |
| `Revisor-Confiabilidad` | `review-reliability.agent.md` | Subagente R3: pruebas de comportamiento, casos límite, determinismo | `read`, `search` |
| `Revisor-Resiliencia` | `review-resilience.agent.md` | Subagente R4: timeouts, fugas de recursos, degradación elegante | `read`, `search` |
| `Refutador-Revision` | `review-refuter.agent.md` | Verificador adversarial de hallazgos BLOCKER/CRITICAL | `read`, `search` |
| `Auditor-Bancario` | `banking-security.agent.md` | Auditoría de normas financieras, matemáticas exactas y trazabilidad | `read`, `search` |
| `Juez-Arbitro` | `jd-judge.agent.md` | Arbitraje de Judgment Day para dirimir discrepancias | `read`, `search` |

---

## Catálogo de Habilidades (`skills/` y `.github/skills/`)

Antes de realizar tareas especializadas, consultar la habilidad correspondiente:

| Habilidad | Ruta | Disparador de Activación |
|---|---|---|
| `work-unit-commits` | `skills/work-unit-commits/SKILL.md` | Dimensionamiento de commits, conventional commits, empaquetado de cambios |
| `branch-pr` | `skills/branch-pr/SKILL.md` | Creación de ramas GitFlow (feature, release, hotfix), redacción de PRs, trazabilidad de auditoría |
| `chained-pr` | `skills/chained-pr/SKILL.md` | División de funcionalidades grandes (>400 líneas) en PRs encadenados |
| `cognitive-doc-design` | `skills/cognitive-doc-design/SKILL.md` | Redacción de documentación técnica escaneable y de alta densidad |
| `comment-writer` | `skills/comment-writer/SKILL.md` | Redacción de comentarios explicativos de arquitectura y feedback de revisión |
| `issue-root-resolution` | `skills/issue-root-resolution/SKILL.md` | Reproducción y resolución de defectos en la causa raíz estructural |
| `systemic-issue-triage` | `skills/systemic-issue-triage/SKILL.md` | Clasificación de errores por invariantes; prevención de acumulación de parches |
| `banking-security-audit` | `skills/banking-security-audit/SKILL.md` | Auditoría de código financiero, pagos y tratamiento de datos sensibles |
