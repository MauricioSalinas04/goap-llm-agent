# unity-project

Proyecto de Unity 3D del agente (Unity **6000.6.2f1**, render pipeline **URP**).

Contendrá:

- El planificador **GOAP** (módulo de ejecución táctica) — etapa 3 del [roadmap](../docs/roadmap.md), S6–S8.
- El cliente que consume la API de [`llm-service`](../llm-service/) y traduce sus intenciones en goals de GOAP — etapa 5, S12–S13.
- La escena 3D de prueba acotada descrita en el anteproyecto (un agente, conjunto reducido de acciones, situaciones sociales predefinidas).
- La UI de depuración visual (estado interno, intención del LLM, plan GOAP, justificación) — etapa 5, S12–S13.

## Estructura

Esqueleto inicializado; sin código funcional todavía (se puebla a partir de la etapa 3).

```
Assets/_Project/
├── Scripts/
│   ├── Core/        → Project.Core.asmdef       (sin dependencias)
│   ├── GOAP/        → Project.GOAP.asmdef       (dep: Core)
│   ├── Agent/       → Project.Agent.asmdef      (dep: GOAP, Core)
│   ├── LLMClient/   → Project.LLMClient.asmdef  (dep: Core — sin dep de GOAP)
│   └── DebugUI/     → Project.DebugUI.asmdef    (dep: Core, GOAP, Agent, LLMClient)
├── Tests/EditMode/  → Project.Tests.asmdef
├── Scenes/          → TestScene.unity
├── Prefabs/
├── ScriptableObjects/
└── Settings/        → assets de URP (pipeline + renderer)
```

`LLMClient` no depende de `GOAP` a propósito: la interfaz de "intención" definida en `docs/metodologia.md` (etapa 2) permite desarrollar los módulos GOAP (etapa 3) y LLM (etapa 4) en paralelo; la separación de assemblies hace cumplir ese desacople a nivel de compilación.
