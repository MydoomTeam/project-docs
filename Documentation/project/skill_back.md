# 🛠️ Skill de Revisión — Backend ArenaSync (`skill_back.md`)

> **Plantilla de trabajo.** Esta es la *skill* que valida el backend contra buenas prácticas de lenguaje, arquitectura y reglas de código limpio. Complétenla, ejecútenla y peguen la evidencia "todo verde" donde dice `📸`. Copia final en `Documentation/Project/skill_back.md`.

---

## 1. Propósito de la skill
Validar que el backend cumple:
1. **Buenas prácticas del lenguaje** (Python) — guía básica abajo.
2. **Buena arquitectura** (por capas, con dependencias bien dirigidas).
3. **Reglas MUST / SHOULD** de código limpio y documentación.

El resultado esperado al ejecutarla es **"todo verde"** (sin violaciones).

---

## 2. Guía básica de buenas prácticas — Python
- **PEP 8** + nombres en **inglés**, `snake_case` (funciones/variables), `PascalCase` (clases), `UPPER_SNAKE_CASE` (constantes).
- Tipado con *type hints* (`def f(x: int) -> str:`).
- Funciones **pequeñas, una sola responsabilidad**, retornos tempranos, evitar anidación profunda.
- Sin imports sin usar ni código muerto (verificado con **ruff**).
- Excepciones específicas; no `except:` desnudo.
- Tests con **pytest**; lógica de negocio testeable sin BD.

## 3. Arquitectura del backend (detallada + dependencias)

**Estilo:** monolito por capas (FastAPI + SQLAlchemy 2.0 + PostgreSQL 16). Migraciones con Alembic.

```
Presentación   →   Aplicación   →   Dominio / Infraestructura
(controllers,      (services)        (repositories → models → BD)
 api)
```

| Capa | Carpeta(s) | Responsabilidad | Puede depender de |
|---|---|---|---|
| **Presentación** | `api/`, `controllers/` | HTTP: recibir request, validar borde, llamar services, construir response | services, schemas |
| **Aplicación** | `services/` | Lógica de negocio y orquestación de casos de uso | repositories, models, schemas |
| **Infraestructura** | `repositories/`, `models/`, `core/`, `tasks/` | Persistencia (ORM, sin SQL crudo), config, auth, scheduler | models, core |
| **Dominio** | `domain/` (models, schemas, constants) | Entidades y contratos de datos del stack jugadores/alertas | — |

**Flujo de dependencias permitido:** `Presentación → Aplicación → Infraestructura/Dominio`.
**Prohibido:** Presentación → repos/BD directo · Dominio → FastAPI/SQLAlchemy session · dependencias circulares · saltarse capas.

📊 *(Sugerencia: incluir aquí un diagrama de capas/flechas en el PDF final.)*

---

## 4. Reglas de revisión — MUST / SHOULD

### ✅ MUST HAVE (obligatorias — su incumplimiento es error)
| Regla | Cómo se verifica |
|---|---|
| Capas respetadas: presentación NO importa `repositories`/`models` ni usa SQL/Session | `grep` de imports por capa |
| Repositorios NO importan services/controllers; models no importan services/repos | `grep` de imports |
| Sin dependencias circulares | análisis de imports |
| Identificadores técnicos en **inglés** (archivos, clases, funciones, vars, columnas, rutas) | ruff + revisión |
| Sin imports sin usar / código muerto | `ruff check .` |
| Pruebas pasan (`pytest`) | `pytest` |
| Esquema gestionado por Alembic (no `create_all`) | revisión de `main.py` |
| Sin secretos versionados (`.env` fuera de git) | `git ls-files` |

### 🟡 SHOULD HAVE (recomendadas — su incumplimiento es advertencia)
| Regla | Nota |
|---|---|
| Funciones ≤ ~20 líneas, una responsabilidad | `match_service.py` es grande → candidato a dividir |
| Coverage del núcleo (services/algoritmos) alto | actualmente 67–100% |
| Documentación coherente (README, ADRs, docs/) | mantener al día |
| Excepciones de dominio en services en vez de `HTTPException` | mejora futura documentada |

---

## 5. Cómo ejecutar la skill y evidencia

> En este proyecto la "skill" se materializa con verificaciones reproducibles. Ejecuten y capturen **todo verde**:

```powershell
# 1. Lint (estilo + calidad) — debe dar: All checks passed!
python -m ruff check .

# 2. Tests — deben pasar todos
pytest -q

# 3. Verificación de capas (no debe imprimir violaciones)
#    Presentación no accede a infraestructura:
python -m ruff check .  # (las reglas de imports/orden ya lo cubren)
```

📸 **Captura 1:** `ruff check .` → `All checks passed!`
📸 **Captura 2:** `pytest -q` → `XX passed`
📸 **Captura 3:** (opcional) resultado de la verificación de capas en verde.

> 💡 Si usan una skill de Claude Code (`/code-review` u otra), peguen el texto del resultado aquí, mostrando que la revisión sale **sin hallazgos críticos**.

---

## 6. Resultado de la revisión
`[Pegar el resumen: "El backend cumple todas las reglas MUST y N de M SHOULD. Linter en verde, tests en verde, capas sin violaciones." + capturas.]`
