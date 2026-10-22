# Arquitectura: Gentle AI para GitHub Copilot

## 1. Visión General y Filosofía Central

**gentle-ai-copilot** adapta los principios contrastados del ecosistema Gentle AI para organizaciones y entidades bancarias donde los ingenieros utilizan **VS Code + GitHub Copilot** y las herramientas de terceros, agentes autónomos o daemons en línea de comandos están restringidos.

Las plataformas de arnés de agentes convencionales dependen de procesos residentes en segundo plano, servidores MCP locales y dependencias en Node, Python o Go que frecuentemente infringen las normativas de seguridad de las entidades financieras.

`gentle-ai-copilot` consigue el mismo rigor arquitectónico utilizando de manera **100% nativa los archivos de configuración de VS Code y GitHub Copilot, junto con artefactos de Git y Markdown**:

```
┌─────────────────────────────────────────────────────────────┐
│                    VS Code + GitHub Copilot                 │
│                                                             │
│   ┌────────────────────────┐    ┌──────────────────────┐    │
│   │ .github/copilot-       │    │ .github/prompts/     │    │
│   │ instructions.md        │    │ *.prompt.md          │    │
│   │ (Reglas Globales)      │    │ (Agentes / Roles)    │    │
│   └───────────┬────────────┘    └──────────┬───────────┘    │
└───────────────┼────────────────────────────┼────────────────┘
                │                            │
                ▼                            ▼
┌─────────────────────────────────────────────────────────────┐
│             Harness Sin Herramientas Externas               │
│                                                             │
│   odd/tasks/              odd/evidence/         skills/     │
│   (Especificaciones ODD)  (Ledgers de Revisión) (Habilidades│
└─────────────────────────────────────────────────────────────┘
```

## 2. Pilares Fundamentales

| Pilar | En Gentle AI CLI | En Gentle AI Copilot |
|---|---|---|
| **Memoria** | Daemon Engram + MCP SQLite | Historial de Git + `odd/tasks/` + bitácoras en Markdown |
| **Workflow** | Protocolo ODD vía binario en Go | `.github/copilot-instructions.md` + `/odd-spec` + `/tdd-cycle` |
| **Evidencia** | Recibos generados por CLI | `.github/prompts/review-4r.prompt.md` + `odd/evidence/*.md` |
| **Seguridad** | Aislamiento por sandbox | Cero ejecutables externos, compatible con redes aisladas |

## 3. Prompts / Agentes Especializados de Copilot

Los archivos de prompt de VS Code (`.github/prompts/*.prompt.md`) proporcionan roles especializados invocables directamente en Copilot Chat:

1. **`orchestrator`**: Arquitecto principal que coordina ODD, TDD y presupuesto de líneas.
2. **`odd-spec`**: Generador y mantenedor de tareas antes de escribir código.
3. **`tdd-cycle`**: Guía del ciclo estricto Rojo -> Verde -> Refactorización.
4. **`review-4r`**: Revisor multidimensional (Riesgo, Legibilidad, Confiabilidad, Resiliencia).
5. **`review-refuter`**: Verificador adversarial de hallazgos críticos con contra-evidencia.
6. **`banking-security`**: Auditor de OWASP, fuga de datos y reglas financieras.
7. **`work-unit-commit`**: Empaquetador de commits atómicos bajo 400 líneas.
