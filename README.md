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
3. Abrir GitHub Copilot Chat y escribir `/` para acceder a los prompts especializados:
   - Ejecutar `/odd-spec` para definir la funcionalidad antes de programar.
   - Ejecutar `/tdd-cycle` para implementar con disciplina de pruebas previas.
   - Ejecutar `/review-4r` para auditar los cambios y generar un registro de evidencias.
   - Ejecutar `/banking-security` para validar normas financieras y prevención de fugas de datos.
   - Ejecutar `/work-unit-commit` para estructurar un commit convencional atómico.

---

## 📚 Documentación Técnica

- [Visión General de Arquitectura](docs/architecture.md)
- [Cumplimiento y Seguridad Bancaria](docs/banking-environment.md)
- [Guía de Configuración en VS Code](docs/vscode-copilot-setup.md)
- [Manual del Flujo ODD](docs/odd-workflow.md)
- [Framework de Revisión 4R](docs/review-receipts-guide.md)
