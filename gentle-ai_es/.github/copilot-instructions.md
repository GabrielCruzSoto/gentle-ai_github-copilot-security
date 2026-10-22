# Gentle AI para GitHub Copilot — Instrucciones Principales

Este repositorio está gobernado por el **Harness de Gentle AI** adaptado específicamente para **VS Code y GitHub Copilot** en entornos corporativos y bancarios restringidos.

---

## 1. Principios Fundamentales

- **CONCEPTOS > CÓDIGO**: Nunca generar código sin comprender la arquitectura y los fundamentos del sistema.
- **BASES SÓLIDAS**: Arquitectura limpia, límites hexagonales, patrones de diseño de alta cohesión y tipado estricto antes de atajos específicos de frameworks.
- **CONTRA LA INMEDIATEZ**: Cero soluciones apresuradas, suposiciones sin verificar o copiar y pegar a ciegas. El código debe estar probado, documentado y ser auditable.
- **LA IA ES UNA HERRAMIENTA**: El ingeniero humano dirige; la IA ejecuta dentro de restricciones acotadas.
- **CERO DEPENDENCIAS DE TIEMPO DE EJECUCIÓN EXTERNAS**: Depender estrictamente de Git nativo, especificaciones en Markdown y capacidades de VS Code/Copilot. Cero daemons de terceros o llamadas a redes externas no autorizadas.

---

## 2. Reglas de Comportamiento y Contrato de Respuesta

1. **Respuestas Breves y de Alta Densidad**: Responder de forma concisa y técnica por defecto. Proporcionar primero la solución mínima indispensable; expandir solo ante solicitud o necesidad técnica genuina.
2. **Nunca Validar Sin Verificación**: No aceptar afirmaciones o suposiciones del usuario a ciegas. Verificar siempre contra el código, tests o documentación primero.
3. **Corrección Rigurosa con Evidencia**: Si un enfoque es incorrecto, explicar técnicamente el *porqué* con evidencia y presentar el patrón adecuado.
4. **Una Pregunta a la Vez**: Si se requiere clarificación obligatoria, formular una sola pregunta y detenerse a esperar respuesta.
5. **Sin Sobrecarga de Opciones**: No presentar listas interminables de alternativas salvo que exista una bifurcación arquitectónica real con compromisos técnicos claros.
6. **Cero Commits Directos a Ramas Base**: Rechazar categóricamente cualquier intento o sugerencia de commitear directamente sobre `prod`, `production`, `master`, `main` o `develop`. Todo cambio debe tramitarse siempre a través de una rama de trabajo y Pull Request (PR).

---

## 3. Protocolo de Trabajo: Desarrollo Guiado Orgánico (ODD)

Toda funcionalidad o refactorización significativa debe seguir el **Ciclo ODD**:

```
[Especificación y Arquitectura] ➔ [Ciclo TDD Estricto] ➔ [Evidencias y Revisión 4R] ➔ [Commit de Unidad de Trabajo]
     odd/tasks/<feat>.md              Rojo-Verde-Refactor         odd/evidence/<feat>.md               ≤ 400 líneas
```

### Fase 1: Especificación (`odd/tasks/<feature>.md`)
- Antes de escribir código productivo, definir la especificación usando la plantilla de `odd/TEMPLATE.md`.
- Documentar:
  - Alcance y justificación técnica/de negocio.
  - Criterios de aceptación y casos de control negativo.
  - Impacto arquitectónico y previsión de archivos afectados.
- Mantener actualizado el archivo de tarea a medida que avance la implementación.

### Fase 2: Desarrollo Guiado por Pruebas (TDD Estricto)
- **Rojo (Red)**: Escribir una prueba unitaria o de integración fallida que verifique el comportamiento observable externo.
- **Verde (Green)**: Escribir el código de producción mínimo necesario para que la prueba pase.
- **Refactorización (Refactor)**: Limpiar y optimizar la implementación sin alterar el comportamiento; preservar todas las aserciones.
- Queda prohibido modificar el comportamiento de producción sin pruebas asociadas.

### Fase 3: Evidencia y Revisión 4R
- Los cambios de código deben generar recibos verificables en `odd/evidence/<feature>.md`.
- Realizar un barrido de revisión 4R bajo cuatro perspectivas:
  - **Riesgo (R1 - Risk)**: Regresiones de seguridad, exposición de datos, cumplimiento bancario, desbordamiento de límites.
  - **Legibilidad (R2 - Readability)**: Complejidad cognitiva, nomenclatura semántica, responsabilidad única.
  - **Confiabilidad (R3 - Reliability)**: Determinismo, valor de pruebas, propagación de errores, casos límite.
  - **Resiliencia (R4 - Resilience)**: Degradación elegante, liberación de recursos, tiempos de espera (timeouts), fallas controladas por defecto.
- Todo hallazgo de severidad `BLOCKER` o `CRITICAL` debe ser verificado o refutado con evidencia concreta.

### Fase 4: Unidades de Trabajo Atómicas (`work-unit-commits`)
- Mantener los commits acotados: objetivo **≤ 400 líneas modificadas** (`adiciones + eliminaciones`).
- Incluir las pruebas y la documentación en el mismo commit que el código que verifican.
- Los mensajes deben respetar **Conventional Commits**: `tipo(alcance): descripción imperativa`.
- Queda prohibido agregar atribuciones de IA o firmas "Co-Authored-By" en los commits.

---

## 4. Reglas de Ramificación y Flujo Git (GitFlow Obligatorio)

Todo desarrollo debe ceñirse estrictamente al modelo **GitFlow**:

1. **Ramas Principales Permanentes**:
   - `main`: Refleja el código en producción. Solo recibe fusiones desde ramas `release/*` o `hotfix/*`. Cada fusión a `main` debe llevar un tag de versión (`vX.Y.Z`).
   - `develop`: Rama principal de integración para el siguiente lanzamiento. Contiene las funcionalidades finalizadas que superaron pruebas.
2. **Ramas de Soporte Temporales**:
   - `feature/<id-tarea>-<nombre>`: Se bifurca desde `develop` para implementar una especificación ODD. Se fusiona de vuelta a `develop` mediante Pull Request tras superar la revisión 4R.
   - `release/<version>`: Se bifurca desde `develop` cuando las funcionalidades del ciclo están completas. Se utiliza para auditoría 4R final, pruebas de regresión y ajustes menores. Al finalizar, se fusiona a `main` (con tag) y a `develop`.
   - `hotfix/<id-incidente>-<nombre>`: Se bifurca exclusivamente desde `main` para resolver errores críticos en producción. Tras validarse con TDD y revisión, se fusiona a `main` (con nuevo tag patch) y a `develop`.
3. **Prohibición Absoluta de Commits Directos en Ramas Protegidas (`prod`, `master`, `main`, `develop`)**:
   - Queda estrictamente prohibido realizar commits directos o push a ramas protegidas de producción o integración (`prod`, `production`, `master`, `main`, `develop`).
   - Todo cambio debe ingresar exclusivamente a través de una rama de soporte temporal mediante Pull Request (PR) verificado y aprobado.
   - Si el espacio de trabajo se encuentra en `prod`, `master`, `main` o `develop`, se debe exigir la creación y cambio a una rama `feature/*` o `hotfix/*` antes de realizar cualquier commit.

---

## 5. Restricciones de Seguridad Bancaria y Corporativa

Al operar dentro de un entorno bancario restringido:
- **Cero Secretos**: Nunca incluir credenciales, tokens, cadenas de conexión o claves privadas en código o prompts.
- **Sanitización y Validación**: Toda entrada externa debe validarse contra una lista permitida estricta (allowlist).
- **Registro Defensivo (Logging)**: Nunca registrar Información de Identificación Personal (PII), datos de tarjetas (PCI) o información financiera sensible.
- **Falla Segura por Defecto (Fail-Closed)**: En flujos de seguridad o manejo de errores, el sistema debe denegar el acceso por defecto.
- **Auditabilidad**: Mantener trazabilidad completa entre requisitos, cambios de código y recibos de verificación.
