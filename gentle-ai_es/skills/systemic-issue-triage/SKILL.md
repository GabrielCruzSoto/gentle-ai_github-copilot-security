---
name: systemic-issue-triage
description: "Clasificar errores por causa estructural en lugar de parches sintomáticos individuales. Disparador: triaje de bugs, gestión de backlog."
license: Apache-2.0
metadata:
  author: gentle-ai-copilot
  version: "1.0"
---

# Habilidad: Triaje Sistémico de Errores

## Cuándo Usar

Cargar esta habilidad al clasificar reportes de errores entrantes o gestionar el backlog de defectos, con el objetivo de evitar la acumulación de parches dispersos que degraden la arquitectura.

## Reglas Obligatorias

1. **Agrupación por Invariante Estructural**:
   - No implementar diez parches individuales para diez síntomas que comparten el mismo fallo de diseño subyacente.
   - Agrupar los defectos según el invariante arquitectónico vulnerado (ciclo de vida de sesión, redondeo monetario, propagación de contexto de autorización).
2. **Una Solución Raíz Cierra el Conjunto**:
   - Diseñar una única modificación estructural que erradique todos los síntomas del grupo.
   - Desarrollar pruebas automatizadas que demuestren la desaparición de cada síntoma agrupado.
3. **Taxonomía de Clasificación**:
   - `Superado`: Error que pierde vigencia ante un rediseño en desarrollo.
   - `Duplicado`: Corresponde a un grupo estructural ya registrado.
   - `Defecto Sistémico`: Fallo real derivado de una ruptura de invariante.
   - `Incompleto`: Información insuficiente del reportador; clarificar antes de codificar.
