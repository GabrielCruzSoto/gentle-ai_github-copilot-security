---
name: issue-root-resolution
description: "Aislar, reproducir y solucionar la causa raíz de un defecto. Disparador: corrección de errores, investigaciones de regresión, post-mortems."
license: Apache-2.0
metadata:
  author: gentle-ai-copilot
  version: "1.0"
---

# Habilidad: Resolución de Causa Raíz

## Cuándo Usar

Cargar esta habilidad al investigar un error en producción, traza de excepción o fallo de comportamiento reportado.

## Protocolo de Resolución

1. **Reproducción Previa a la Solución**:
   - Nunca escribir código correctivo sin antes reproducir el error mediante una prueba determinista que falle de manera predecible.
   - Si no es viable automatizarlo en una prueba unitaria, estructurar un script o arnés de prueba mínimo reproducible.
2. **Análisis de Causa Raíz (5 Porqués)**:
   - Diferenciar el síntoma visible (`NullPointerException`, error HTTP 500) de la causa estructural (estado de concurrencia no contemplado, deserialización defectuosa, condición de carrera).
3. **Corrección Quirúrgica sin Ocultar Estado**:
   - Solucionar la anomalía en el origen. No enmascarar síntomas con comprobaciones defensivas de nulos que perpetúen estados inconsistentes.
   - Validar que la solución no introduzca regresiones en componentes vinculados.
4. **Documentación de Recibos**:
   - Registrar la causa raíz, la prueba de comprobación fallida y la justificación de la solución en `odd/evidence/<id-error>-resolution.md`.
