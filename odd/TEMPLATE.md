# Especificación de Funcionalidad ODD: <Nombre de la Funcionalidad>

- **Estado**: `borrador` | `en-progreso` | `en-revision` | `completado`
- **Responsable**: <Desarrollador / Pareja>
- **Presupuesto de Líneas**: ≤ 400 líneas modificadas
- **Tarea o Ticket Base**: #<ID-Issue>
- **Rama GitFlow**: `feature/<id-tarea>-<slug>` (Base: `develop`, Destino PR: `develop`)

---

## 1. Intención y Valor de Negocio

### ¿Qué problema estamos resolviendo?
Descripción concisa de la necesidad funcional o arquitectónica.

### Fuera de Alcance (No-Objetivos)
Enumerar explícitamente lo que NO será abordado en esta unidad de trabajo.

---

## 2. Diseño e Impacto Arquitectónico

### Límites de Componentes y Módulos
- **Interfaces / Tipos Modificados**:
- **Nuevos Archivos**:
- **Cambios en Contratos Públicos**:

### Lista de Verificación de Seguridad Bancaria
- [ ] Cero datos PII/PCI en logs o excepciones
- [ ] Matemática monetaria exacta (sin coma flotante)
- [ ] Autorización y validación con falla segura por defecto (fail-closed)
- [ ] Idempotencia implementada si es una mutación transaccional

---

## 3. Criterios de Aceptación y Controles Negativos

### Escenarios de Éxito (Camino Feliz)
1. Dado `<contexto>`, cuando `<acción>`, entonces `<resultado esperado>`.

### Escenarios de Control Negativo y Casos Límite
1. Dado `<entrada inválida o vacía>`, cuando `<acción>`, entonces `<error esperado / rechazo>`.
2. Dado `<tiempo de espera / fallo externo>`, cuando `<acción>`, entonces `<degradación controlada>`.

---

## 4. Tareas de Ejecución (TDD Estricto)

- [ ] **Paso 1 (Prueba Primero)**: Agregar prueba de comportamiento fallida en `test/<modulo>.test.ts`
- [ ] **Paso 2 (Implementación)**: Implementación mínima en `src/<modulo>.ts`
- [ ] **Paso 3 (Refactorización y Tipado)**: Limpiar diseño y robustecer contratos
- [ ] **Paso 4 (Revisión)**: Ejecutar barrido de revisión 4R (`/review-4r`) y registrar recibos
- [ ] **Paso 5 (Commit)**: Commit convencional atómico (≤ 400 líneas)

---

## 5. Recibos de Verificación y Evidencias

Enlace al registro de evidencias: `odd/evidence/<funcionalidad>-recibos.md`

- **Comando de Suite de Pruebas**: `npm test` / `pytest` / `go test ./...`
- **Resultado**: `Superado (X pruebas, 0 fallos)`
- **Ledger de Revisión**: `R1: Limpio | R2: Limpio | R3: Limpio | R4: Limpio`
