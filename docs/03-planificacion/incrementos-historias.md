# RELAJAO — Entregas e historias de usuario del MVP

| Campo | Valor |
|---|---|
| Versión | 0.1 |
| Estado | **Aprobado** — 18-nov-2026; aprobación explícita de la documentación por el responsable del producto |
| Ejecución | Todas las historias pendientes; desarrollo sin iniciar |
| Disponibilidad de referencia | 6 horas semanales: martes, jueves y sábado, 2 horas por sesión |
| Alcance | MVP completo F01–F07; orden documental aprobado, sin modificar el Discovery |

El [SPEC técnico de construcción](../06-construccion/SPEC-TECNICO.md) desarrolla el cómo de estas historias. Sus propuestas DTP siguen pendientes de decisión donde exceden las fuentes aprobadas; aprobar este backlog no las resuelve.

## 1. Secuencia de entregas

Cada incremento agrega una capacidad utilizable sobre los anteriores. Las historias se entregan de extremo a extremo y se demuestran con datos conservados entre sesiones. Acceso, aislamiento de datos y arquitectura aprobada son condiciones de la entrega, no incrementos de infraestructura separados.

| Orden | Incremento | Qué puede hacer el usuario al recibirlo | Historias | Dependencia |
|---|---|---|---|---|
| I01 | Capturar y ejecutar mis pendientes | Acceder a sus datos, crear y editar tareas simples, consultar pendientes, cambiar estados y recuperar eliminadas | HU-01–HU-07 | Ninguna entrega funcional previa |
| I02 | Organizar trabajo y rutinas | Dividir tareas, repetirlas y organizarlas en áreas/proyectos con progreso básico | HU-08–HU-13 | I01 |
| I03 | Construir una agenda realista | Consultar calendario, registrar eventos y reservar tiempo para tareas/subtareas según disponibilidad | HU-14–HU-17 | I01; I02 para subtareas y pruebas de clasificación |
| I04 | Ajustar mi planificación con ayuda | Recibir alternativas, gestionar recurrencias de eventos y reprogramar conservando historia | HU-18–HU-22 | I02, I03 |
| I05 | Decidir qué hacer hoy | Usar el Dashboard para tareas, agenda, proyectos y conflictos, sin duplicar reglas | HU-23–HU-27 | I02, I04; resumen de logros ampliado por I07 |
| I06 | Atender compromisos a tiempo | Ver avisos internos de vencimientos/eventos y administrar su lectura | HU-28–HU-30 | I02, I04; cabecera compartida con I05 |
| I07 | Reconocer avances y mantener constancia | Consultar logros, configurar meta diaria y obtener puntos, insignias y rachas | HU-31–HU-34 | I01, I02, I03, I05 |
| I08 | Validar el MVP en uso cotidiano | Completar un piloto de al menos siete días y evaluar el MVP completo | HU-35 | I01–I07 aceptados |

**Calendario de trabajo:** sesiones de 2 h, martes/jueves/sábado. A partir de la fecha de esta propuesta las siguientes son jueves 19, sábado 21 y martes 24 de noviembre de 2026. Se trabaja primero HU-01–HU-07 en ese orden de dependencia; una historia puede ocupar varias sesiones. No se asigna una entrega a una sesión de dos horas sin estimarla. El antiguo horizonte de nueve semanas es una referencia histórica, no una fecha de entrega reconfirmada.

Las fechas de entrega de I01–I08 quedan pendientes de estimar las historias con la capacidad de 6 h/semana. Este backlog define ya el contenido y el orden de todas las entregas; no presupone una velocidad de desarrollo medida. La prueba de siete días de I08 es tiempo transcurrido adicional al trabajo de preparación y corrección.

**Regla de cierre de cada incremento:** historias aceptadas y demostradas, criterios propios y originales aplicables comprobados, sin defectos que impidan sus flujos o la conservación/aislamiento de datos, y cambios versionados en feature para revisión. La aprobación del backlog no marca las historias como realizadas ni autoriza por sí sola implementación. `main` conserva lo oficial y terminado.

## 2. I01 — Capturar y ejecutar mis pendientes

### HU-01 — Acceder a mi espacio personal

**Como** titular de una cuenta, **quiero** entrar y salir de mi sesión, **para** trabajar con mis datos de forma privada.

**Aceptación:**

- Dada una cuenta habilitada, al usar credenciales válidas accedo a mi espacio; un intento inválido no concede acceso.
- Sin sesión válida no puedo consultar ni modificar tareas. Con dos cuentas A/B, ninguna puede listar, consultar o modificar los datos de la otra, aunque conozca sus identificadores.
- Al cerrar sesión pierdo el acceso a operaciones protegidas; al volver a entrar mis datos siguen disponibles.
- El mecanismo respeta DEC-001. El alta inicial de cuentas y la política detallada de sesión deben acordarse antes de desarrollar esta historia; no se asume registro público aprobado.

**Fuente:** F07 CA-14–15; ARC-002 §8; DEC-001 §2. **Dependencia:** habilitación de cuentas/sesión por especificar.

### HU-02 — Capturar una tarea sin planificarla

**Como** usuario, **quiero** registrar una tarea solo con su título, **para** sacar pendientes de mi cabeza sin organizar todo previamente.

**Aceptación:**

- Al guardar un título válido se crea una sola tarea Pendiente, sin exigir fecha, duración, proyecto, área ni bloque.
- Un título vacío o compuesto solo de espacios se rechaza sin crear tarea.
- La tarea sin planificación aparece en la bandeja. Bandeja es una vista, no un estado adicional.
- Al salir y volver la tarea conserva identidad, título y estado.

**Fuente:** F01 CA-01–03, CA-18; RN-01–02. **Depende de:** HU-01.

### HU-03 — Consultar y ajustar mis tareas

**Como** usuario, **quiero** consultar y editar los datos de mis tareas, **para** aclarar qué debo hacer y su prioridad.

**Aceptación:**

- Puedo abrir una tarea propia y consultar sus datos y estado guardados.
- Puedo editar descripción, prioridad y duración estimada opcionales y volver a consultarlas tras reingresar.
- Puedo asignar una fecha límite sin que eso cree reservas ni cambie el estado. Una tarea puede seguir existiendo sin ella.
- No aparecen campos obligatorios de clasificación ni medición de tiempo real. La interpretación de fecha límite sin hora se decide antes de habilitar esa modalidad.

**Fuente:** F01 CA-04, CA-18; F02 CA24 y D40; F04 D13. **Depende de:** HU-02. **Pendiente aplicable:** PA-03 del modelo.

### HU-04 — Avanzar, pausar y cancelar trabajo

**Como** usuario, **quiero** cambiar el estado de una tarea según mi avance, **para** reflejar lo que realmente estoy haciendo.

**Aceptación:**

- Puedo iniciar Pendiente, pausar En progreso y reanudar Pausada.
- Puedo cancelar desde Pendiente, En progreso o Pausada; una cancelada no se contabiliza como logro.
- Los cinco estados y las transiciones coinciden con F01 §3. Una transición no permitida se rechaza sin alterar datos.
- Los cambios persisten al volver a entrar; cambiar el estado no crea una tarea nueva.

**Fuente:** F01 CA-05, CA-15, CA-18 y diagrama de estados. **Depende de:** HU-03.

### HU-05 — Completar y retomar una tarea

**Como** usuario, **quiero** completar una tarea o retomarla, **para** registrar resultados y corregir su estado cuando lo necesite.

**Aceptación:**

- Puedo completar directamente desde cualquiera de los tres estados activos, sin pasar por estados intermedios.
- Completar registra fecha y hora y presenta retroalimentación visual; no se introduce un mensaje motivacional automático excluido por E12.
- Puedo reabrir Completada o reactivar Cancelada a Pendiente conservando la identidad.
- Un reintento no duplica la tarea. La corrección de finalización al reabrir se acuerda antes de implementar; los conteos y recompensas de I07 deben reutilizar esa identidad sin duplicar logros.

**Fuente:** F01 CA-06, CA-13–15; F06 CA-15. **Depende de:** HU-04. **Pendiente:** PA-04, parte de historia de finalización.

### HU-06 — Recuperar una tarea eliminada

**Como** usuario, **quiero** enviar tareas a una papelera y recuperarlas, **para** corregir eliminaciones sin perder información.

**Aceptación:**

- Al eliminar una tarea se realiza eliminación lógica; papelera no sustituye su estado de ejecución.
- Al restaurar recupero sus datos y relaciones conservadas; eliminar no equivale a cancelar.
- No se ofrece eliminación definitiva como flujo habitual del MVP.
- Los escenarios con subtareas, recurrencias, proyectos y bloques se verifican al incorporar I02–I04; no se declara esa integración probada en I01.

**Fuente:** F01 CA-16–18, RN-07. **Depende de:** HU-02.

### HU-07 — Consultar mi perfil y conservar preferencias

**Como** usuario, **quiero** gestionar mi nombre visible y consultar mi cuenta desde Configuración, **para** mantener mis datos personales básicos.

**Aceptación:**

- Configuración es accesible desde la navegación principal y muestra el nombre y datos básicos de la cuenta.
- Puedo guardar explícitamente un nombre visible válido; no vacío ni solo espacios.
- Tras cerrar y volver a entrar se conserva el nombre. Cerrar sesión no modifica tareas ni otros datos existentes.
- No se muestran opciones de apariencia, avisos personalizados, exportación ni restablecimiento global excluidas del MVP. Disponibilidad, zona horaria y meta se incorporan con sus historias posteriores.

**Fuente:** F07 CA-01–04, CA-13–17. **Depende de:** HU-01.

**Demostración I01:** entrar → capturar → editar → iniciar/pausar/completar → reabrir → eliminar/restaurar → salir y volver con datos conservados.

## 3. I02 — Organizar trabajo y rutinas

### HU-08 — Dividir una tarea en subtareas

**Como** usuario, **quiero** dividir una tarea en pasos simples, **para** ejecutar trabajo grande sin crear jerarquías complicadas.

**Aceptación:**

- Puedo crear, editar, completar y eliminar subtareas de un solo nivel, con título y estado pendiente/completada.
- Al completar la principal se completan automáticamente las subtareas pendientes.
- Completar todas las subtareas no completa automáticamente la principal.
- Se conserva el vínculo al guardar y reingresar. Reapertura y trazabilidad automática/manual requieren resolver PA-02 antes de sus operaciones afectadas.

**Fuente:** F01 CA-07–08, CA-18; RN-04. **Depende de:** HU-05.

### HU-09 — Repetir tareas habituales

**Como** usuario, **quiero** crear tareas diarias, semanales o mensuales, **para** gestionar rutinas sin capturarlas cada vez.

**Aceptación:**

- Puedo definir repetición diaria, semanal o mensual y consultar sus ocurrencias.
- Completar una ocurrencia conserva los estados de las restantes; cada una mantiene su cumplimiento.
- Editar una ocurrencia no modifica otras; editar las futuras preserva la historia anterior.
- Al volver a entrar se conservan recurrencia, ocurrencias y estados; la generación no duplica ocurrencias. Se resuelven días 29–31 y edición/materialización antes de desarrollar los casos afectados.

**Fuente:** F01 CA-09–12, CA-18; RN-05. **Depende de:** HU-05. **Pendientes:** PA-01/06.

### HU-10 — Clasificar responsabilidades por áreas

**Como** usuario, **quiero** organizar mis tareas por áreas de vida, **para** distinguir mis responsabilidades sin clasificar todo obligatoriamente.

**Aceptación:**

- Existen cinco áreas iniciales: Trabajo, Salud, Finanzas, Desarrollo personal y Vida personal; puedo editar nombre y color.
- No puedo crear, archivar ni eliminar áreas en el MVP.
- Una tarea puede tener área directa sin proyecto o ninguna clasificación; no se exige área al capturar.
- Puedo navegar y filtrar por área; los cambios persisten.

**Fuente:** F03 CA1–3, CA18/20 (numeración v1.0). **Depende de:** HU-03.

### HU-11 — Agrupar trabajo en proyectos

**Como** usuario, **quiero** agrupar tareas en proyectos de un área, **para** dar seguimiento a un objetivo concreto.

**Aceptación:**

- Puedo crear y editar proyecto con nombre y área obligatorios y descripción opcional; su identidad no cambia al renombrarlo.
- Las tareas del proyecto heredan su área; cambiarla actualiza la clasificación sin alterar estados ni reservas existentes.
- Puedo mover tareas entre proyectos, área directa o sin clasificación conservando datos, subtareas, fechas y recurrencias; en I03–I04 se comprueba también la conservación de bloques.
- Eliminar el proyecto conserva sus tareas asociadas al área anterior. Lista jerárquica y filtros permiten encontrarlas.

**Fuente:** F03 CA4–10, CA18–20; RN-F03-63. **Depende de:** HU-08–10.

### HU-12 — Distinguir proyectos prioritarios y favoritos

**Como** usuario, **quiero** marcar favoritos y asignar prioridad a proyectos, **para** encontrar antes los que me importan.

**Aceptación:**

- Un proyecto nuevo inicia con prioridad Media y sin favorito; puedo modificar ambas propiedades de forma independiente.
- Los favoritos se muestran aparte; cada grupo se ordena Alta → Media → Baja y luego alfabéticamente, sin duplicados.
- Cambiar prioridad/favorito no altera prioridades, estados, fechas, progreso o bloques de sus tareas.
- Los valores persisten y quedan disponibles para el Dashboard de I05.

**Fuente:** F03 CA-F03-21–26; RN-F03-64–70. **Depende de:** HU-11.

### HU-13 — Conocer el avance de un proyecto

**Como** usuario, **quiero** ver progreso y tiempo estimado de mis proyectos, **para** conocer qué he terminado y qué queda pendiente.

**Aceptación:**

- Progreso = principales completadas elegibles / principales elegibles; sin elegibles muestra 0 %, sin declarar el proyecto terminado.
- Se excluyen subtareas, canceladas, eliminadas lógicamente y tareas recurrentes (serie y ocurrencias); las recurrentes permanecen visibles.
- Total suma estimaciones elegibles y pendiente suma las de estados activos; sin estimación aporta cero. No descuenta minutos trabajados.
- Completar, cancelar, mover, eliminar o restaurar recalcula los indicadores y los cambios se conservan entre sesiones.

**Fuente:** F03 CA11–17, CA19–20; P01/P02. **Depende de:** HU-06, HU-09, HU-11.

**Demostración I02:** organizar una rutina y una tarea con pasos en un proyecto, cambiar su área y comprobar el progreso sin contar recurrencias ni subtareas por separado.

## 4. I03 — Construir una agenda realista

### HU-14 — Interpretar mis horarios en mi zona horaria

**Como** usuario, **quiero** consultar y cambiar mi zona horaria, **para** interpretar correctamente mis compromisos.

**Aceptación:**

- Configuración muestra la zona vigente y permite guardar otra.
- Crear, guardar y visualizar horarios respeta la zona configurada.
- Cambiar la zona no cambia automáticamente los estados de tareas o eventos.
- La preferencia se conserva al volver a entrar; los efectos sobre historia de logros se resuelven antes de I07 (PA-05).

**Fuente:** F02 CA25; F07 CA-05–07, CA-16. **Depende de:** HU-07.

### HU-15 — Consultar y gestionar compromisos en calendario

**Como** usuario, **quiero** ver y editar compromisos en calendario, **para** conocer mi agenda diaria, semanal y mensual.

**Aceptación:**

- Puedo alternar vistas diaria, semanal y mensual con los mismos datos en sus fechas correctas.
- Puedo crear, editar y eliminar eventos independientes con inicio anterior al fin; un intervalo inválido se rechaza.
- F02 funciona con eventos locales y tareas sin área; no exige integraciones externas.
- Los eventos y sus cambios permanecen al volver a ingresar y se muestran en la zona configurada.

**Fuente:** F02 CA01–02, CA08, CA25; S07. **Depende de:** HU-14.

### HU-16 — Reservar tiempo para tareas y pasos

**Como** usuario, **quiero** asignar bloques a tareas o subtareas, **para** decidir cuándo dedicarles tiempo.

**Aceptación:**

- Una tarea/subtarea puede tener cero, uno o varios bloques; cada bloque referencia un destino concreto sin crear otra tarea.
- Puedo crear, mover y eliminar bloques futuros sin cambiar estados de tareas/subtareas ni borrar reservas pasadas.
- Los bloques no tienen recurrencia propia; su duración es tiempo reservado, no trabajado.
- La fecha límite permanece independiente; vencer advierte sin cambiar estado y permite reprogramar. Clasificar/mover la tarea no pierde reservas. Antes de implementar intervalos de bloque se resuelve PA-07.

**Fuente:** F02 CA03–04, CA07, CA24, CA26–27; F03 CA9–10. **Depende de:** HU-08, HU-11, HU-15.

### HU-17 — Definir disponibilidad y conocer superposiciones

**Como** usuario, **quiero** configurar horarios habituales y excepciones y recibir advertencias de conflicto, **para** planificar con mi disponibilidad real.

**Aceptación:**

- Puedo consultar y editar disponibilidad semanal y excepciones por fecha desde Configuración con las validaciones de F02.
- Una superposición se advierte y puedo confirmar manualmente la reserva.
- Las vistas mantienen los horarios y excepciones guardados al volver a entrar.
- La precedencia de excepciones y límites de validación se concretan antes de los casos afectados, sin introducir una prohibición general de guardar conflictos (PA-08).

**Fuente:** F02 CA05–06; F07 CA-08–09, CA-16. **Depende de:** HU-15–16.

**Demostración I03:** configurar disponibilidad, crear evento, reservar dos bloques para una tarea y uno para su subtarea; guardar un conflicto advertido y comprobar que no cambia la ejecución.

## 5. I04 — Ajustar mi planificación con ayuda

### HU-18 — Detectar sobrecarga y respetar descansos

**Como** usuario, **quiero** saber si planifiqué más de mi disponibilidad y configurar descansos, **para** evitar una agenda poco realista.

**Aceptación:**

- Una planificación superior a la disponibilidad muestra advertencia, pero permite guardar manualmente.
- Puedo configurar descansos y márgenes desde los ajustes de disponibilidad; las sugerencias los respetan.
- No se exige registrar sesiones ejecutadas ni minutos reales para evaluar planificación.

**Fuente:** F02 CA09–10; F07 CA-08–09. **Depende de:** HU-17.

### HU-19 — Elegir una sugerencia de horario

**Como** usuario, **quiero** recibir alternativas individuales de horario, **para** planificar o redistribuir trabajo conservando el control.

**Aceptación:**

- Una sugerencia considera disponibilidad, prioridad, fecha límite y área si existe; funciona sin área/proyecto.
- Antes de confirmar no crea ni mueve reservas; rechazar no cambia planificación.
- No mueve compromisos fijos salvo modificación explícita del usuario.
- Doble clic o reintento de confirmación no duplica la reserva; puedo crear intencionalmente otra sesión.

**Fuente:** F02 CA11–13, CA18. **Depende de:** HU-18; PA-08 antes de concretar algoritmo y desempates.

### HU-20 — Gestionar compromisos y horarios habituales recurrentes

**Como** usuario, **quiero** repetir eventos y aprovechar horarios habituales de mis tareas, **para** planificar mis rutinas sin perder excepciones.

**Aceptación:**

- Creo eventos diarios, semanales o mensuales y edito una ocurrencia o esta y las futuras preservando excepciones e historia pasada.
- Al eliminar puedo elegir esta ocurrencia o toda la serie; retirar la serie del calendario activo conserva historia mínima pasada.
- Puedo vincular un bloque a una ocurrencia concreta de tarea sin duplicarla ni dar recurrencia al bloque.
- El horario habitual de una tarea recurrente es opcional; aceptar la sugerencia crea el bloque, rechazar no cambia nada.

**Fuente:** F02 CA14–17, CA26–27; OBS-F02-01. **Depende de:** HU-09, HU-19; PA-01/06.

### HU-21 — Reprogramar sin perder reservas pasadas

**Como** usuario, **quiero** consultar reservas pasadas y reorganizar pendientes, **para** ajustar mi agenda sin fingir que trabajé en ellas.

**Aceptación:**

- Un bloque pasado se conserva como reserva, sin marcarlo realizado o incumplido.
- Reprogramar una tarea pendiente conserva el bloque pasado y crea una reserva futura de la misma tarea.
- Completar o cancelar sugiere liberar bloques futuros de tarea y subtareas: aceptar elimina los seleccionados y rechazar conserva todos.
- Editar/eliminar planificación futura no borra historia ni modifica automáticamente estados.

**Fuente:** F02 CA19–21, CA27. **Depende de:** HU-19–20.

### HU-22 — Recuperar planificación de tareas eliminadas

**Como** usuario, **quiero** recuperar las reservas de una tarea restaurada, **para** continuar su planificación sin rehacerla.

**Aceptación:**

- Eliminar lógicamente una tarea oculta sus bloques del calendario activo y dejan de consumir disponibilidad.
- Restaurar recupera las reservas vinculadas y advierte conflictos sin mover reservas ajenas.
- Se conservan datos y relaciones de la tarea y se recalculan indicadores de proyecto según su elegibilidad.

**Fuente:** F02 CA22–23; F01 CA17; F03 P01. **Depende de:** HU-06, HU-13, HU-21.

**Demostración I04:** detectar sobrecarga, aceptar una alternativa, reprogramar manteniendo historia y restaurar una tarea con reservas que presentan conflicto.

## 6. I05 — Decidir qué hacer hoy

### HU-23 — Ver y ejecutar las tareas del día

**Como** usuario, **quiero** ver en el Dashboard las tareas relevantes de hoy, **para** decidir qué hacer y actuar desde el mismo lugar.

**Aceptación:**

- Al abrir se consultan datos actuales. Tareas con bloques hoy o vencimiento hoy aparecen sin duplicados.
- Orden: bloques actuales y próximos (ventana de 120 min), luego posteriores y vencimiento de hoy sin bloque.
- Puedo abrir, iniciar, pausar y completar con las transiciones válidas de F01.
- Completadas hoy aparecen en sección secundaria contraída. Vencidas van aparte, inicialmente cinco de mayor atraso, con total y acceso a todas.

**Fuente:** F04 CA-01–06; D10/D23. **Depende de:** I04.

### HU-24 — Capturar y planificar desde el Dashboard

**Como** usuario, **quiero** capturar pendientes y usar espacios libres desde mi agenda del día, **para** organizarme sin cambiar de sección.

**Aceptación:**

- Captura rápida exige solo título; prioridad, fecha límite y área son opcionales.
- Agenda diferencia eventos/compromisos fijos de bloques y muestra espacios disponibles según F02.
- Seleccionar un espacio permite planificación manual con validación y confirmación.
- Puedo solicitar a F02 sugerencias de planificación y reprogramación sin crear otro motor.

**Fuente:** F04 CA-07–11; D13–16. **Depende de:** HU-23.

### HU-25 — Consultar avance y proyectos importantes

**Como** usuario, **quiero** ver logros del día/semana y proyectos importantes, **para** mantener una visión breve de mis avances.

**Aceptación:**

- Los conteos diarios/semanales usan estados y fechas de F01; progreso de proyectos usa exactamente F03.
- Favoritos permanecen anclados aunque no tengan trabajo pendiente; puedo marcar/desmarcar desde Dashboard.
- Los no favoritos aparecen cuando tienen tareas principales elegibles pendientes; no se duplican entre grupos y se respeta prioridad/alfabético.
- Las métricas de metas/rachas/puntos se integran en I07 sin duplicar el progreso de proyectos; no se declara F06 entregado en I05.

**Fuente:** F04 CA-12–15, RN-F04-42–49. **Depende de:** HU-12–13, HU-23; PA-04/05 antes de cálculos afectados.

### HU-26 — Entender conflictos desde mi vista del día

**Como** usuario, **quiero** consultar causas y alternativas de conflictos, **para** decidir cómo corregir mi agenda.

**Aceptación:**

- Panel preventivo muestra alertas contextuales obtenidas de F02 y permite expandir elementos involucrados/causas.
- Puedo solicitar alternativas a F02, sin modificar planificación hasta confirmar.
- Puede mostrar conflictos de la semana actual, sin proyecciones, porcentajes agregados de ocupación ni otro algoritmo de recomendaciones.

**Fuente:** F04 CA-16–18; D25/P01. **Depende de:** HU-19, HU-23.

### HU-27 — Usar el Dashboard sin confusiones de carga o guardado

**Como** usuario, **quiero** que la vista se adapte a mi dispositivo y refleje operaciones confirmadas, **para** confiar en lo que veo.

**Aceptación:**

- Datos vacíos muestran mensajes sencillos y carga inicial muestra un indicador.
- Un fallo de consulta ofrece reintento; una operación fallida no se muestra como guardada o completada.
- Una acción confirmada refresca los componentes afectados.
- Layout fijo adaptable a escritorio, tableta y móvil; sin reorganización personalizable de componentes.

**Fuente:** F04 CA-19–22; P02. **Depende de:** HU-23–26.

**Demostración I05:** revisar el día, capturar, completar y planificar desde Dashboard, consultar proyectos y resolver una advertencia con los datos actualizados.

## 7. I06 — Atender compromisos a tiempo

### HU-28 — Recibir avisos relevantes dentro de la aplicación

**Como** usuario, **quiero** ver avisos de vencimientos y eventos próximos, **para** atender lo importante al entrar a RELAJAO.

**Aceptación:**

- Tareas con fecha límite avisan dentro de las 24 h previas; vencidas no completadas ni canceladas mantienen aviso activo.
- Eventos avisan dentro de los 30 min previos; cada ocurrencia se evalúa independientemente.
- Tareas sin fecha límite no generan aviso aunque tengan bloques. No hay avisos por bloques ni canales externos.
- Los avisos aparecen en la aplicación; tras varios días ausente solo se muestran vigentes, sin reconstruir historia ni duplicar ocurrencia/condición.

**Fuente:** F05 CA-01–06, CA-18; D12/D15. **Depende de:** I04; PA-03.

### HU-29 — Consultar y marcar avisos leídos

**Como** usuario, **quiero** consultar y marcar mis avisos, **para** distinguir lo que ya revisé sin perder la advertencia vigente.

**Aceptación:**

- Campana global en cabecera con contador de activos sin leer; no se duplica el centro en Dashboard.
- Orden: vencidas → eventos próximos → tareas próximas, por fecha/hora dentro del grupo. Se ven diez inicialmente y puedo abrir todos.
- Abrir el elemento desde aviso lo marca leído; también puedo marcar uno o todos los activos, no solo los diez visibles.
- Leer no cambia ni elimina el origen o su condición; los contadores reflejan el cambio.

**Fuente:** F05 CA-07–14; D05/D08–11. **Depende de:** HU-28.

### HU-30 — Mantener avisos vigentes sin acumularlos

**Como** usuario, **quiero** que los avisos obsoletos se retiren, **para** confiar en los pendientes que todavía requieren atención.

**Aceptación:**

- Completar/cancelar tarea, finalizar evento o dejar de cumplirse la condición retira avisos irrelevantes.
- Cambiar fecha límite retira el anterior y genera otro sin leer cuando corresponda.
- Al pasar a vencida, el aviso de proximidad se sustituye por uno nuevo de vencimiento sin leer.
- Ediciones/eliminaciones de ocurrencias respetan independencia y no crean duplicados al volver a entrar.

**Fuente:** F05 CA-15–18; D04/D06–07/D13–15. **Depende de:** HU-29.

**Demostración I06:** mostrar un aviso próximo, leerlo, modificar el vencimiento y completar el origen comprobando sustitución/limpieza y contador.

## 8. I07 — Reconocer avances y mantener constancia

### HU-31 — Consultar mis logros por día

**Como** usuario, **quiero** ver tareas completadas hoy y durante los últimos siete días, **para** reconocer mi avance real.

**Aceptación:**

- Cuenta principales completadas; excluye subtareas y canceladas. Cada ocurrencia recurrente completada cuenta una sola vez.
- El día se determina por fecha local de finalización y zona horaria configurada.
- El historial incluye siete días, incluidos ceros; al cambiar una finalización se ajustan conteos sin duplicarlos.
- Los indicadores se presentan compactos en Dashboard, sin duplicar el progreso de proyectos.

**Fuente:** F06 CA-01–03, CA-13–16. **Depende de:** HU-09, HU-14, HU-25; PA-04/05.

### HU-32 — Elegir una meta diaria opcional

**Como** usuario, **quiero** establecer, modificar o desactivar una meta de tareas diarias, **para** orientar mi esfuerzo sin imponerme un objetivo obligatorio.

**Aceptación:**

- Configuración muestra la meta vigente y permite modificarla o desactivarla con reglas de F06, sin crear otro sistema de metas.
- Con meta, progreso = completadas del día/meta, indicador visual hasta 100 %; alcanzar o superar registra el día cumplido.
- Sin meta se muestran logros sin porcentaje ni rachas nuevas.
- La preferencia persiste al salir/volver; la validez del valor y el efecto temporal de cambiar meta se concretan antes de los escenarios afectados (PA-05).

**Fuente:** F06 CA-04–07; F07 CA-10–12, CA-16. **Depende de:** HU-31.

### HU-33 — Reconocer mi constancia sin castigos

**Como** usuario, **quiero** ver mi racha de metas cumplidas, **para** reconocer la constancia sin ser penalizado por descansar.

**Aceptación:**

- La racha aumenta con días consecutivos de meta cumplida.
- Un día sin cumplimiento interrumpe continuidad, sin restar puntos o insignias por inactividad.
- Sin meta no se generan rachas nuevas; los efectos retroactivos de cambios de meta/zona se resuelven según PA-05.
- No hay comparaciones entre usuarios, puntuaciones negativas ni mensajes motivacionales automáticos.

**Fuente:** F06 CA-08–09, CA-12, CA-17. **Depende de:** HU-32.

### HU-34 — Recibir puntos e insignias por logros

**Como** usuario, **quiero** recibir reconocimientos sencillos por completar trabajo, **para** hacer visibles mis logros.

**Aceptación:**

- Cada principal completada otorga 10 puntos una sola vez; consultar, reintentar o recompletar no duplica recompensas.
- Tres insignias iniciales: primera tarea completada, primera meta diaria alcanzada y racha de tres días.
- Interrumpir racha conserva puntos/insignias; no se introducen niveles, rankings ni tienda.
- Reabrir/corregir finalizaciones ajusta conteos sin duplicaciones; reversión de recompensas y efectos de eliminar/restaurar se deciden explícitamente según PA-04 antes de implementar esos casos.

**Fuente:** F06 CA-10–12, CA-15, CA-17; RN-F06-10–15. **Depende de:** HU-31–33.

**Demostración I07:** completar principal y ocurrencia, comprobar conteos y puntos, cumplir meta y observar historia/racha sin duplicar logros al reabrir.

## 9. I08 — Validar el MVP en uso cotidiano

### HU-35 — Probar el sistema con responsabilidades reales

**Como** usuario piloto, **quiero** utilizar RELAJAO durante al menos siete días, **para** comprobar que puedo organizar y ejecutar mis compromisos sin depender de herramientas externas.

**Aceptación:**

- Están disponibles y aceptadas las historias de I01–I07 y todos los CA originales de F01–F07, incluyendo integraciones verificadas al incorporar nuevas capacidades.
- Usuarios piloto realizan captura, organización, planificación, Dashboard, avisos y motivación con datos conservados entre sesiones; se registran problemas y comentarios durante al menos siete días.
- Se evalúan S01–S10 con evidencia; sin defectos críticos abiertos. Una incidencia se registra con pasos y resultado esperado/obtenido, sin declarar aprobado un criterio que falla.
- El responsable del producto revisa resultados para declarar MVP validado o identificar correcciones necesarias. Siete días por sí solos no prueban el éxito.

**Fuente:** Discovery S01–S10, definición de MVP validado. **Depende de:** I01–I07 aceptados; acceso y entorno del piloto acordados.

## 10. Cobertura de los criterios aprobados

Las fuentes son la referencia de aceptación completa: los criterios de cada historia los concretan y agrupan, no los reemplazan ni reducen. Un CA transversal se verifica al entregar su capacidad y se vuelve a comprobar al integrar dependencias posteriores. En F03, CA1–20 refiere a la lista v1.0, CA21–26 a la ampliación v1.1.

| Fuente | Criterios originales → historia | Entrega completa |
|---|---|---|
| [F01](../02-requisitos/F01-tareas.md) | CA01–03 → HU-02; CA04 → HU-03; CA05/15 → HU-04; CA06/13/14 → HU-05; CA07–08 → HU-08; CA09–12 → HU-09; CA16–17 → HU-06; CA18 → HU-02–09 y regresión de datos en cada incremento | I02 para F01; integración con planificación en I03–I04 y motivación en I07 |
| [F02](../02-requisitos/F02-calendario.md) | CA01–02/08 → HU-15; CA03–04/07/24/26–27 → HU-16; CA05–06 → HU-17; CA09–10 → HU-18; CA11–13/18 → HU-19; CA14–17/26–27 → HU-20; CA19–21/27 → HU-21; CA22–23 → HU-22; CA25 → HU-14–15 | P0 en I03; P1 y regresión completa en I04 |
| [F03](../02-requisitos/F03-areas-proyectos.md) | CA1–3 → HU-10; CA4–10 → HU-11; CA11–17 → HU-13; CA18 → HU-10–11; CA19 → HU-09/13; CA20 → HU-10–13 y regresión; CA21–26 → HU-12 | I02; conservación de reservas se vuelve a comprobar en I03–I04 |
| [F04](../02-requisitos/F04-dashboard.md) | CA01–06 → HU-23; CA07–11 → HU-24; CA12–15 → HU-25; CA16–18 → HU-26; CA19–22 → HU-27 | I05; integración compacta de F06 en I07 |
| [F05](../02-requisitos/F05-notificaciones.md) | CA01–06 → HU-28; CA07–14 → HU-29; CA15–18 → HU-30 (CA18 también HU-28) | I06 |
| [F06](../02-requisitos/F06-progreso-motivacion.md) | CA01–03/13–16 → HU-31; CA04–07 → HU-32; CA08–09/12/17 → HU-33; CA10–12/15/17 → HU-34 | I07 |
| [F07](../02-requisitos/F07-configuracion.md) | CA01–04/13/17 → HU-07; CA05–07 → HU-14; CA08–09 → HU-17/18; CA10–12 → HU-32; CA14–15 → HU-01/07; CA16 → HU-07/14/17/32 | I07 por incorporación gradual de preferencias |
| [Discovery](../01-discovery/discovery-v1.0.md) | S01 tareas → I01–I04; S02 planificación → I03–I04; S03 día → I05; S04 organización → I02; S05 avisos → I06; S06 motivación → I07; S07 persistencia/S08 sencillez → todos; S09 piloto/S10 aceptación completa → HU-35 | I08 valida el conjunto |

## 11. Pendientes que condicionan historias

Se conservan las preguntas abiertas del [modelo aprobado](../04-arquitectura/domain-model.md#7-análisis-adicional-y-decisiones-abiertas). Identificar una pregunta no autoriza una respuesta ni bloquea historias no afectadas.

| Pregunta | Antes de desarrollar |
|---|---|
| Acceso inicial, alta de cuenta y detalle de sesión (PA-09) | HU-01; respetar mecanismos aprobados de DEC-001 sin asumir registro público |
| Fechas límite sin hora (PA-03) | Modalidad afectada de HU-03; HU-16/23/28 requieren interpretación consistente |
| Historia de finalización y corrección de recompensas (PA-04) | Parte de historia de HU-05; conteos HU-25/31 y recompensas HU-34 |
| Reapertura y finalización automática de subtareas (PA-02) | Operaciones afectadas de HU-08 |
| Días 29–31 y edición/generación de series (PA-01/06) | HU-09 y HU-20 |
| Intervalos de bloque y disponibilidad/sugerencias (PA-07/08) | HU-16–19 |
| Retroactividad de meta/zona y validaciones de meta (PA-05) | Cálculos afectados de HU-25/31–34; cambio de zona HU-14 preserva información necesaria |
| Entorno y acceso del piloto | Antes de exponer una entrega a usuarios piloto y de iniciar HU-35; no se selecciona hosting nuevo en este backlog |

Estimaciones y fechas de cada incremento se registrarán aquí después de revisar las historias; no se crearán planes paralelos para la misma entrega. Los habilitadores técnicos (base ejecutable, persistencia, contratos, controles de acceso, pruebas y despliegue) forman parte del trabajo necesario para aceptar las historias, sin cambiar el stack aprobado ni sustituirlas por tareas técnicas presentadas como valor al usuario.
