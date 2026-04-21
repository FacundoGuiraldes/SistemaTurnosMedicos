🛠️ Fix - Correcciones en Diagramas de Casos de Uso, relaciones de dominio y documentación IA

Descripción: Se realizaron ajustes técnicos y semánticos en los diagramas de Casos de Uso para cumplir estrictamente con las reglas del dominio del negocio y las buenas prácticas de UML solicitadas en el feedback del docente. Además, se reestructuraron las rutas de los archivos y se amplió la documentación de la Inteligencia Artificial.

Cambios realizados:
Límites del sistema: Se envolvió el flujo de los 5 diagramas .puml dentro de un bloque rectangle "Sistema de Turnos Médicos" para separar visualmente los procesos internos de los actores externos.
Relaciones obligatorias (Dominio): En 02-caso-uso-solicitar-turno-01.puml y 02-caso-uso-cancelar-turno-02.puml, se cambió la relación de las notificaciones de <<extend>> a <<include>>, ya que son obligatorias por regla de negocio.
Actor Doctor (CU03): En 02-caso-uso-registrar-llegada-03.puml, se reintegró al actor Doctor y se lo vinculó al flujo central mediante un <<extend>> hacia "Ver lista de espera", cumpliendo con la postcondición del requerimiento.
Estructura de archivos: Se movieron los 5 archivos .puml y sus respectivos .png directamente a la raíz de diagramas/02-casos-de-uso/, eliminando las subcarpetas individuales que rompían el formato solicitado.

Documentación IA: Se actualizó ia/a2/modelador-diagramas-casos-uso.md incluyendo el prompt literal en bloque de código, el detalle exhaustivo del output generado por diagrama, los ajustes manuales aplicados y la cantidad de iteraciones.

Changelog: Se actualizaron los registros correspondientes para reflejar estos cambios en la Release N°1.

Archivos modificados:
diagramas/02-casos-de-uso/02-caso-uso-solicitar-turno-01.puml (y .png)
diagramas/02-casos-de-uso/02-caso-uso-cancelar-turno-02.puml (y .png)
diagramas/02-casos-de-uso/02-caso-uso-registrar-llegada-03.puml (y .png)
diagramas/02-casos-de-uso/02-caso-uso-registrar-paciente-04.puml (y .png)
diagramas/02-casos-de-uso/02-caso-uso-ver-agenda-05.puml (y .png)
ia/a2/modelador-diagramas-casos-uso.md

Responsable: @ValeriaMSilva (Modelador de Diagramas de Casos de Uso)