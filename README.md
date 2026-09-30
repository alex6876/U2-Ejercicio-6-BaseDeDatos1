# Ejercicio — Base de Datos de Gestión de Proyectos, Tareas y Recursos

Proyecto enfocado en la modelación Entidad-Relación (DER / MER) e implementación de base de datos relacional para un sistema de gestión integral de proyectos, administrando fases, tareas, asignaciones de empleados y asignación de recursos materiales.

---

## Descripción

El sistema modela una estructura de datos relacional para la planificación, ejecución y control de proyectos organizacionales. Permite definir proyectos con presupuesto y objetivos, desglosarlos en fases y tareas específicas con estimaciones de tiempo, asignar personal/empleados registrando horas trabajadas y roles, y administrar la asignación de recursos materiales del inventario de la empresa.

---

## Funcionalidades e Implementación

### Entidades y Atributos

* Proyecto:


* id_Proyecto: Clave primaria identificadora del proyecto.


* Nombre comercial: Nombre o título del proyecto.


* Descripción de objetivo: Metas u objetivos a alcanzar con el proyecto.


* Fecha de inicio: Fecha programada de inicio.


* Fecha de finalización: Fecha estimada o real de cierre del proyecto.


* Presupuesto asignado: Monto económico destinado al proyecto.




* Fase:


* id_Fase: Clave primaria identificadora de la fase.


* Nombre: Denominación de la etapa del proyecto (ej. Análisis, Desarrollo, Pruebas).


* Descripción: Detalle sobre el alcance de la fase.


* Estimación de hora: Horas estimadas requeridas para completar la fase.


* Estado: Situación actual de la fase (ej. pendiente, en progreso, completada).




* Tarea:


* id_Tarea: Clave primaria identificadora de la tarea.


* descripción_T: Descripción conceptual del trabajo a realizar.


* Horas estimadas: Estimación de tiempo para la ejecución de la tarea.


* Prioridad: Nivel de importancia (ej. alta, media, baja).


* Estado_T: Estado de avance de la tarea.




* Empleado:


* legajo(PK): Clave primaria única del empleado.


* Nombre: Nombre del empleado.


* DNI: Documento Nacional de Identidad.


* Categoria laboral: Nivel o puesto de la contratación (ej. Senior, Semi-Senior, Junior).


* Perfil técnico: Habilidades o especialidad del empleado.




* Asignación_Tarea:


* legajo(PK): Clave foránea referenciando al empleado asignado.


* id_Tarea: Clave foránea referenciando a la tarea asignada.


* Hora trabajadas: Registro de horas efectivamente insumidas en la tarea.


* Rol en tareas: Función que desempeña en la tarea (ej. responsable, revisor, desarrollador).


* Estado Asiganación: Estado de la asignación (ej. activa, pausada, finalizada).




* Recurso Material:


* id_Nr_Inventario: Clave primaria identificadora del recurso de inventario.


* marca: Marca del equipo o material.


* tipo recurso: Categoría del recurso (ej. hardware, insumo, herramienta).


* Estado_R: Estado físico o funcional del recurso.


* descripción_R: Descripción técnica del bien de inventario.


* Numero de serie: Número de serie único de fábrica.




* Asignación_Recurso:


* id_Proyecto: Clave foránea referenciando al proyecto de destino.


* id_Nr_Inventario: Clave foránea referenciando al recurso asignado.


* Fecha asignación: Fecha en que se asignó el recurso al proyecto.


* Fecha devolución: Fecha programada o real de devolución del recurso.


* observaciones: Comentarios o notas sobre el uso o condición del recurso.





---

## Relaciones del Modelo

1. Proyecto ↔ Fase (Relación 1:N):


* Un proyecto se divide en múltiples fases secuenciales o paralelas, pero cada fase pertenece a un único proyecto.




2. Fase ↔ Tarea (Relación 1:N):


* Una fase agrupa múltiples tareas operativas a ejecutar, mientras que cada tarea forma parte de una fase determinada.




3. Tarea ↔ Empleado (Relación N:M):


* Varias tareas pueden ser asignadas a múltiples empleados, y un empleado puede participar en múltiples tareas. Se resuelve mediante la entidad intermedia `Asignación_Tarea`.




4. Empleado ↔ Asignación_Tarea (Relación 1:N):


* Un empleado tiene asignaciones de tareas registradas.




5. Tarea ↔ Asignación_Tarea (Relación 1:N):


* Una tarea cuenta con registros de asignación a uno o más empleados.




6. Proyecto ↔ Recurso Material (Relación N:M):


* Un proyecto requiere múltiples recursos materiales para su desarrollo, y un recurso puede reasignarse a diferentes proyectos a lo largo del tiempo. Se resuelve a través de la entidad intermedia `Asignación_Recurso`.




7. Proyecto ↔ Asignación_Recurso (Relación 1:N):


* Un proyecto dispone de registros de asignación de recursos.




8. Recurso Material ↔ Asignación_Recurso (Relación N:1):


* Un recurso de inventario participa en uno o más registros de asignación.
