# gentle-ai-copilot

> **Deterministic Harness for VS Code + GitHub Copilot in Restricted Enterprise & Banking Environments**
> **Harness determinista para VS Code + GitHub Copilot en entornos corporativos y bancarios restringidos**

This repository provides the **Gentle AI Copilot Harness** packaged into two language distributions:

Este repositorio proporciona el **Harness de Gentle AI para Copilot** empaquetado en dos distribuciones por idioma:

---

## 📁 Repository Structure / Estructura del Repositorio

```
gentle-ai-copilot/
├── gentle-ai_es/      # Distribución completa en Español
│   ├── .github/       # Instrucciones (.github/copilot-instructions.md), prompts y skills
│   ├── docs/          # Guías de arquitectura, seguridad bancaria, GitFlow y ODD
│   ├── odd/           # Plantillas ODD (Organic Driven Development), tareas y evidencias
│   ├── skills/        # Catálogo de habilidades en Markdown
│   ├── AGENTS.md      # Índice integral de roles, prompts y habilidades
│   └── README.md      # Documentación y guía de inicio rápido en español
│
├── gentle-ai_en/      # Complete English Distribution
│   ├── .github/       # Instructions (.github/copilot-instructions.md), prompts & skills
│   ├── docs/          # Architecture, banking security, GitFlow, and ODD guides
│   ├── odd/           # ODD (Organic Driven Development) templates, tasks & evidence
│   ├── skills/        # Markdown skills catalog
│   ├── AGENTS.md      # Comprehensive index of roles, prompts, and skills
│   └── README.md      # Documentation and quickstart guide in English
│
├── .gitignore
└── README.md
```

---

## 🚀 How to Use / Modo de Uso

### En Español (`gentle-ai_es/`)
1. Copia el contenido del directorio `gentle-ai_es/` a la raíz de tu proyecto bancario:
   ```bash
   cp -r gentle-ai_es/.github gentle-ai_es/docs gentle-ai_es/odd gentle-ai_es/skills gentle-ai_es/AGENTS.md /ruta/a/tu/proyecto/
   ```
2. Abre el proyecto en VS Code con GitHub Copilot habilitado.
3. Consulta [`gentle-ai_es/README.md`](gentle-ai_es/README.md) para más detalles.

### In English (`gentle-ai_en/`)
1. Copy the contents of the `gentle-ai_en/` directory into the root of your repository:
   ```bash
   cp -r gentle-ai_en/.github gentle-ai_en/docs gentle-ai_en/odd gentle-ai_en/skills gentle-ai_en/AGENTS.md /path/to/your/project/
   ```
2. Open the project in VS Code with GitHub Copilot enabled.
3. Consult [`gentle-ai_en/README.md`](gentle-ai_en/README.md) for full details.

---

## 🏛️ Key Principles / Principios Clave
- **Zero Third-Party Dependencies / Cero Dependencias de Terceros**: Native to VS Code and GitHub Copilot (`.prompt.md`, `.github/copilot-instructions.md`).
- **GitFlow & Protected Branches / GitFlow y Ramas Protegidas**: Direct commits or pushes to `prod`, `production`, `master`, `main`, and `develop` are strictly prohibited. All changes must be routed via Pull Requests.
- **Organic Driven Development (ODD)**: Specifications in `odd/tasks/` before production code; strict Test-Driven Development (TDD).
- **4R Review & Receipts / Revisión 4R y Evidencias**: Risk, Readability, Reliability, Resilience sweeps with adversarial refuters.
