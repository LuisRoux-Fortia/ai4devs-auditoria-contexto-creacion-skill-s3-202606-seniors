# Entregable · Sesión 3 — Copilotos IA

- Luis Roux
- 28/06/2026
- openspec-sandbox

---

## 1. Hallazgos de la auditoría (Parte A)

> 3-5 cosas que el agente **no pudo inferir** del código y que tendrías que decirle explícitamente.
> Redáctalas para que otra persona las entienda sin contexto adicional. **Sin código propietario ni secretos.**

El repo que le solicité a Claude Code analizar fue el openspec-sandbox que creamos en el módulo 2 Spec-Driven Development 

1. Identificó como se arranca, pero omitió la relevancia del archivo .env. Para arrancar la app es crítico (sin .env válido no bootea) y normalmente debe ser omitido en .gitignore. 
2. Identificó el uso de sqlite3 pero omitió la ubicación que la base de datos de sqlite3 que esta almacenada en tmp. La existencia de sqlite3 es requerida para el funcionamiento de la app y normalmente esta omitida en .gitignore.
3.
4.
5.

El Proyecto es un boilerplate asi que no hay mucho mas relevante que identifiqué que se haya omitido.

## 2. SKILL.md de la skill creada (Parte B)

> Pega aquí el contenido completo de tu `.claude/skills/<nombre-skill>/SKILL.md`
> (o enlaza al archivo en tu repositorio sandbox).

```markdown
---
name: routes
description: List the HTTP routes registered in the AdonisJS API. Use when the
  user wants to see the available endpoints, inspect methods/paths/middleware,
  or verify a route was wired up after an OpenSpec change.
metadata:
  author: LuisRoux-Fortia
  version: "1.0"
---

List the API routes registered by the AdonisJS backend and present them clearly.

**Steps**

1. **List the routes from `backend/`:**
   ```bash
   node ace list:routes
   ```

2. **Present the result** as a table with: HTTP method, path, the controller +
   action handling it, and any middleware (notably `auth`). Group public routes
   (`/api/v1/auth/*`) separately from protected routes (`/api/v1/account/*`) to
   make the auth boundary obvious.

3. This skill is **read-only**: never edit `start/routes.ts`, controllers, or any
   source as part of listing routes.


---

## 3. Diario de decisiones

*Skill creada:* list-adonisjs-routes

*Decisiones de diseño tomadas:*
- Decisión 1: Como no tengo experiencia en la creación de skills, decidí que la skill que crearía sería informativa, que no cambiara nada del código 
- Decisión 2: Al aplicar openspec al AdonisJS, consideré que será común agregar end-points, así que una skill que se pudiera llamar para listar los endpoints existentes pudiera ser de ayuda para validar si un nuevo end-points ha sido agregado al proyecto.
- Decisión 3: Que fuera fácil de implementar y listar los endpoints de AdonisJS pueden listarse facilmente usando el comando `node ace list:routes`

*Qué me resultó fácil:*
- Listar los endpoints de AdonisJS

*Qué me resultó ambiguo o difícil de decidir:*
- Como formatear la salida del comando

*Tiempo real invertido:*
- 1 hora

*Qué probarías si tuvieras más tiempo:*
- Que se invoque cuando un spec cree un nuevo endpoint para verificar si se creo correctamente

*¿Usaste IA para crear la skill?* (qué partes generaste con IA y qué partes decidiste tú)
- Use la IA para escribir el prompt para formatear la salida del comando `node ace list:routes`

### Resultado de la prueba (Paso 8)

- ¿Se activó cuando lo esperabas?
Si
- ¿El resultado fue el que querías?
Si
- Si no, ¿qué crees que falló? (no la "arregles" — documenta el primer intento)
