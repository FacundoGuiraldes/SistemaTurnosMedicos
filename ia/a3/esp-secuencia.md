# Documentación IA - Especialista en Diagramas de Secuencia

### Diagrama de Secuencia 1: Solicitar Turno - Solicitar turno

**Archivos de contexto referenciados:**
Para la generación de este diagrama se tomaron como contexto explícito los pasos del escenario correspondientes ubicados en `diagramas/03-escenarios-casos-de-uso/` y las responsabilidades de las clases involucradas detalladas en `herramientas-agile/tarjetas-crc/`.

**Prompt utilizado:**
```text
Actúa como un experto en Diseño Orientado a Objetos y UML. Tu tarea es generar el código en PlantUML para el diagrama de secuencia del escenario "Solicitar turno" correspondiente al caso de uso "Solicitar Turno".

Contexto obligatorio: Lee los pasos del escenario en la carpeta `diagramas/03-escenarios-casos-de-uso/` y las responsabilidades de las clases en `herramientas-agile/tarjetas-crc/`.

Genera el código PlantUML cumpliendo ESTRICTAMENTE estas reglas de evaluación:
1. Incluye al menos 4 participantes. El primero (a la izquierda) debe representar al actor que inicia el escenario.
2. Cada participante debe enviar o recibir un mínimo de 3 mensajes.
3. Usa flechas simples de PlantUML (-> para llamadas, --> para respuestas). El naming debe ser en camelCase e indicar los argumentos recibidos.
4. Respeta la notación UML para nombrar participantes (Clase, :objeto, o Clase:objeto).
5. Indica la finalización de los objetos temporales que dejan de existir usando el comando `destroy nombreObjeto`.

Devuelve únicamente el código de PlantUML encerrado entre @startuml y @enduml.
```

**Iteraciones e Incidencias Técnicas:**
Durante la generación de este diagrama, la herramienta exigida (GitHub Copilot) presentó reiteradas caídas de servidor y fallos de timeout (`stream_initialization_failed`). Como plan de contingencia técnico para no bloquear la integración de la entrega, se optó por utilizar el modelo Claude IA pasándole los mismos prompts y archivos de contexto.

---

### Diagrama de Secuencia 2: Cancelar Turno - Cancelar turno

**Archivos de contexto referenciados:**
Para la generación de este diagrama se tomaron como contexto explícito los pasos del escenario correspondientes ubicados en `diagramas/03-escenarios-casos-de-uso/` y las responsabilidades de las clases involucradas detalladas en `herramientas-agile/tarjetas-crc/`.

**Prompt utilizado:**
```text
Actúa como un experto en Diseño Orientado a Objetos y UML. Tu tarea es generar el código en PlantUML para el diagrama de secuencia del escenario "Cancelar turno" correspondiente al caso de uso "Cancelar Turno".

Contexto obligatorio: Lee los pasos del escenario en la carpeta `diagramas/03-escenarios-casos-de-uso/` y las responsabilidades de las clases en `herramientas-agile/tarjetas-crc/`.

Genera el código PlantUML cumpliendo ESTRICTAMENTE las reglas de evaluación: al menos 4 participantes (el primero a la izquierda inicia el escenario), mínimo 3 mensajes por participante, flechas simples (-> y -->), naming en camelCase con argumentos, notación UML para participantes, y usa 'destroy' para finalizar objetos temporales. Devuelve únicamente el código PlantUML.
```

**Iteraciones e Incidencias Técnicas:**
Durante la generación de este diagrama, la herramienta exigida (GitHub Copilot) presentó reiteradas caídas de servidor y fallos de timeout (`stream_initialization_failed`). Como plan de contingencia técnico para no bloquear la integración de la entrega, se optó por utilizar el modelo Claude IA pasándole los mismos prompts y archivos de contexto.

---

### Diagrama de Secuencia 3: Registrar Llegada - Registrar llegada del paciente

**Archivos de contexto referenciados:**
Para la generación de este diagrama se tomaron como contexto explícito los pasos del escenario correspondientes ubicados en `diagramas/03-escenarios-casos-de-uso/` y las responsabilidades de las clases involucradas detalladas en `herramientas-agile/tarjetas-crc/`.

**Prompt utilizado:**
```text
Actúa como un experto en Diseño Orientado a Objetos y UML. Tu tarea es generar el código en PlantUML para el diagrama de secuencia del escenario "Registrar llegada del paciente" correspondiente al caso de uso "Registrar Llegada".

Contexto obligatorio: Lee los pasos del escenario en la carpeta `diagramas/03-escenarios-casos-de-uso/` y las responsabilidades de las clases en `herramientas-agile/tarjetas-crc/`.

Genera el código PlantUML cumpliendo ESTRICTAMENTE las reglas de evaluación: al menos 4 participantes (el primero a la izquierda inicia el escenario), mínimo 3 mensajes por participante, flechas simples (-> y -->), naming en camelCase con argumentos, notación UML para participantes, y usa 'destroy' para finalizar objetos temporales. Devuelve únicamente el código PlantUML.
```

**Iteraciones e Incidencias Técnicas:**
Durante la generación de este diagrama, la herramienta exigida (GitHub Copilot) presentó reiteradas caídas de servidor y fallos de timeout (`stream_initialization_failed`). Como plan de contingencia técnico para no bloquear la integración de la entrega, se optó por utilizar el modelo Claude IA pasándole los mismos prompts y archivos de contexto.

---

### Diagrama de Secuencia 4: Registrar Paciente - Registrar paciente

**Archivos de contexto referenciados:**
Para la generación de este diagrama se tomaron como contexto explícito los pasos del escenario correspondientes ubicados en `diagramas/03-escenarios-casos-de-uso/` y las responsabilidades de las clases involucradas detalladas en `herramientas-agile/tarjetas-crc/`.

**Prompt utilizado:**
```text
Actúa como un experto en Diseño Orientado a Objetos y UML. Tu tarea es generar el código en PlantUML para el diagrama de secuencia del escenario "Registrar paciente" correspondiente al caso de uso "Registrar Paciente".

Contexto obligatorio: Lee los pasos del escenario en la carpeta `diagramas/03-escenarios-casos-de-uso/` y las responsabilidades de las clases en `herramientas-agile/tarjetas-crc/`.

Genera el código PlantUML cumpliendo ESTRICTAMENTE las reglas de evaluación: al menos 4 participantes (el primero a la izquierda inicia el escenario), mínimo 3 mensajes por participante, flechas simples (-> y -->), naming en camelCase con argumentos, notación UML para participantes, y usa 'destroy' para finalizar objetos temporales. Devuelve únicamente el código PlantUML.
```

**Iteraciones e Incidencias Técnicas:**
Durante la generación de este diagrama, la herramienta exigida (GitHub Copilot) presentó reiteradas caídas de servidor y fallos de timeout (`stream_initialization_failed`). Como plan de contingencia técnico para no bloquear la integración de la entrega, se optó por utilizar el modelo Claude IA pasándole los mismos prompts y archivos de contexto.

---

### Diagrama de Secuencia 5: Ver Agenda - Ver agenda 

**Archivos de contexto referenciados:**
Para la generación de este diagrama se tomaron como contexto explícito los pasos del escenario correspondientes ubicados en `diagramas/03-escenarios-casos-de-uso/` y las responsabilidades de las clases involucradas detalladas en `herramientas-agile/tarjetas-crc/`.

**Prompt utilizado:**
```text
Actúa como un experto en Diseño Orientado a Objetos y UML. Tu tarea es generar el código en PlantUML para el diagrama de secuencia del escenario "Ver agenda exitoso" correspondiente al caso de uso "Ver Agenda".

Contexto obligatorio: Lee los pasos del escenario en la carpeta `diagramas/03-escenarios-casos-de-uso/` y las responsabilidades de las clases en `herramientas-agile/tarjetas-crc/`.

Genera el código PlantUML cumpliendo ESTRICTAMENTE estas reglas de evaluación:
1. Incluye al menos 4 participantes. El primero (a la extrema izquierda) debe ser el actor principal que inicia el escenario.
2. Cada participante debe enviar o recibir un mínimo de 3 mensajes.
3. Los mensajes deben usar formato camelCase e indicar los argumentos recibidos.
4. Respeta la notación UML para nombrar participantes (Clase, :objeto, o Clase:objeto).
5. Indica la finalización de los objetos temporales que dejan de existir durante el escenario usando el comando `destroy nombreObjeto`.

Devuelve únicamente el código de PlantUML encerrado entre @startuml y @enduml.
```