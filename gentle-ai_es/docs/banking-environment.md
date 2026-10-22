# Guía de Cumplimiento Bancario y Entornos Corporativos Restringidos

## 1. Por qué los Entornos Bancarios Restringen Herramientas Externas

Las entidades financieras aplican políticas estrictas de ciberseguridad:
- **Prohibición de Binarios no Homologados**: Ningún ejecutable sin firma de código institucional o aprobación expresa puede correr en estaciones de trabajo.
- **Restricción Estricta de Tráfico Saliente (Firewalls / Redes Aisladas)**: Los equipos no pueden abrir conexiones arbitrarias ni invocar APIs externas no autorizadas.
- **Cero Daemons en Segundo Plano**: Procesos residentes locales (como servidores MCP no homologados o listeners de telemetría) disparan alertas en las herramientas EDR (Endpoint Detection & Response).
- **Prevención de Fuga de Datos (DLP)**: El código fuente, datos de clientes y esquemas internos no deben salir del perímetro corporativo.

## 2. Cómo Resuelve Gentle AI Copilot Estas Restricciones

`gentle-ai-copilot` está diseñado desde su concepción para operar en esquemas de Confianza Cero (Zero Trust):

1. **Cero Binarios y Cero Scripts de Ejecución**:
   Todo el sistema está estructurado en Markdown estándar, commits de Git e integraciones nativas de `.github/`. No hay binarios que compilar, daemons de Node que levantar ni entornos virtuales de Python que mantener.
2. **Nativo para VS Code y GitHub Copilot**:
   GitHub Copilot es habitualmente la herramienta de IA homologada corporativamente en las organizaciones. `gentle-ai-copilot` utiliza el motor nativo de instrucciones y prompts de Copilot (`.github/copilot-instructions.md` y `.github/prompts/`), sin requerir extensiones adicionales.
3. **La Información Permanece en el Repositorio**:
   La memoria arquitectónica, los estados de tarea, las revisiones y los recibos de prueba residen íntegramente dentro del repositorio (`odd/tasks/`, `odd/evidence/`). No se envía información a servidores o bases de datos externas.
4. **Protección de Invariantes Financieros**:
   Las habilidades y prompts integrados auditan continuamente:
   - Prohibición de aritmética de coma flotante sobre dinero.
   - Prevención de fuga de PII/PCI en logs y excepciones.
   - Obligatoriedad de compuertas de autorización y cabeceras de idempotencia en mutaciones.
