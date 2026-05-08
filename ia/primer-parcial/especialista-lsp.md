# Documentación de Uso de IA - Especialista LSP

## 🤖 Herramienta Utilizada
**[Cursor - Agent Mode]**

## 💬 Prompt Utilizado

```
Analiza las jerarquías de herencia propuestas para el Sistema de Turnos Médicos y verifica si se cumple el Principio de Sustitución de Liskov (LSP) para la clase Doctor. Propón una jerarquía simple y coherente con el dominio, indicando por qué una subclase puede sustituir a su superclase sin alterar el comportamiento esperado.
```

## 📂 Archivos de contexto referenciados
* `anexos/introduccion.md`
* `diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw`
* `herramientas-agile/tarjetas-crc/04-tarjeta-crc-doctor.md`
* `herramientas-agile/tarjetas-crc/06-tarjeta-crc-agenda.md`
* `herramientas-agile/tarjetas-crc/05-tarjeta-crc-turno.md`

## 📤 Output obtenido (Fragmento representativo)
La IA propuso una jerarquía con `Doctor` como clase abstracta y especialidades concretas (`Cardiologo`, `Pediatra` y `Traumatologo`), acompañada por una explicación sobre contrato de comportamiento, uso polimórfico de `verAgenda(): void` y condiciones para que las especialidades médicas puedan reutilizar la misma interfaz pública sin romper clientes existentes.

## 🛠️ Ajustes realizados
1. **Alineación con el diagrama final:** Se agregó más de un subtipo concreto y se explicitó el contrato esperado de `verAgenda(): void` para que la documentación refleje fielmente la jerarquía propuesta.
2. **Corrección del output obtenido:** Se eliminaron referencias al patrón Strategy, que pertenecen al análisis de OCP, y se reforzó que el contexto utilizado incluye la introducción, el boceto inicial y las tarjetas CRC relevantes.