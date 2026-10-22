# Guía de Revisión 4R y Recibos de Verificación

## 1. Principios de la Revisión Basada en Evidencia

En sistemas corporativos y bancarios de alta criticidad, una revisión de código debe generar **evidencia falseable y comprobable**, no simples opiniones subjetivas o aprobaciones superficiales.

Cada cambio se somete a cuatro perspectivas ortogonales (el **Modelo 4R**):

```
       ┌────────────────────────┐
       │       Diff / PR        │
       └───────────┬────────────┘
                   │
    ┌──────────────┼──────────────┬──────────────┐
    ▼              ▼              ▼              ▼
[R1: Riesgo]  [R2: Legibilidad] [R3: Confiabilidad] [R4: Resiliencia]
    │              │              │              │
    └──────────────┴──────┬───────┴──────────────┘
                          ▼
            [Registro Único de Hallazgos]
                          │
                  (¿Hay Bloqueadores?)
                  Sí  /       \ No
                     /         \
        [Refutador Adversarial] [Recibo Aprobado]
```

---

## 2. Las 4 Perspectivas

| Perspectiva | Foco de Análisis | Fallos Principales que Detecta |
|---|---|---|
| **R1: Riesgo** | Seguridad, OWASP, PII/PCI, autenticación, autorización | Fuga de secretos, inyección SQL, omisión de permisos |
| **R2: Legibilidad** | Carga cognitiva, nombres, encapsulamiento, arquitectura | Código espagueti, anidamientos profundos, nombres engañosos |
| **R3: Confiabilidad** | Pruebas de comportamiento, determinismo, casos límite | Comportamiento sin probar, condiciones de carrera, nulos |
| **R4: Resiliencia** | Fugas de recursos, timeouts, degradación controlada | Conexiones abiertas, bloqueos indefinidos, caída en cascada |

---

## 3. Niveles de Severidad y Verificación Adversarial

- **BLOCKER**: Riesgo crítico de seguridad, corrupción o pérdida de datos. Prohibido fusionar hasta resolver o refutar.
- **CRITICAL**: Defecto funcional severo o ausencia de pruebas de contrato.
- **WARNING**: Oportunidad de mejora técnica que no quiebra invariantes centrales.
- **SUGGESTION**: Sugerencia opcional o refinamiento futuro.

### El Verificador Adversarial (Refuter)
Para evitar falsos positivos que paralicen el desarrollo asistido por IA, cualquier hallazgo clasificado como `BLOCKER` o `CRITICAL` puede ser sometido al **Refutador** (`/review-refuter`).
- El Refutador busca evidencia concreta en el código (middleware existente, garantías del tipado, pruebas preexistentes) que demuestre que el riesgo no es real.
- Si se refuta con pruebas, el hallazgo se marca como `Refutado` en el registro y no bloquea la entrega.
