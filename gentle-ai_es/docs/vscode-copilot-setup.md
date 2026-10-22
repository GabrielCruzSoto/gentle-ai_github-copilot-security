# Guía de Configuración: VS Code + GitHub Copilot

Esta guía detalla los pasos para habilitar y operar con `gentle-ai-copilot` en Visual Studio Code.

---

## 1. Requisitos Previos

- Visual Studio Code (v1.90 o superior).
- Extensiones oficiales de GitHub Copilot y GitHub Copilot Chat instaladas y autenticadas con la cuenta corporativa.
- No se requiere ninguna otra extensión ni herramienta de línea de comandos.

---

## 2. Incorporación a un Proyecto

Para aplicar `gentle-ai-copilot` a un repositorio nuevo o existente dentro de la red corporativa:

1. Copiar los siguientes directorios y archivos a la raíz del proyecto:
   ```
   .github/
   ├── copilot-instructions.md
   ├── prompts/
   └── skills/
   odd/
   ├── TEMPLATE.md
   ├── tasks/
   └── evidence/
   AGENTS.md
   ```
2. Abrir el proyecto en VS Code.

---

## 3. Carga Automática en Copilot

- **Instrucciones Globales del Repositorio**:
  VS Code Copilot detecta automáticamente `.github/copilot-instructions.md`. Cualquier consulta en Copilot Chat o autocompletado inline respetará los principios arquitectónicos, el límite de líneas y las reglas de seguridad bancaria.
- **Archivos de Prompt (`.prompt.md`)**:
  Los prompts ubicados en `.github/prompts/` quedan accesibles interactivamente en Copilot Chat:
  - En Copilot Chat, escribir `/` o pulsar el selector de prompts para ejecutar:
    - `/orchestrator` — Iniciar la planificación y orquestación arquitectónica.
    - `/odd-spec` — Redactar una especificación técnica en `odd/tasks/`.
    - `/tdd-cycle` — Desarrollar bajo la disciplina estricta Rojo-Verde-Refactor.
    - `/review-4r` — Ejecutar el barrido de revisión 4R sobre los cambios actuales.
    - `/review-refuter` — Auditar y verificar hallazgos críticos con contra-evidencia.
    - `/banking-security` — Realizar auditoría de seguridad y cumplimiento financiero.
    - `/work-unit-commit` — Generar el commit convencional atómico bajo 400 líneas.
- **Habilidades (`skills/` y `.github/skills/`)**:
  Se puede invocar cualquier habilidad en Copilot Chat haciendo referencia a su archivo mediante `#file` (ej. `#file:skills/work-unit-commits/SKILL.md`) o solicitando consultar el índice de `AGENTS.md`.
