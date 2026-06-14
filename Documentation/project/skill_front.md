# 🎨 Skill de Revisión — Frontend (`skill_front.md`)

> ⚠️ **Este documento pertenece al repositorio del FRONTEND**, no al backend. Está aquí como **plantilla** para que el/la integrante del front la copie a su repo y la complete. La versión final va en `Documentation/Project/skill_front.md`.
>
> Adapten los `[corchetes]` a su stack real (React/Vue/Angular, JS/TS, etc.) y peguen evidencia "todo verde" donde dice `📸`.

---

## 1. Propósito de la skill
Validar que el frontend cumple:
1. **Buenas prácticas del lenguaje** (`[JavaScript / TypeScript]`).
2. **Buena arquitectura** (componentes, servicios, estado, ruteo).
3. **Reglas MUST / SHOULD** de código limpio y documentación.

Resultado esperado: **"todo verde"**.

---

## 2. Guía básica de buenas prácticas — `[lenguaje del front]`
- Estándar de estilo: **ESLint** (+ **Prettier** para formato). Reglas en `.eslintrc`.
- Nombres en inglés; componentes en `PascalCase`, funciones/variables en `camelCase`.
- Tipado con **TypeScript** (`[si aplica]`): evitar `any`, tipar props/estado.
- Componentes pequeños, una responsabilidad; lógica reutilizable en hooks/servicios.
- Sin código muerto, sin `console.log` en producción, sin imports sin usar.
- Manejo de errores y estados de carga en llamadas a la API.

## 3. Arquitectura del frontend (detallada + dependencias)

```
[ Vistas/Páginas ] → [ Componentes ] → [ Servicios/API client ] → [ Backend (ArenaSync) ]
                        ↘ [ Estado/Store ] ↗
```

| Capa | Carpeta | Responsabilidad | Depende de |
|---|---|---|---|
| Páginas/Vistas | `[src/pages]` | composición de pantallas, ruteo | componentes, store |
| Componentes | `[src/components]` | UI reutilizable, presentación | — |
| Servicios/API | `[src/services o api]` | llamadas HTTP al backend | cliente HTTP |
| Estado | `[src/store]` | estado global/local | servicios |

> 🔗 **Integración con el backend:** el front consume la API en **inglés** (`POST /users`, `POST /sessions`, `/tournaments/...`) y **traduce los valores a español para el usuario** (estados, formatos), porque el backend devuelve `status`, `elimination_type`, etc. con valores en español como contenido. *(Ver README del backend.)*

📊 *(Sugerencia: incluir un diagrama de componentes/flujo de datos en el PDF.)*

---

## 4. Reglas de revisión — MUST / SHOULD

### ✅ MUST HAVE
| Regla | Cómo se verifica |
|---|---|
| ESLint sin errores | `npm run lint` |
| Sin imports/variables sin usar, sin `console.log` | ESLint |
| Componentes con una sola responsabilidad | revisión |
| Llamadas a la API centralizadas en servicios (no `fetch` suelto en componentes) | revisión |
| Nombres en inglés / consistentes | ESLint + revisión |
| Manejo de errores de la API (401, 403, 404, 422) | revisión |
| Sin secretos/tokens hardcodeados | revisión + `.gitignore` |

### 🟡 SHOULD HAVE
| Regla | Nota |
|---|---|
| Tipado fuerte (TS), evitar `any` | `[si usan TS]` |
| Componentes ≤ ~150 líneas | dividir si crecen |
| Documentación (README del front, cómo correr) | mantener |
| Accesibilidad básica (labels, alt) | recomendado |

---

## 5. Cómo ejecutar la skill y evidencia
```bash
# 1. Lint
npm run lint        # o: npx eslint .   → debe salir sin errores

# 2. Formato
npx prettier --check .

# 3. Build/tests (si aplica)
npm run build
npm test
```
📸 **Captura 1:** `npm run lint` sin errores.
📸 **Captura 2:** `npm run build` / tests en verde.

---

## 6. Resultado de la revisión
`[Pegar resumen: "El frontend cumple las reglas MUST y N de M SHOULD. ESLint en verde, build en verde." + capturas.]`
