# Diagramas UML

Este espacio centraliza los modelos gráficos y especificaciones que describen la estructura y el comportamiento dinámico de nuestro **Sistema de Turnos Médicos**.

## 🏛️ Modelo Estático y Requerimientos (Entregas Anteriores)
- [Diagrama de Clases](01-diagrama-clases/diagrama_clases.md) — Representación de la estructura del sistema, sus clases, atributos, métodos y relaciones fundamentales.
- [Diagramas de Casos de Uso](02-casos-de-uso/diagramas_de_casos_de_uso.md) — Definición del alcance del sistema y las interacciones entre los actores y las funcionalidades principales.
- [Escenarios de Casos de Uso](03-escenarios-casos-de-uso/escenarios_de_casos_de_uso.md) — Documentación detallada de los flujos principales, alternativos y excepciones de cada caso de uso.

## 📊 Modelo Dinámico y Operativo (Actividad N°3)
- [Diagramas de Actividades](04-diagramas-actividades/diagramas_de_actividades.md) — Modelado del flujo de trabajo y la lógica de negocio de los 5 Casos de Uso, distribuyendo actividades mediante carriles (*swimlanes*) para delimitar responsabilidades claras.
- [Diagramas de Secuencia](05-diagramas-secuencia/diagramas_de_secuencias.md) — Representación de la interacción temporal y cronológica entre los objetos del sistema, detallando el intercambio de mensajes en formato `camelCase` y el control del ciclo de vida de los componentes.

## 📌 Complementariedad entre Modelos

Los nuevos diagramas de la Actividad N°3 refuerzan el análisis del sistema al sumar la visión dinámica a la base estática ya representada.

- El **Diagrama de Clases** describe la estructura estática del sistema: clases, atributos, métodos y relaciones.
- Los **Diagramas de Actividades** modelan los flujos de trabajo, decisiones y responsabilidades por carriles (*swimlanes*) para los 5 Casos de Uso, mostrando cómo se ejecuta la lógica de negocio en cada proceso.
- Los **Diagramas de Secuencia** representan la interacción temporal entre los objetos y las llamadas de mensaje en cada escenario, evidenciando el orden y el ciclo de vida de los componentes.

Juntos, estos artefactos:
- conectan el comportamiento operativo con la arquitectura del sistema,
- permiten verificar que el diseño de clases soporta los procesos reales,
- y garantizan coherencia entre el modelo estático y el modelo dinámico del Sistema de Turnos Médicos.