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

---

## 🙏 Credits & Acknowledgements / Créditos y Reconocimientos

This project is a specialized adaptation inspired by and derived from **[Gentle AI](https://github.com/Gentleman-Programming/gentle-ai)**, an outstanding open-source deterministic harness for coding agents created and maintained by **[Gentleman Programming](https://github.com/Gentleman-Programming)**.

All original architectural concepts — including **Organic Driven Development (ODD)**, the **4R Review Framework (Risk, Readability, Reliability, Resilience)**, **Verification Receipts**, and the **Senior Architect mindset (Concepts > Code)** — belong to the Gentle AI project. This repository exists to bring those exact same principles into restricted corporate banking environments utilizing purely declarative VS Code + GitHub Copilot configurations without external binaries or third-party daemons.

---

Este proyecto es una adaptación especializada inspirada y derivada de **[Gentle AI](https://github.com/Gentleman-Programming/gentle-ai)**, un extraordinario harness determinista de código abierto para agentes de desarrollo creado y mantenido por **[Gentleman Programming](https://github.com/Gentleman-Programming)**.

Todos los conceptos arquitectónicos originales — incluyendo el **Desarrollo Guiado Orgánico (ODD)**, el **Modelo de Revisión 4R (Riesgo, Legibilidad, Confiabilidad, Resiliencia)**, los **Recibos de Verificación** y la filosofía de **Bases Sólidas y Conceptos sobre Código** — pertenecen al proyecto Gentle AI. Este repositorio adapta esa disciplina a entornos bancarios restringidos mediante configuraciones declarativas nativas para VS Code + GitHub Copilot sin requerir binarios externos ni daemons de terceros.

