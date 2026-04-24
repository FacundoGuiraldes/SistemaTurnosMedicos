# Documentación de Code Reviews con Copilot Agent Mode

## Rol: Documentador y Coordinador de Repositorio — Primer Examen Parcial

## Contexto General
Para la realización de las code reviews se diseñaron prompts específicos para cada rol del compañero evaluado, indicando explícitamente qué aspectos validar según la consigna del parcial (coherencia con el dominio del sistema de turnos médicos, relación entre markdown y diagrama UML, y correcta documentación del uso de IA).

### Code Review 1 — PR #51 de carolabenvenuto-uces (Especialista DIP)
```text
Actúa como un Senior Software Engineer realizando code review profesional. Estás analizando los cambios de una Pull Request activa. INSTRUCCIONES IMPORTANTES: - lee anexos/introduccion.md para tener el contexto del proyecto. - Identifica problemas reales del código - Enumera los hallazgos (1, 2, 3…) - Cada hallazgo debe ser independiente - Sé claro, técnico y concreto - No inventes problemas hipotéticos sin evidencia en el código - No incluyas sugerencias de tests Para cada hallazgo usa EXACTAMENTE esta estructura: ================================================== 
HALLAZGO #<número> Archivo: Línea: Tipo de problema: (bug | performance | seguridad | legibilidad | diseño | otro) Severidad: (baja | media | alta | crítica) Explicación técnica: Por qué esto es un problema real. Sugerencia de mejora: Cambio concreto recomendado. Ejemplo de código corregido (si aplica):
codigo
ejemplo
DECISIÓN DEL REVISOR HUMANO:

[ ] Aceptar sugerencia
[ ] Rechazar sugerencia

Justificación del revisor humano:
(Completar manualmente si se rechaza)
Al final agrega:

RESUMEN GENERAL DE LA PR
Evaluación global de calidad y riesgos técnicos.

DECISIÓN FINAL SUGERIDA POR IA:

APPROVE / REQUEST CHANGES / COMMENT ONLY

Indicame si:
1. Usa interfaces o clases abstractas
2. Aplica inyección de dependencias
3. No depende de clases concretas
4. Diagrama muestra inversión
```
### Code Review 2 — PR #62 de facundoguiraldes (Especialista LSP)

```text
Actúa como un Senior Software Engineer realizando code review profesional.

Estás analizando los cambios de una Pull Request activa.

INSTRUCCIONES IMPORTANTES:

- Leé los archivos modificados en esta PR (03-lsp.md, diagrama UML y especialista-lsp.md).
- lee anexos/introduccion.md para tener el contexto del proyecto.
- Identifica problemas reales del código
- Enumera los hallazgos (1, 2, 3…)
- Cada hallazgo debe ser independiente
- Sé claro, técnico y concreto
- No inventes problemas hipotéticos sin evidencia en el código
- No incluyas sugerencias de tests

Validá:

1. Que el principio LSP esté correctamente explicado.
2. Que exista una jerarquía de herencia clara.
3. Que las subclases puedan reemplazar a la clase base sin alterar el comportamiento del sistema.
4. Que no se violen contratos (por ejemplo: cambiar comportamiento esperado, lanzar errores inesperados, etc.).
5. Que el ejemplo esté alineado con el sistema de turnos médicos.
6. Que el diagrama UML coincida con lo explicado en el markdown.
7. Que el archivo especialista-lsp.md documente correctamente:
   - prompt
   - archivos usados
   - output
   - ajustes

RESUMEN GENERAL DE LA PR
Evaluación global de calidad y riesgos técnicos.

DECISIÓN FINAL SUGERIDA POR IA:

APPROVE / REQUEST CHANGES 
```
### Code Review 3 — PR #61 de facundoguiraldes (Especialista OCP)

```text
Actúa como un Senior Software Engineer realizando una code review profesional de una Pull Request del parcial de Diseño Orientado a Objetos.

Estás analizando los cambios correspondientes al rol: Especialista en Abierto/Cerrado (OCP).

INSTRUCCIONES IMPORTANTES:

* Lee `anexos/introduccion.md` para entender el contexto del sistema de turnos médicos.
* Revisa los archivos modificados en esta Pull Request (archivo markdown, diagrama UML y archivo de IA).
* Identifica problemas reales con evidencia en los archivos.
* No inventes problemas hipotéticos.
* No incluyas sugerencias de tests.
* Sé claro, técnico y concreto.
* Enumera los hallazgos.

Validá específicamente:

1. Que el principio OCP esté correctamente explicado.
2. Que el diseño permita extender funcionalidades sin modificar clases existentes.
3. Que se utilicen correctamente abstracciones (interfaces, clases abstractas o polimorfismo).
4. Que no haya lógica que obligue a modificar clases cada vez que se agrega un nuevo comportamiento.
5. Que el ejemplo esté alineado con el sistema de turnos médicos.
6. Que el diagrama UML coincida con lo explicado en el markdown.
7. Que el archivo `especialista-ocp.md` documente correctamente:

   * prompt
   * archivos de contexto
   * output obtenido
   * ajustes realizados

Para cada hallazgo usá EXACTAMENTE esta estructura:

==================================================
HALLAZGO #<número>

Archivo:
Línea:

Tipo de problema:
(bug | performance | seguridad | legibilidad | diseño | documentación | otro)

Severidad:
(baja | media | alta | crítica)

Explicación técnica:
Por qué esto es un problema real.

Sugerencia de mejora:
Cambio concreto recomendado.

Comentario sugerido para GitHub:
Texto breve que pueda copiarse como comentario en la Pull Request.

DECISIÓN DEL REVISOR HUMANO:

[ ] Aceptar sugerencia
[ ] Rechazar sugerencia

Justificación del revisor humano:
(Completar manualmente si se rechaza)

No completes la sección "DECISIÓN DEL REVISOR HUMANO".

Al final agregá:

RESUMEN GENERAL DE LA PR

Evaluación global de calidad, coherencia con la consigna y riesgos técnicos.

CHECKLIST OCP

* Permite extender sin modificar código existente:
* Usa abstracciones correctamente:
* Evita condicionales que rompan OCP:
* El diagrama refleja extensibilidad:
* Documenta correctamente el uso de Copilot:

DECISIÓN FINAL SUGERIDA POR IA:

APPROVE / REQUEST CHANGES
```
### Code Review 4 — PR #55 de valeriaMsilva (Especialista ISP)

```text
Actúa como un Senior Software Engineer realizando una code review profesional de una Pull Request del parcial de Diseño Orientado a Objetos.

Estás analizando los cambios correspondientes al rol: Especialista en Segregación de Interfaces (ISP).

INSTRUCCIONES IMPORTANTES:

* Lee `anexos/introduccion.md` para entender el contexto del sistema de turnos médicos.
* Revisa los archivos modificados en esta Pull Request (archivo markdown, diagrama UML y archivo de IA).
* Identifica problemas reales con evidencia en los archivos.
* No inventes problemas hipotéticos.
* No incluyas sugerencias de tests.
* Sé claro, técnico y concreto.
* Enumera los hallazgos.

Validá específicamente:

1. Que el principio ISP esté correctamente explicado.
2. Que no existan interfaces “grandes” con métodos que no todos los clientes utilizan.
3. Que las interfaces estén correctamente segregadas según responsabilidades específicas.
4. Que las clases dependan solo de los métodos que realmente necesitan.
5. Que no haya clases obligadas a implementar métodos que no usan.
6. Que el diseño sea coherente con el sistema de turnos médicos.
7. Que el diagrama UML coincida con lo explicado en el markdown.
8. Que el archivo `especialista-isp.md` documente correctamente:

   * prompt
   * archivos de contexto
   * output obtenido
   * ajustes realizados

Para cada hallazgo usá EXACTAMENTE esta estructura:

==================================================
HALLAZGO #<número>

Archivo:
Línea:

Tipo de problema:
(bug | performance | seguridad | legibilidad | diseño | documentación | otro)

Severidad:
(baja | media | alta | crítica)

Explicación técnica:
Por qué esto es un problema real.

Sugerencia de mejora:
Cambio concreto recomendado.

Comentario sugerido para GitHub:
Texto breve que pueda copiarse como comentario en la Pull Request.

DECISIÓN DEL REVISOR HUMANO:

[ ] Aceptar sugerencia
[ ] Rechazar sugerencia

Justificación del revisor humano:
(Completar manualmente si se rechaza)

No completes la sección "DECISIÓN DEL REVISOR HUMANO".

Al final agregá:

RESUMEN GENERAL DE LA PR

Evaluación global de calidad, coherencia con la consigna y riesgos técnicos.

CHECKLIST ISP

* Interfaces pequeñas y específicas:
* No obliga a implementar métodos innecesarios:
* Clases dependen solo de lo que usan:
* El diagrama refleja segregación de responsabilidades:
* Documenta correctamente el uso de Copilot:

DECISIÓN FINAL SUGERIDA POR IA:

APPROVE / REQUEST CHANGES
```

## Ajustes realizados al output 
A partir del output generado por Copilot, se realizaron ajustes para adaptar el contenido a los requerimientos del parcial.

En particular:

- Se simplificaron las explicaciones técnicas para adecuarlas a un nivel académico claro y comprensible.
- Se eliminaron ejemplos o conceptos que no estaban alineados con el sistema de turnos médicos.
- Se redujo la complejidad de las propuestas de diseño, evitando soluciones innecesariamente elaboradas.
- Se verificó la coherencia entre los archivos markdown, los diagramas UML y la documentación de IA.