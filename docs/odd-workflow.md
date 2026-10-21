# Manual de Flujo de Trabajo: Desarrollo Guiado Orgánico (ODD)

## 1. ¿Qué es ODD?

El **Desarrollo Guiado Orgánico (ODD - Organic Driven Development)** es un flujo de ingeniería determinista creado para prevenir la degradación arquitectónica, el desvío de alcance y las asunciones no comprobadas generadas comúnmente por asistentes de IA.

En el desarrollo asistido por IA habitual, los modelos generan código especulativo de forma apresurada, acumulando deuda técnica. ODD impone un ritmo estructurado:

```
Especificación Previa ➔ TDD Estricto ➔ Revisión 4R y Recibos ➔ Unidad de Trabajo Atómica
```

---

## 2. Ejecución Fase por Fase

### Fase 1: Especificación (`odd/tasks/<funcionalidad>.md`)
1. Crear una tarea a partir de `odd/TEMPLATE.md`.
2. Delimitar con precisión qué está dentro del alcance y qué queda explícitamente fuera.
3. Especificar criterios de aceptación y controles negativos (entradas inválidas, fallos de red).
4. Estimar el presupuesto de líneas modificadas (objetivo: ≤ 400 líneas).

### Fase 2: TDD Estricto
1. **Rojo**: Escribir una prueba unitaria o de integración que compruebe el siguiente comportamiento.
2. **Verde**: Escribir el código estrictamente indispensable para que la prueba sea exitosa.
3. **Refactorización**: Optimizar el diseño sin alterar el comportamiento observable.
4. Actualizar la lista de tareas en `odd/tasks/<funcionalidad>.md`.

### Fase 3: Evidencia y Revisión 4R (`odd/evidence/<funcionalidad>.md`)
1. Ejecutar el barrido de revisión 4R (`/review-4r`).
2. Documentar los hallazgos en el registro de evidencias.
3. En caso de hallazgos `BLOCKER` o `CRITICAL`, ejecutar el verificador adversarial (`/review-refuter`).
4. Resolver todos los bloqueadores confirmados antes de continuar.

### Fase 4: Commit de Unidad de Trabajo
1. Confirmar que las pruebas y la documentación estén preparadas junto al código.
2. Verificar que el total de líneas modificadas no exceda las 400 líneas.
3. Ejecutar `/work-unit-commit` para estructurar el mensaje bajo Conventional Commits.
4. Registrar los recibos de verificación finales y marcar la tarea como completada.
