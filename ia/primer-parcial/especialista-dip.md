# Documentación de Uso de IA - Especialista DIP

## 🤖 Herramienta Utilizada
**GitHub Copilot - Agent Mode (VS Code)**

## 💬 Prompt Utilizado

```Rol: Actuá como un Arquitecto de Software experto en principios SOLID, específicamente en el Principio de Inversión de Dependencias (DIP). Contexto: Estoy trabajando en el "Sistema de Turnos Médicos". Revisá los siguientes archivos como base de conocimiento: - anexos/introduccion.md (Contexto de negocio). - diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw (Estructura de clases). - Todos los archivos .md en herramientas-agile/tarjetas-crc/ (Responsabilidades y colaboraciones). Tarea: Identificá todos los puntos críticos en el diseño actual donde las clases de alto nivel (ej. lógica de asignación de turnos o registro de llegada) dependan directamente de clases de bajo nivel (clases concretas), generando un acoplamiento rígido. Para cada punto identificado, por favor: 1. Diagnóstico: Explicá por qué la dependencia actual rompe el principio DIP. 2. Propuesta de Abstracción: Definí una Interfaz o Clase Abstracta que actúe como mediadora para invertir la dependencia. 3. Inyección de Dependencias: Indicá en qué clase y mediante qué método se debería inyectar la nueva abstracción. 4. Beneficio: Explicá cómo este cambio facilita la extensibilidad del sistema (por ejemplo, permitir cambiar el motor de base de datos o el servicio de notificaciones sin afectar la lógica central).```

## 📂 Archivos de contexto referenciados
* `anexos/introduccion.md`
* `diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw`
* `herramientas-agile/tarjetas-crc/` (Directorio completo).

## 📤 Output obtenido (Fragmento representativo)
Copilot identificó acoplamientos en la clase `Sistema` con servicios de infraestructura y en el flujo de `LlegadaPaciente` con la clase `SalaEspera`. Sugirió la creación de interfaces como `IPersistenciaRepository`, `INotificacionService` e `IEspacioEspera`, proponiendo inyección vía constructor para desacoplar los módulos de alto nivel.

## 🛠️ Ajustes realizados
1. **Filtro de Dominio:** Se descartó la propuesta de `IPersistenciaRepository`. Se determinó que, para el alcance de este parcial, el enfoque debe estar en la lógica de dominio médico y no en patrones de persistencia técnica.
2. **Refinamiento Semántico:** Se modificó la abstracción `IEspacioEspera` por **`IGestorPrioridad`**. El ajuste permite que la clase `LlegadaPaciente` delegue la decisión de orden de atención a una estrategia intercambiable (Strategy Pattern), cumpliendo con el requisito de flexibilidad del sistema.
3. **Consistencia de Nombres:** Se renombró `INotificacionService` a **`IServicioComunicacion`** para mantener coherencia con el lenguaje utilizado en el resto de la documentación técnica del equipo.