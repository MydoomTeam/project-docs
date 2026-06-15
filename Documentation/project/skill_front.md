# Skill Front

## Contexto
Frontend del proyecto con React 19, TypeScript, Vite, React Router, React Hook Form, Zod y Framer Motion.

## Buenas prácticas de desarrollo
- Reutilizar componentes visuales comunes como `PlayerAvatar` en lugar de duplicar lógica.
- Mantener componentes de página delgados y mover lógica repetida a componentes o servicios.
- Usar tipos compartidos entre formularios, servicios y validaciones.
- Evitar mezclar responsabilidades de navegación, presentación y persistencia en el mismo componente.
- Mantener accesibles los estados de carga, vacío, éxito y error.
- Diseñar flujos estructurales como rutas reales, no como modales flotantes.

## Buenas prácticas de arquitectura
- Separar `pages`, `components`, `services`, `validation`, `assets` y `types`.
- Mantener los formularios alineados con el contrato del backend.
- Conservar la lógica del bracket aislada en un componente dedicado.
- Reutilizar el shell privado y la navegación existente.
- Evitar duplicar títulos o estados que ya se muestran en la página padre.

## Reglas MUST
- MUST mantener `npm run build` verde antes de cerrar un cambio.
- MUST alinear el formulario de creación con el payload real del backend.
- MUST respetar la estructura de rutas del app shell privado.
- MUST evitar estilos que rompan contraste o legibilidad.
- MUST usar componentes reutilizables para perfiles y avatares.

## Reglas SHOULD
- SHOULD mantener la sección de creación de torneos dentro de una ruta propia.
- SHOULD usar un flujo corto y claro cuando el caso de uso lo pida.
- SHOULD conservar el bracket legible en formatos de eliminación y ligas.
- SHOULD documentar cualquier ajuste visual que cambie el comportamiento esperado.
- SHOULD preferir datos reales del backend sobre placeholders.

## Reglas de documentación
- Registrar qué vista cambió y por qué.
- Documentar el comando de validación ejecutado y su resultado.
- Guardar evidencia en `project-docs/Documentation/Project/`.
- Mantener el texto corto, directo y revisable por terceros.

## Evidencia
- Comando ejecutado: `npm run build`
- Resultado final: compilación exitosa con Vite y TypeScript.
- Ajustes validados: creación de torneo en ruta dedicada, avatares reutilizables y bracket mejorado.

## Estado final
- Frontend validado en verde con build de producción.
- La UI quedó alineada con el backend y con el flujo de negocio.