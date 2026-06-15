# Skill Backend

## Contexto
Backend del proyecto con FastAPI, SQLAlchemy, Alembic y pruebas con pytest.

## Buenas prácticas de desarrollo
- Mantener el contrato técnico en inglés para rutas, esquemas, modelos y columnas.
- Reservar el español para los valores de negocio y mensajes visibles al usuario.
- Mover la lógica de negocio a services y dejar api solo para entrada/salida.
- Mantener los modelos ORM, esquemas Pydantic y repositorios sincronizados.
- Evitar imports de reexportación sin __all__ o alias explícito en paquetes.
- Preferir fixtures pequeñas y aisladas en pruebas.

## Buenas prácticas de arquitectura
- Separar claramente api, services, repositories, schemas y models.
- Tratar schemas como la frontera pública del backend.
- Usar migraciones de Alembic cuando cambia la estructura de datos.
- Evitar efectos secundarios en módulos de paquete como __init__.py.
- Mantener pruebas de integración para los flujos de negocio críticos.

## Reglas MUST
- MUST ejecutar Ruff antes de entregar cambios de backend.
- MUST corregir importaciones no usadas o reexportarlas de forma explícita.
- MUST mantener alineados los esquemas de entrada con el modelo y el servicio.
- MUST evitar que conftest.py o las fixtures dependan de código frágil no documentado.
- MUST revisar que cambios de validación no rompan los casos de uso existentes.

## Reglas SHOULD
- SHOULD añadir pruebas focalizadas cuando se cambia una validación o contrato.
- SHOULD documentar decisiones no obvias en README, ADR o notas de arquitectura.
- SHOULD preferir helpers pequeños y reutilizables para semilla de datos.
- SHOULD revisar la salida del linter con el mismo alcance del código modificado.

## Reglas de documentación
- Registrar comando ejecutado, resultado y fecha.
- Anotar archivos tocados y motivo del cambio.
- Mantener lenguaje claro y breve.
- Guardar la evidencia en project-docs/Documentation/Project/.

## Evidencia
- Comando ejecutado: .venv\Scripts\python.exe -m ruff check src tests
- Resultado final: All checks passed!
- Archivos ajustados para limpiar el linter: src/app/models/__init__.py, src/app/schemas/__init__.py, tests/conftest.py, tests/integration/test_uc03_tournament.py

## Estado final
- Backend validado en verde con Ruff.
- El proyecto queda listo para documentar el resultado como evidencia formal.
