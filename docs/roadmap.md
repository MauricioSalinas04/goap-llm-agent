# Roadmap del proyecto

Fuente de verdad del avance de la tesis. Traduce el cronograma de 16 semanas del [`Anteproyecto.pdf`](../Anteproyecto.pdf) en épicas secuenciadas por fecha real, cada una con hipótesis/objetivo, entregable, criterio de éxito y dependencias.

Este roadmap **no es un contrato**: si una etapa se atrasa, se recorren las fechas de las etapas siguientes en vez de comprimir el alcance definido en el anteproyecto.

Inicio del proyecto (S1): **lunes 3 de agosto de 2026**.

## Línea de tiempo

| # | Épica | Semanas | Fechas | Estado |
|---|---|---|---|---|
| 1 | Revisión y Marco Teórico | S1–S3 | 3 ago – 23 ago 2026 | 🟡 En curso |
| 2 | Diseño Metodológico | S4–S5 | 24 ago – 6 sep 2026 | ⬜ Pendiente |
| 3 | Desarrollo: Módulo Táctico (GOAP) | S6–S8 | 7 sep – 27 sep 2026 | ⬜ Pendiente |
| 4 | Desarrollo: Módulo de Razonamiento (LLM) | S9(SG)–S11 | 28 sep – 18 oct 2026 | ⬜ Pendiente |
| 5 | Integración y UI de Depuración | S12–S13 | 19 oct – 1 nov 2026 | ⬜ Pendiente |
| 6 | Pruebas y Análisis de Desempeño | S14 | 2 nov – 8 nov 2026 | ⬜ Pendiente |
| 7 | Conclusiones y Documento Final | S15–S16 | 9 nov – 22 nov 2026 | ⬜ Pendiente |

Cada épica tiene su [Milestone](https://github.com/MauricioSalinas04/goap-llm-agent/milestones) correspondiente en GitHub con la fecha de cierre de la tabla. Los Issues de tareas puntuales se crean al arrancar cada etapa, no de antemano.

## Épicas

### 1. Revisión y Marco Teórico
- **Objetivo:** consolidar la revisión de literatura (FSM/Utility AI, Comme il Faut, Generative Agents/CRSEC, arquitecturas híbridas LLM+GOAP) que sustenta el diseño del agente.
- **Entregable:** [`docs/marco-teorico.md`](./marco-teorico.md) con la síntesis y bibliografía ampliada del anteproyecto.
- **Criterio de éxito:** marco teórico revisado y aprobado por el asesor.
- **Dependencias:** ninguna.

### 2. Diseño Metodológico
- **Objetivo:** definir la arquitectura del agente híbrido antes de escribir código: cómo se comunican el módulo LLM y el módulo GOAP.
- **Entregable:** [`docs/metodologia.md`](./metodologia.md) con diagrama de arquitectura, formato de "intención" (LLM → GOAP), catálogo de acciones disponibles y situaciones sociales predefinidas.
- **Criterio de éxito:** interfaz LLM↔GOAP especificada de forma que ambos módulos (3 y 4) puedan desarrollarse en paralelo sin bloquearse.
- **Dependencias:** (1).

### 3. Desarrollo: Módulo Táctico (GOAP)
- **Objetivo:** implementar el planificador GOAP en Unity, capaz de traducir una intención a una secuencia de acciones ejecutables.
- **Entregable:** [`unity-project/`](../unity-project/) con GOAP funcional, probado con intenciones simuladas (sin LLM todavía).
- **Criterio de éxito:** el planificador genera planes válidos para el conjunto reducido de acciones y goals definidos en (2).
- **Dependencias:** (2).

### 4. Desarrollo: Módulo de Razonamiento (LLM)
- **Objetivo:** integrar un modelo de lenguaje compacto que evalúe situaciones sociales y genere intenciones de alto nivel bajo restricciones de latencia.
- **Entregable:** [`llm-service/`](../llm-service/) con una API que recibe estado + contexto del agente y regresa una intención estructurada en el formato definido en (2).
- **Criterio de éxito:** salida parseable de forma consistente por el módulo GOAP; latencia de inferencia medida y documentada.
- **Dependencias:** (2). Puede desarrollarse en paralelo a (3).

### 5. Integración y UI de Depuración
- **Objetivo:** conectar `llm-service` y `unity-project` end-to-end, y dar visibilidad en tiempo real al razonamiento del agente.
- **Entregable:** integración funcional dentro de `unity-project/` + interfaz de depuración visual (estado interno, intención del LLM, plan GOAP resultante, justificación de la acción).
- **Criterio de éxito:** un escenario social predefinido corre de punta a punta (percepción → LLM → GOAP → acción) y es inspeccionable en la UI.
- **Dependencias:** (3) y (4).

### 6. Pruebas y Análisis de Desempeño
- **Objetivo:** medir el desempeño del agente en las situaciones sociales predefinidas.
- **Entregable:** scripts de prueba en [`tests/`](../tests/) y métricas/logs en [`results/`](../results/) (latencia de inferencia, coherencia de las acciones ejecutadas).
- **Criterio de éxito:** reporte cuantitativo (latencia promedio, tasa de coherencia) y cualitativo del comportamiento observado.
- **Dependencias:** (5).

### 7. Conclusiones y Documento Final
- **Objetivo:** sintetizar hallazgos y evidencia empírica sobre la viabilidad técnica de la arquitectura híbrida.
- **Entregable:** [`docs/conclusiones.md`](./conclusiones.md) y documento final de tesis integrado.
- **Dependencias:** (6).
