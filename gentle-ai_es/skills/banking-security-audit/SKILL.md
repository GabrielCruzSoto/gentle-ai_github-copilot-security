---
name: banking-security-audit
description: "Estándares de seguridad bancaria, OWASP, tratamiento de datos PCI/PII, pistas de auditoría y confianza cero. Disparador: auditorías, lógica financiera."
license: Apache-2.0
metadata:
  author: gentle-ai-copilot
  version: "1.0"
---

# Habilidad: Auditoría de Seguridad Bancaria

## Cuándo Usar

Cargar esta habilidad al desarrollar o auditar código vinculado con:
- Procesamiento de pagos, libros contables, saldos de cuenta o enrutamiento de transacciones.
- Autenticación de usuarios, tokens de sesión, firmas criptográficas o gestión de accesos.
- Recepción de cargas externas no confiables o datos sensibles de clientes.

## Invariantes Esenciales de Seguridad Bancaria

1. **Precisión Numérica y Representación Monetaria**:
   - Queda terminantemente prohibido utilizar tipos de coma flotante (`float`, `double`) para importes de dinero.
   - Utilizar unidades enteras mínimas (centavos) o tipos decimales de precisión arbitraria (`BigDecimal`, `Decimal`).
2. **Enmascaramiento Defensivo de Datos Financieros y Personales**:
   - Enmascarar números de tarjeta (PAN): mostrar únicamente los últimos cuatro dígitos (`**** **** **** 1234`).
   - Jamás serializar ni volcar cuerpos de peticiones con códigos CVV, contraseñas, PINs o documentos de identidad en archivos de log o telemetría.
3. **Idempotencia Transaccional**:
   - Toda mutación financiera (transferencias, reversas, débitos) debe requerir una cabecera `Idempotency-Key` para evitar ejecuciones duplicadas por reintentos de red.
4. **Pistas de Auditoría Inmutables**:
   - Cada cambio de estado sobre activos financieros debe emitir un registro inmutable que contenga: marca temporal UTC, identidad del operador/cliente, tipo de operación, sumas de verificación y canal de origen.
5. **Autorización con Cierre por Defecto (Fail-Closed)**:
   - Ante cualquier excepción, timeout o respuesta no concluyente del proveedor de identidad, la decisión de autorización debe resolverse como `DENEGADA`.
