# Skill Back

## Contexto
Backend del proyecto con FastAPI, SQLAlchemy, Alembic y pruebas con pytest.

## Buenas prácticas de desarrollo
- Mantener el contrato técnico en inglés para rutas, esquemas, modelos y columnas.
- Reservar el español para los valores de negocio y mensajes visibles al usuario.
- Mover la lógica de negocio a `services` y dejar `api` solo para entrada/salida.
- Mantener los modelos ORM, esquemas Pydantic y repositorios sincronizados.
- Evitar imports de reexportación sin `__all__` o alias explícito en paquetes.
- Preferir fixtures pequeñas y aisladas en pruebas.

## Buenas prácticas de arquitectura
- Separar claramente `api`, `services`, `repositories`, `schemas` y `models`.
- Tratar `schemas` como la frontera pública del backend.
- Usar migraciones de Alembic cuando cambia la estructura de datos.
- Evitar efectos secundarios en módulos de paquete como `__init__.py`.
- Mantener pruebas de integración para los flujos de negocio críticos.

## Reglas MUST
- MUST ejecutar Ruff antes de entregar cambios de backend.
- MUST corregir importaciones no usadas o reexportarlas de forma explícita.
- MUST mantener alineados los esquemas de entrada con el modelo y el servicio.
- MUST evitar que `conftest.py` o las fixtures dependan de código frágil no documentado.
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
- Guardar la evidencia en `project-docs/Documentation/Project/`.

## Proceso de validación estática — flujo completo

### Fase 1 — Sin archivo de configuración (configuración por defecto)

**Ejecución inicial**
```
.venv\Scripts\python.exe -m ruff check src tests
```
Resultado:
```
Found 23 errors.
[*] 1 fixable with the `--fix` option.
```
Hallazgos principales:
- `F401` — imports sin uso en `src/app/models/__init__.py` y `src/app/schemas/__init__.py` (4 + 2 casos).
- `E402` — imports de módulo fuera de la parte superior del archivo en `tests/conftest.py` (15 casos, por diseño intencional del fixture).
- `F401` — import innecesario `TournamentModel` en `tests/integration/test_uc03_tournament.py`.

**Correcciones aplicadas (ronda 1)**
- `src/app/models/__init__.py` → añadido `__all__` con re-export explícito.
- `src/app/schemas/__init__.py` → añadido `__all__` con re-export explícito.
- `tests/conftest.py` → añadido comentario `# ruff: noqa: E402` para suprimir el E402 intencional.
- `tests/integration/test_uc03_tournament.py` → eliminado el import no usado.

**Verificación tras correcciones (ronda 1)**
```
.venv\Scripts\python.exe -m ruff check src tests
```
Resultado:
```
All checks passed!
```

---

### Fase 2 — Con archivo de configuración explícita (`ruff.toml`)

**Creación del archivo `ruff.toml`** en la raíz del backend con:
- `target-version = "py311"`, `line-length = 100`
- Reglas activas: `E`, `W` (pycodestyle), `F` (pyflakes), `I` (isort), `B` (bugbear)
- Ignoradas globalmente: `E501`, `B008`
- Ignorado por archivo: `E402` en `tests/conftest.py`

**Segunda ejecución (con la nueva configuración)**
```
.venv\Scripts\ruff.exe check src tests
```
Resultado: `Found 5 errors.`

Nuevos hallazgos por las reglas `I` y `B` (antes no estaban activas):
- `I001` — bloques de imports sin ordenar en `src/app/api/tournaments.py`, `src/app/repositories/player_repository.py`, `src/app/services/match_service.py`, `src/app/services/player_service.py`, `tests/conftest.py`, `tests/e2e/test_auth.py`, `tests/integration/test_uc02_alerts.py`, `tests/unit/test_alert_service_unit.py`.
- `W191` — indentación con tabs en `src/app/models/__init__.py` (4 líneas).
- `W293` — líneas en blanco con espacios en `tests/unit/test_alert_service_unit.py`.
- `B904` — excepción lanzada dentro de `except` sin `from err` en `src/app/services/player_service.py`.

**Correcciones aplicadas (ronda 2)**
```
.venv\Scripts\ruff.exe check src tests --fix
```
Ruff autofixó automáticamente: orden de imports (`I001`) y espacios en blanco (`W293`).

Correcciones manuales adicionales:
- `src/app/models/__init__.py` → tabs reemplazados por espacios en el bloque `__all__`.
- `src/app/services/player_service.py` → `raise HTTPException(...) from err` para satisfacer `B904`.

**Ejecución final**
```
.venv\Scripts\ruff.exe check src tests
```
Resultado:
```
All checks passed!
```

---

## Estado final
- Backend validado en verde con Ruff.
- Configuración activa documentada en `ruff.toml` (raíz del backend).
- Reglas aplicadas: `E`, `W`, `F`, `I`, `B` con exclusiones justificadas.
