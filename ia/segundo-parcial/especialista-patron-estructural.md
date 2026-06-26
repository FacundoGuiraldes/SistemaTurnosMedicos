# Bitácora del Especialista en Patrón de Diseño Estructural

## Rol

Especialista en Patrón de Diseño Estructural

## Objetivo

Identificar un problema estructural en el Sistema de Turnos Médicos, seleccionar un patrón GoF de tipo estructural y documentar su aplicación mediante un anexo explicativo y un diagrama de clases UML en PlantUML.

## Patrón seleccionado

Se seleccionó el patrón **Facade**.

El problema identificado es que los casos de uso principales requieren coordinar varias clases del dominio y servicios internos. Si los clientes del sistema conocieran directamente esa estructura, quedarían acoplados a demasiados detalles. `Sistema` se explicita como fachada porque ofrece operaciones de alto nivel y delega internamente en `Agenda`, `Turno`, `SalaEspera`, `PersistenciaService`, `ServicioNotificaciones`, `ServicioAutenticacion` y `AuditoriaService`.

## Prompt utilizado para CoPilot

```text
Actúa como Especialista en Patrón de Diseño Estructural para el proyecto "Sistema de Turnos Médicos".

Necesito aplicar un patrón estructural sobre el diseño existente. La entrega debe ser textual y mediante diagramas UML.

Usa como contexto obligatorio los siguientes archivos:
- diagramas/01-diagrama-clases/06-clases-diagrama-final.puml
- diagramas/01-diagrama-clases/01-solid-01-srp.puml
- diagramas/01-diagrama-clases/01-solid-02-ocp.puml
- diagramas/01-diagrama-clases/01-solid-03-lsp.puml
- diagramas/01-diagrama-clases/01-solid-04-isp.puml
- diagramas/01-diagrama-clases/01-solid-05-dip.puml

Tarea:
1. Identificar un problema estructural concreto del sistema.
2. Seleccionar el patrón estructural más apropiado entre Adapter, Bridge, Composite, Decorator, Facade o Proxy.
3. Justificar por qué el patrón elegido resuelve el problema.
4. Crear un diagrama de clases UML en PlantUML con las clases directamente involucradas.
5. Redactar el anexo patron-de-diseno-estructural.md con introducción, propósito, motivación, estructura de clases y justificación técnica.

Restricciones:
- Mantener coherencia con el diagrama de clases final y con los principios SOLID ya documentados.
```

## Archivos de contexto referenciados

- `diagramas/01-diagrama-clases/06-clases-diagrama-final.puml`
- `diagramas/01-diagrama-clases/01-solid-01-srp.puml`
- `diagramas/01-diagrama-clases/01-solid-02-ocp.puml`
- `diagramas/01-diagrama-clases/01-solid-03-lsp.puml`
- `diagramas/01-diagrama-clases/01-solid-04-isp.puml`
- `diagramas/01-diagrama-clases/01-solid-05-dip.puml`

## Ajustes realizados al output de la IA

1. Se descartó una primera alternativa basada en `Adapter` porque podía llevar el análisis hacia integraciones con servicios externos o APIs, fuera del alcance indicado para esta entrega.
2. Se seleccionó `Facade` por ser más coherente con una entrega textual y de diagramas, y porque el diagrama final ya contiene una clase `Sistema` que puede formalizarse como punto de entrada estructural.
3. Se acotó el diagrama a clientes, fachada y subsistemas internos para evitar sobrecargarlo con todas las clases del modelo.
4. Se aclaró que `Sistema` no debe transformarse en una clase con todas las reglas de negocio. Su rol es coordinar operaciones de alto nivel, mientras `Agenda`, `Turno`, `SalaEspera` y los servicios conservan sus responsabilidades.

## Iteraciones relevantes

1. Se revisó el diagrama de clases final para identificar clases de coordinación y subsistemas internos.
2. Se revisaron los diagramas SOLID para mantener coherencia con SRP, OCP, LSP, ISP y DIP.
3. Se creó el diagrama `01-patron-estructural-facade.puml`.
4. Se redactó el anexo `patron-de-diseno-estructural.md`.
5. Se actualizaron los índices de anexos y diagramas para incorporar la nueva entrega.

## Entregables generados

- `anexos/patrones-diseno/patron-de-diseno-estructural.md`
- `diagramas/01-diagrama-clases/01-patron-estructural-facade.puml`
- `ia/segundo-parcial/especialista-patron-estructural.md`S
