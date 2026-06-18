# ⚒️ Apartado 1
### Sección Individual
- Qué tipo de rol le gustaría desempeñar dentro de un equipo de software.

- Qué fortalezas personales cree que ya tiene hoy para aportar a un equipo.

- Qué aspectos considera que debe fortalecer o mejorar para ser un buen integrante de equipo.

## 📝 Juan Diego Cardozo Pedraza
- Me gustaría hacer pruebas y calidad, para garantizar que se haga un trabajo que se pueda mantener durante el tiempo, que sea robusto y que funcione.

- Soy una persona que me gusta aprender, y cuando me interesa un tema, hago el esfuerzo por hacerlo bien y entender. También soy una persona bastante calmada y tranquila, que siento que puede ayudar a que las cosas no se escalen mucho.

- Considero que es importante tener un mejor manejo de la comunicación, quedar al tanto de toda la información, además creo que siempre hay más por aprender y siento que podría reforzar programación y tecnicas en general.

## 🛸 Samuel Eduardo Fajardo Quintero
- Podría asumir el rol de facilitador, algo asi como un Scrum Master; ya que por lo general mantengo comunicación constante con el equipo de desarrollo para asegurarme del cumplimiento efectivo de las tareas asignadas.

- Soy organizado, responsable, disciplinado y valoro mucho la comunicación dentro del equipo. Además, tengo disposición para aprender y adaptarme a los cambios cuando sea necesario.

- Debo fortalecer mis conocimientos técnicos en diseño y arquitectura de software, para poder aportarle al equipo cuando se presenten problemas de este tipo.

## 🚀 Alejandro Baca Torregroza
- Me gustaría asumir el rol de programador, más que nada de backend y bases de datos; dado que manejo buena lógica de programación y soy capaz de crear bases de datos relacionales.

- Me gusta mantener órden en mis trabajos, aunque tengo la capacidad de improvisar cuando las cosas no salen como están planeadas. Además, considero que soy autodidacta y aprendo mucho haciendo proyectos.

- A pesar de manejar buena lógica de programación, debo mejorar el manejo de frameworks y arquitecturas importantes para el backend y el frontend, cosa que estoy trabajando desde este momento para apoyar al equipo.

## 🧑‍💻 Santiago Gamboa Martínez
- Me gustaría asumir un rol enfocado en la arquitectura y organización técnica del proyecto, contribuyendo al diseño estructural de la aplicación y a la definición clara de qué función cumple cada parte del sistema.

- Como fortalezas, considero que tengo buena capacidad de análisis, facilidad para estructurar soluciones y adaptabilidad para asumir diferentes responsabilidades según lo requiera el equipo.

- Debo mejorar en la retroalimentación constante al equipo, fortalecer la documentación continua y trabajar en una mejor planificación anticipada de las tareas.

## 💻 Carlos Arturo Parra Camelo

- Me gustaría desempeñar un rol orientado al desarrollo de software, especialmente en la parte de backend, bases de datos y organización de la lógica del sistema. También me interesa apoyar en la documentación del proyecto, ya que considero importante que el equipo entienda claramente cómo está estructurada la solución y qué función cumple cada parte.

- Como fortalezas, considero que tengo disposición para aprender, curiosidad por entender cómo funcionan las cosas y capacidad para relacionar ideas técnicas con problemas reales. También me gusta trabajar sobre proyectos aplicados, como propuestas de emprendimiento o sistemas que puedan resolver necesidades concretas. Además, tengo interés en herramientas como Java, MySQL, Git y GitHub, que son importantes para el desarrollo colaborativo de software.

- Debo fortalecer mi manejo de Git y GitHub en escenarios de trabajo en equipo, especialmente en el uso de ramas, Pull Requests y resolución de conflictos. También considero que debo mejorar mi planificación del tiempo, mi comunicación constante con el equipo y profundizar más en buenas prácticas de programación, arquitectura de software y documentación técnica.

# 🏭 Apartado 2
### Sección Grupal

- ¿Cómo van a usar el tablero (Kanban o Scrum) para organizar tareas?

El equipo adoptará la metodología **Kanban**, implementada en **Jira** como herramienta oficial de seguimiento. Para esto, el tablero contará con las siguientes columnas en orden: **Backlog → En progreso → Bloqueado → En revisión → Hecho → Rechazado → Terminada**.
En primer lugar, para la priorización de tareas se realizará ordenando el Backlog según impacto, urgencia y dependencia técnica. Por ejemplo, Las tareas críticas o bloqueantes tendrán prioridad sobre nuevas funcionalidades. En cuanto a las reglas operativas, ningún integrante puede tener más de **dos tareas en estado "En progreso"** simultáneamente. Para que una tarea pueda entrar a ese estado debe cumplir con los siguientes criterios: tener una descripción clara, incluir criterios de aceptación, estar asignada a un responsable y tener prioridad definida.
Respecto al movimiento entre estados: el paso a *En revisión* se hace cuando el entregable está completo y documentado; el estado *Hecho* solo puede asignarse tras revisión y aprobación de otra persona; y una tarea puede marcarse como *Rechazada* únicamente con justificación documentada.
Por otro lado, se considera que una tarea está **Terminada** cuando cumple todos estos criterios: el código está implementado, el commit fue realizado, el Pull Request fue creado y aprobado, no existen errores críticos abiertos y la documentación fue actualizada si aplica.
Finalmente, el tablero debe **revisarse diariamente** y todo cambio debe quedar registrado en los comentarios internos de cada tarea en Jira.

- Frecuencia mínima de reuniones o sincronizaciones.

Se establece una **sesión fija semanal los viernes**, en la tarde-noche. También, se pueden realizar encuentros al finalizar las clases de Ingeniería de Software I si el tiempo lo dispone, teniendo en ambos casos una duración máxima de una hora a dos horas, ya sea en modalidad presencial o virtual. Esta sesión tendrá siempre la misma agenda: revisión del estado del tablero, identificación de bloqueos, revisión de Pull Requests pendientes e importantes y planeación de la semana siguiente.
Adicionalmente, se realizarán **sesiones extraordinarias** cuando la carga de trabajo o la estructura del proyecto lo requiera. Estas deben convocarse con mínimo **24 horas de anticipación**, tener un objetivo específico y dejar un acta breve registrada en Jira o en el documento compartido del proyecto.
Para la **sincronización asincrónica diaria**, cada integrante tendrá que estar pendiente acerca de los cambios hechos al proyecto o si tiene un bloqueo activo que deba ser resuelto.

- Reglas básicas sobre uso de Git/GitHub (por ejemplo: crear ramas, revisar antes de hacer merge, no hacer cambios directos en la rama principal sin avisar, etc.).

El repositorio oficial será gestionado en **GitHub** bajo el siguiente flujo de trabajo:
La estrategia de ramas será: `main` como rama estable de producción, `develop` como rama de integración, y ramas específicas con los prefijos `feature/nombre-funcionalidad` y `fix/nombre-error` para cada cambio importante. Está **estrictamente prohibido** hacer push directo a `main`, hacer merge sin Pull Request y auto-aprobar un PR propio sin revisión previa.
Los Pull Requests deben incluir una descripción clara, el issue asociado en Jira y evidencia del cambio como capturas si aplica. Los PR menos importantes, deben ser revisados y aprobados por **mínimo un integrante diferente** al autor, en un tiempo máximo de **24 horas**. Los conflictos y merges críticos se resuelven preferiblemente durante la sesión fija semanal.
Para los commits se seguirá el estándar de **Conventional Commits**, usando los prefijos `feat:`, `fix:`, `docs:`, `refactor:`, `test:` y `chore:` según corresponda. Están prohibidos los mensajes genéricos como *"cambios"* o *"update"*.

- Compromisos sobre avisar cuando alguien no pueda cumplir una tarea.

Cuando un integrante detecte que no podrá cumplir con una tarea, debe **avisar con mínimo 24 horas de anticipación**, justificar la causa y proponer una alternativa, ya sea una extensión del plazo o una reasignación.

Dependiendo del origen del incumplimiento se actúa de la siguiente forma: si la causa es **dificultad técnica o incapacidad puntual**, la tarea regresa al estado *En progreso*, se reevalúa su prioridad, se reasigna formalmente a otro integrante y se le asigna al afectado una tarea acorde a sus posibilidades en ese momento. Si la causa es **falta de responsabilidad reiterada** —dos o más veces sin justificación válida— se convoca una reunión extraordinaria, se hace un llamado de atención y se levanta un acta y, si la situación afecta el cronograma del proyecto, se comunica al *stakeholder*.

- Acuerdos sobre cómo se tomarán decisiones en el equipo.

Las decisiones se toman de forma **grupal**, idealmente con todos los integrantes presentes. El proceso formal sigue estos pasos: presentación del problema, argumentación técnica de cada postura, propuesta de alternativas y votación. El criterio de aprobación es **mayoría simple** (50% + 1). En caso de empate, decide quien ejerza el rol de líder técnico del área que se está discutiendo en ese momento, o se escala directamente al *stakeholder*.
Si algún integrante no puede estar presente, deberá acogerse a la decisión tomada y será notificado oportunamente a través del grupo de **WhatsApp**, que es el canal de comunicación rápida del equipo. Si una decisión resulta difícil de concretar internamente tras agotar el proceso descrito, se escala al *stakeholder* para orientación.

Toda decisión técnica relevante debe quedar **documentada** en el issue correspondiente de Jira o en un documento compartido del proyecto.
