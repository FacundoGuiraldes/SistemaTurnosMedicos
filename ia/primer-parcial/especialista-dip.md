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
Copilot identificó un acoplamiento crítico en la clase `Sistema` con la implementación concreta `WhatsAppService`. La IA diagnosticó que esta dependencia directa violaba el DIP, ya que cualquier cambio en la API de WhatsApp o la incorporación de nuevos canales de comunicación obligaría a modificar la lógica central del sistema. Para resolver esto, Copilot sugirió la creación de una **interfaz de servicio de comunicación** que actuara como abstracción, permitiendo que `Sistema` dependiera de un contrato en lugar de una implementación concreta. Propuso además la inyección de la dependencia a través del constructor para garantizar flexibilidad y testabilidad.

## 🛠️ Ajustes realizados
1. **Focalización en Inversión de Dependencias de Comunicación:** Se descartaron propuestas genéricas de Copilot tales como `IPersistenciaRepository` (patrón de persistencia) e `IEspacioEspera` (lógica de gestión de sala de espera). Se determinó que, para el alcance de este parcial, el enfoque debía concentrarse exclusivamente en la **inversión de dependencias entre la clase de alto nivel `Sistema` y los servicios de comunicación de bajo nivel**, dejando otros patrones de infraestructura para iteraciones futuras.
2. **Ajuste Semántico del Nombre:** La interfaz fue renombrada a **`IServicioComunicacion`** en lugar del nombre genérico `INotificacionService`. Este ajuste asegura coherencia semántica con el dominio médico y la terminología utilizada en la documentación técnica del equipo, reflejando fielmente que el sistema requiere un servicio que maneje la comunicación integral (notificaciones, confirmaciones, etc.).
3. **Validación Manual del Diagrama UML:** Se revisó manualmente el diagrama UML (archivo `01-solid-05-dip.puml`) para confirmar que la abstracción reflejada fielmente la estructura propuesta: `Sistema` depende de `IServicioComunicacion`, y las implementaciones concretas (`WhatsAppService`, potencialmente `EmailService` o `SMSService` en el futuro) implementan la interfaz. Esta validación garantiza la correcta aplicación del principio de inversión de dependencias en el diseño.