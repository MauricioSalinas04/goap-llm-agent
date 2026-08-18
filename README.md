# Agente Híbrido para NPCs: Deliberación Semántica (LLM) + Ejecución Táctica (GOAP)

Anteproyecto de tesis — Universidad Autónoma de Nuevo León, Facultad de Ingeniería Mecánica y Eléctrica (FIME).

- **Alumno:** Nicolás Mauricio Cantú Salinas (Matrícula 2013576)
- **Asesor:** Raymundo Said Samora Pequeño
- **Documento base:** [`Anteproyecto.pdf`](./Anteproyecto.pdf)

## Descripción

Este proyecto propone e implementará un agente inteligente híbrido para NPCs (Non-Player Characters) dentro de un entorno 3D en Unity, que combina dos niveles de control:

- **Módulo de razonamiento:** un modelo de lenguaje (LLM) compacto, optimizado para inferencia bajo restricciones de latencia, encargado de la deliberación semántica sobre situaciones sociales y de generar intenciones de alto nivel a partir del estado y contexto del agente.
- **Módulo de ejecución táctica:** un planificador **GOAP** (Goal-Oriented Action Planning) que traduce esas intenciones en secuencias de acciones ejecutables dentro de las restricciones físicas del motor de juego.

El objetivo es explorar la viabilidad técnica de esta arquitectura híbrida para simular comportamientos sociales en NPCs, evitando tanto la rigidez del scripting manual (FSM / Utility AI) como el costo computacional y la falta de anclaje espacial de usar un LLM como controlador único.

## Objetivo general

Implementar un agente inteligente híbrido dentro de un entorno 3D acotado, que combine un componente de deliberación basado en un modelo de lenguaje compacto con un componente de ejecución táctica basado en GOAP, con el fin de explorar la viabilidad de este tipo de integración para la simulación de comportamientos sociales en NPCs.

## Objetivos particulares

1. Diseñar el módulo de razonamiento del agente, integrando un modelo de lenguaje compacto optimizado para latencia que permita evaluar situaciones sociales básicas y generar intenciones de alto nivel.
2. Implementar el módulo de ejecución táctica en Unity mediante un planificador GOAP que reciba las intenciones del módulo de razonamiento y las traduzca en secuencias de acciones ejecutables.
3. Validar el funcionamiento del agente en un prototipo acotado, con una interfaz de depuración visual para inspeccionar el razonamiento y las decisiones del agente, documentando latencia y coherencia de las acciones.

## Alcance

El proyecto se acota exclusivamente al componente de **interacciones sociales** del comportamiento del agente, asumiendo representaciones simplificadas del entorno físico y del estado interno (necesidades fisiológicas). La interacción entre módulos se limita a un único agente operando en una escena controlada de Unity, con un conjunto reducido de acciones y situaciones sociales predefinidas.

## Contribución esperada

- Diseño e implementación del agente híbrido (LLM + GOAP) en Unity 3D.
- Entorno de prueba acotado para la operación del agente.
- Interfaz de depuración visual en tiempo real (estado interno, decisiones y justificación de acciones).
- Documentación empírica del comportamiento observado y del costo computacional del modelo de lenguaje en conjunto con el planificador.

## Estado del proyecto

🚧 En fase de anteproyecto / planeación. Ver el [cronograma tentativo](./Anteproyecto.pdf) (16 semanas) para las etapas: revisión y marco teórico, diseño metodológico, desarrollo del módulo táctico (GOAP), desarrollo del módulo de razonamiento (LLM), integración y UI de depuración, pruebas de desempeño, y documento final.

## Referencias

Ver la sección de referencias en [`Anteproyecto.pdf`](./Anteproyecto.pdf), incluyendo trabajos sobre arquitecturas GOAP modulares, razonamiento social en agentes generativos, y balance latencia/precisión en decisiones con LLMs.
