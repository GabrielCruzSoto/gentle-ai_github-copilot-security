# gentle-ai-copilot

> **Harness determinista para VS Code + GitHub Copilot en entornos corporativos y bancarios restringidos**

`gentle-ai-copilot` traslada la arquitectura, la disciplina de flujo de trabajo y los mecanismos de revisión de **Gentle AI** a una **configuración puramente declarativa, sin binarios ni herramientas de terceros**, diseñada específicamente para Visual Studio Code y GitHub Copilot.

---

## 🏛️ Diseñado para Entornos Bancarios Restringidos

En entidades financieras y redes corporativas reguladas, está terminantemente prohibido ejecutar binarios no autorizados, levantar servidores MCP locales, iniciar daemons en segundo plano o realizar llamadas salientes a servicios de IA de terceros.

`gentle-ai-copilot` ofrece el máximo rigor de ingeniería utilizando **exclusivamente**:
- Instrucciones nativas de GitHub Copilot (`.github/copilot-instructions.md`).
- Archivos de prompt nativos de VS Code (`.github/prompts/*.prompt.md`).
- Habilidades estandarizadas en Markdown (`skills/*/SKILL.md`).
- Flujo de Desarrollo Guiado Orgánico respaldado por Git (`odd/tasks/` y `odd/evidence/`).

Cero instalaciones de software. Cero binarios ajenos. Cero alertas de seguridad.

---

## 📦 Contenido del Repositorio

```
gentle-ai-copilot/
├── .github/
│   ├── copilot-instructions.md          # Reglas globales, contrato de respuesta y seguridad bancaria
│   ├── prompts/                         # Archivos de prompt ejecutables en Copilot Chat
│   │   ├── orchestrator.prompt.md       # Orquestador maestro de arquitectura y flujo
│   │   ├── odd-spec.prompt.md           # Redactor de especificaciones de tareas ODD
│   │   ├── tdd-cycle.prompt.md          # Ejecutor de TDD estricto (Rojo -> Verde -> Refactor)
│   │   ├── review-4r.prompt.md          # Barrido de revisión 4R (Riesgo, Legibilidad, Confiabilidad, Resiliencia)
│   │   ├── review-refuter.prompt.md     # Verificador adversarial de hallazgos críticos
│   │   ├── banking-security.prompt.md   # Auditoría de seguridad bancaria y OWASP
│   │   └── work-unit-commit.prompt.md   # Creación de commits atómicos bajo 400 líneas
│   └── skills/                          # Catálogo de habilidades accesibles en Copilot
├── odd/
│   ├── TEMPLATE.md                      # Plantilla estándar para especificaciones y recibos
│   ├── tasks/                           # Tareas y especificaciones activas
│   └── evidence/                        # Ledgers de revisión y recibos de pruebas
├── docs/
│   ├── architecture.md                  # Arquitectura del sistema y principios rectores
│   ├── banking-environment.md           # Guía de cumplimiento y seguridad en redes bancarias
│   ├── gitflow-workflow.md              # Flujo de trabajo GitFlow para banca y Copilot
│   ├── vscode-copilot-setup.md          # Guía paso a paso de configuración en VS Code
│   ├── odd-workflow.md                  # Manual del ciclo de desarrollo ODD
│   └── review-receipts-guide.md         # Modelo de revisión 4R y evidencias
├── AGENTS.md                            # Índice integral de roles, prompts y habilidades
└── README.md
```

---

## 🚀 Inicio Rápido

1. Copiar las carpetas `.github/`, `odd/` y el archivo `AGENTS.md` a la raíz de tu proyecto bancario.
2. Abrir el proyecto en VS Code con GitHub Copilot habilitado.
3. Asegurarse de que el repositorio cuenta con ramas `main` y `develop` (modelo **GitFlow**).
4. Abrir GitHub Copilot Chat y escribir `/` para acceder a los prompts especializados:
   - Ejecutar `/odd-spec` para definir la funcionalidad y crear la rama `feature/*` desde `develop`.
   - Ejecutar `/tdd-cycle` para implementar con disciplina de pruebas previas.
   - Ejecutar `/review-4r` para auditar los cambios y generar un registro de evidencias.
   - Ejecutar `/banking-security` para validar normas financieras y prevención de fugas de datos.
   - Ejecutar `/work-unit-commit` para estructurar un commit convencional atómico.

---

## 📚 Documentación Técnica

- [Visión General de Arquitectura](docs/architecture.md)
- [Cumplimiento y Seguridad Bancaria](docs/banking-environment.md)
- [Flujo GitFlow en Banca](docs/gitflow-workflow.md)
- [Guía de Configuración en VS Code](docs/vscode-copilot-setup.md)
- [Manual del Flujo ODD](docs/odd-workflow.md)
- [Framework de Revisión 4R](docs/review-receipts-guide.md)

---

## 🙏 Créditos y Reconocimientos

Este proyecto es una adaptación especializada inspirada y derivada de **[Gentle AI](https://github.com/Gentleman-Programming/gentle-ai)**, desarrollado y liderado por **[Gentleman Programming](https://github.com/Gentleman-Programming)**.

Todos los conceptos clave — incluyendo el **Desarrollo Guiado Orgánico (ODD)**, el **Marco de Revisión 4R (Riesgo, Legibilidad, Confiabilidad, Resiliencia)**, la filosofía de **Recibos de Verificación** y los principios de **Conceptos sobre Código** — provienen del proyecto original Gentle AI. Esta adaptación traslada esa misma disciplina a entidades bancarias y corporativas con restricciones de software de terceros mediante configuraciones nativas y declarativas para VS Code y GitHub Copilot.
