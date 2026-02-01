# Interactive Skill Creation Wizard

**Purpose:** Guide users step-by-step through skill creation with prompts and confirmations at each phase.

**Mode:** Conversational wizard - ask questions, wait for responses, iterate until complete.

---

## How This Workflow Works

This is an **interactive workflow**. Instead of creating everything automatically, you will:

1. **Ask one question at a time**
2. **Wait for user response**
3. **Confirm understanding**
4. **Move to next phase**
5. **Summarize before creating**

**Important:** Never skip ahead. Each phase requires user input before proceeding.

---

## Phase 1: Discovery

### Step 1.1: Understand the Purpose

**Ask the user:**

```
¡Vamos a crear tu skill paso a paso!

Primero, cuéntame: ¿Qué problema quieres resolver con este skill?

Por ejemplo:
- "Quiero analizar código Python para encontrar errores"
- "Necesito generar documentación de APIs"
- "Quiero revisar prompts y mejorarlos"
```

**Wait for response.**

**Then confirm:**

```
Entiendo. Tu skill servirá para: [paraphrase their answer]

¿Es correcto? (sí/no)
```

### Step 1.2: Identify the Audience

**Ask:**

```
¿Quién usará este skill principalmente?

1. Desarrolladores
2. Escritores/Content creators
3. Analistas de datos
4. Todos los anteriores
5. Otro: ___
```

**Wait for response.**

---

## Phase 2: Identity

### Step 2.1: Choose a Name

**Suggest a name based on Phase 1:**

```
Basándome en lo que me contaste, sugiero estos nombres:

1. `[suggested-name-1]`
2. `[suggested-name-2]`
3. `[suggested-name-3]`

¿Cuál prefieres? También puedes proponer otro nombre.

(Recuerda: usa kebab-case, ejemplo: api-analyzer, code-reviewer)
```

**Wait for response.**

**Validate the name:**

- Is it kebab-case? If not, suggest correction
- Is it descriptive? If too vague (helper, utils), suggest alternative
- Confirm final name

### Step 2.2: Choose Category

**Ask:**

```
¿En qué categoría entra tu skill?

1. development - Desarrollo de software
2. documentation - Documentación
3. security - Seguridad
4. testing - Pruebas
5. data-analysis - Análisis de datos
6. prompt-engineering - Ingeniería de prompts
7. devops - Operaciones
8. Otra: ___
```

**Wait for response.**

---

## Phase 3: Triggers & Examples

### Step 3.1: Define Activation Triggers

**Ask:**

```
¿Cuándo debería activarse tu skill?

Dame 2-3 situaciones donde un usuario pediría ayuda que este skill puede resolver.

Ejemplo para un skill de code-review:
- "Cuando pidan revisar código"
- "Cuando busquen bugs o errores"
- "Cuando quieran mejorar la calidad del código"
```

**Wait for response.**

**Confirm triggers:**

```
Entonces tu skill se activará cuando:
1. [trigger 1]
2. [trigger 2]
3. [trigger 3]

¿Falta algún caso? ¿Quieres modificar alguno?
```

### Step 3.2: Create Usage Example

**Ask:**

```
Dame un ejemplo concreto de conversación donde se usaría tu skill:

Usuario: "[ejemplo de lo que diría el usuario]"

¿Qué diría el usuario para activar tu skill?
```

**Wait for response.**

**Confirm example:**

```
Perfecto. El ejemplo quedaría así:

<example>
User: "[their example]"
Assistant: "I'll use the [skill-name] skill to help with that."
</example>

¿Te parece bien?
```

---

## Phase 4: Scope Definition

### Step 4.1: Define Capabilities

**Ask:**

```
¿Qué debe HACER tu skill? Lista las 3-5 capacidades principales.

Ejemplo para python-analyzer:
1. Detectar errores de sintaxis
2. Identificar malas prácticas
3. Sugerir mejoras de performance
4. Verificar tipado
```

**Wait for response.**

### Step 4.2: Define Boundaries

**Ask:**

```
Igual de importante: ¿Qué NO debe hacer tu skill?

Esto ayuda a evitar confusiones. Por ejemplo:
- "No ejecuta código, solo lo analiza"
- "No modifica archivos automáticamente"
- "No trabaja con otros lenguajes, solo Python"
```

**Wait for response.**

**Confirm scope:**

```
Resumen del alcance:

✅ TU SKILL HACE:
1. [capability 1]
2. [capability 2]
3. [capability 3]

❌ TU SKILL NO HACE:
1. [boundary 1]
2. [boundary 2]

¿Correcto?
```

---

## Phase 5: Structure Decision

### Step 5.1: Determine Complexity

**Ask:**

```
¿Qué tan complejo es tu skill?

1. **Simple** - Solo necesita SKILL.md (< 300 líneas)
   → Skill enfocado en una tarea específica

2. **Estándar** - SKILL.md + algunos archivos de referencia
   → Tiene varios conceptos que explicar

3. **Complejo** - Estructura completa con templates y workflows
   → Múltiples procesos, plantillas reutilizables

¿Cuál describe mejor tu skill? (1, 2, o 3)
```

**Wait for response.**

### Step 5.2: Additional Components (if Standard or Complex)

**If they chose 2 or 3, ask:**

```
¿Qué componentes adicionales necesitas?

- [ ] **references/** - ¿Tienes conceptos complejos que explicar en detalle?
- [ ] **templates/** - ¿Tu skill genera contenido que necesita plantillas?
- [ ] **workflows/** - ¿Hay procesos paso a paso que documentar?
- [ ] **examples/** - ¿Quieres incluir ejemplos completos?

Dime cuáles necesitas (puedes elegir varios).
```

**Wait for response.**

---

## Phase 6: Content Gathering

### Step 6.1: Core Principles

**Ask:**

```
¿Cuáles son los 3-5 principios fundamentales de tu skill?

Estos son los conceptos clave que guían cómo funciona.

Ejemplo para code-reviewer:
1. "Código legible > código clever"
2. "Detectar bugs antes que estilo"
3. "Sugerir, no imponer"
```

**Wait for response.**

### Step 6.2: Main Instructions

**Ask:**

```
Ahora necesito las instrucciones principales.

¿Qué debe saber y hacer el agente cuando use tu skill?

Puedes darme:
- Reglas que debe seguir
- Pasos de un proceso
- Criterios de evaluación
- Formatos de output

(No te preocupes por el formato, yo lo estructuro)
```

**Wait for response.**

**If response is short, probe deeper:**

```
Gracias. ¿Puedes darme más detalles sobre:
- ¿Cómo debe estructurar su respuesta?
- ¿Hay casos especiales a considerar?
- ¿Qué errores comunes debe evitar?
```

---

## Phase 7: Review & Confirm

### Step 7.1: Present Summary

**Show complete summary:**

```
📋 RESUMEN DE TU SKILL

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

📛 Nombre: [skill-name]
📁 Categoría: [category]
📄 Estructura: [Simple/Estándar/Compleja]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

📝 DESCRIPCIÓN:
[Generated description based on their inputs]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

🎯 SE ACTIVA CUANDO:
• [trigger 1]
• [trigger 2]
• [trigger 3]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ CAPACIDADES:
1. [capability 1]
2. [capability 2]
3. [capability 3]

❌ LIMITACIONES:
1. [boundary 1]
2. [boundary 2]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

💡 PRINCIPIOS:
1. [principle 1]
2. [principle 2]
3. [principle 3]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

📂 ARCHIVOS A CREAR:
• ~/.config/opencode/skills/[skill-name]/SKILL.md
[• references/... if applicable]
[• templates/... if applicable]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

¿Todo correcto?

Opciones:
1. ✅ Crear el skill ahora
2. ✏️ Modificar algo (dime qué)
3. ❌ Cancelar
```

**Wait for response.**

### Step 7.2: Handle Modifications

**If they want to modify:**

```
¿Qué quieres cambiar?

1. Nombre
2. Descripción
3. Triggers/Ejemplos
4. Capacidades
5. Limitaciones
6. Principios
7. Estructura

(Dime el número o describe el cambio)
```

**Go back to relevant phase, make changes, return to summary.**

---

## Phase 8: Creation

### Step 8.1: Create SKILL.md

**Once confirmed, create the skill:**

```
¡Perfecto! Creando tu skill...
```

**Use the Write tool to create:**

```
~/.config/opencode/skills/[skill-name]/SKILL.md
```

**Generate content using this structure:**

```yaml
---
name: [skill-name]
description: >-
  [Generated description with what + when + example]

  <example>
  User: "[their example]"
  Assistant: "I'll use the [skill-name] skill."
  </example>

license: MIT
compatibility: agent-skills-standard
metadata:
  category: [category]
  version: "1.0.0"
  author: "[ask or use default]"
---

# [Skill Display Name]

[Introduction based on their purpose description]

## Core Principles

1. **[Principle 1]** - [explanation]
2. **[Principle 2]** - [explanation]
3. **[Principle 3]** - [explanation]

## When to Use

Use this skill when:
- [trigger 1]
- [trigger 2]
- [trigger 3]

Do NOT use this skill for:
- [boundary 1]
- [boundary 2]

## Capabilities

### [Capability 1]

[Instructions from their input]

### [Capability 2]

[Instructions from their input]

### [Capability 3]

[Instructions from their input]

## Examples

### Example 1: [Scenario]

[Based on their usage example]

## Limitations

- [boundary 1]
- [boundary 2]
```

### Step 8.2: Create Additional Files (if needed)

**If Standard or Complex structure:**

Create additional files based on their choices:

- `references/*.md`
- `templates/*.md`
- `workflows/*.md`

### Step 8.3: Confirm Creation

**After creating files:**

```
✅ ¡Skill creado exitosamente!

📂 Archivos creados:
• ~/.config/opencode/skills/[skill-name]/SKILL.md
[• other files if applicable]

🚀 Para usar tu skill:
1. Cualquier agente con `skill: true` puede cargarlo
2. Se activará automáticamente cuando [triggers]

📝 Próximos pasos sugeridos:
1. Revisar el SKILL.md y ajustar si es necesario
2. Probar con un caso real
3. Agregar más ejemplos si lo usas frecuentemente

¿Quieres que abra el archivo para revisarlo?
```

---

## Conversation Flow Summary

```
┌─────────────────────────────────────────────────────────┐
│  PHASE 1: DISCOVERY                                     │
│  "¿Qué problema resuelve?" → Wait → Confirm             │
│  "¿Quién lo usará?" → Wait                              │
└─────────────────────┬───────────────────────────────────┘
                      ▼
┌─────────────────────────────────────────────────────────┐
│  PHASE 2: IDENTITY                                      │
│  "Sugiero estos nombres..." → Wait → Validate           │
│  "¿Qué categoría?" → Wait                               │
└─────────────────────┬───────────────────────────────────┘
                      ▼
┌─────────────────────────────────────────────────────────┐
│  PHASE 3: TRIGGERS                                      │
│  "¿Cuándo se activa?" → Wait → Confirm                  │
│  "Dame un ejemplo de uso" → Wait → Format               │
└─────────────────────┬───────────────────────────────────┘
                      ▼
┌─────────────────────────────────────────────────────────┐
│  PHASE 4: SCOPE                                         │
│  "¿Qué debe hacer?" → Wait                              │
│  "¿Qué NO debe hacer?" → Wait → Confirm                 │
└─────────────────────┬───────────────────────────────────┘
                      ▼
┌─────────────────────────────────────────────────────────┐
│  PHASE 5: STRUCTURE                                     │
│  "¿Simple, estándar o complejo?" → Wait                 │
│  "¿Qué componentes?" → Wait (if needed)                 │
└─────────────────────┬───────────────────────────────────┘
                      ▼
┌─────────────────────────────────────────────────────────┐
│  PHASE 6: CONTENT                                       │
│  "¿Cuáles son los principios?" → Wait                   │
│  "¿Cuáles son las instrucciones?" → Wait → Probe        │
└─────────────────────┬───────────────────────────────────┘
                      ▼
┌─────────────────────────────────────────────────────────┐
│  PHASE 7: REVIEW                                        │
│  [Show complete summary]                                │
│  "¿Crear, modificar o cancelar?" → Wait                 │
│  If modify → Go back to relevant phase                  │
└─────────────────────┬───────────────────────────────────┘
                      ▼
┌─────────────────────────────────────────────────────────┐
│  PHASE 8: CREATE                                        │
│  Create SKILL.md with Write tool                        │
│  Create additional files if needed                      │
│  Confirm and suggest next steps                         │
└─────────────────────────────────────────────────────────┘
```

---

## Key Behaviors

### DO:

- ✅ Ask ONE question at a time
- ✅ Wait for user response before proceeding
- ✅ Confirm understanding before moving on
- ✅ Offer suggestions based on context
- ✅ Allow modifications at any point
- ✅ Use the user's language (Spanish if they write in Spanish)
- ✅ Show progress ("Fase 3 de 8...")

### DON'T:

- ❌ Ask multiple questions at once
- ❌ Assume answers without confirmation
- ❌ Skip phases
- ❌ Create files before Phase 8
- ❌ Use only English if user prefers Spanish
- ❌ Overwhelm with too much information at once

---

## Handling Edge Cases

### User wants to skip ahead

```
User: "Solo créame el skill, ya sé lo que quiero"

Response: "Entiendo que quieres ir rápido. Puedo usar el modo automático.
Dame un párrafo describiendo tu skill y lo creo directamente.

O si prefieres, continuamos paso a paso para asegurar el mejor resultado."
```

### User is unsure

```
User: "No estoy seguro..."

Response: "No hay problema. Te doy algunas opciones basadas en lo que me has contado:

1. [Option A] - [why it might work]
2. [Option B] - [why it might work]
3. [Option C] - [why it might work]

¿Cuál te suena mejor? También podemos explorar otra dirección."
```

### User wants to change something from earlier

```
User: "Espera, quiero cambiar el nombre"

Response: "¡Claro! El nombre actual es `[current-name]`.
¿Cuál te gustaría usar en su lugar?"

[After change]: "Perfecto, actualizado a `[new-name]`. Continuemos..."
```

### User provides too little information

```
User: "Que haga cosas de código"

Response: "Necesito un poco más de detalle. ¿Qué tipo de cosas con código?

Por ejemplo:
- ¿Revisar código para encontrar errores?
- ¿Generar código nuevo?
- ¿Refactorizar código existente?
- ¿Documentar código?

¿Cuál se acerca más a lo que necesitas?"
```

---

## Quick Mode Option

If user explicitly wants quick mode:

```
User: "Créame un skill rápido para X"

Response: "¡Entendido! Modo rápido activado.

Basándome en tu descripción, voy a crear:
- Nombre: [suggested-name]
- Propósito: [inferred purpose]
- Triggers: [inferred triggers]

¿Procedo o prefieres el modo guiado paso a paso?"
```

If they confirm, use `workflows/create-new-skill.md` instead.

---

## Language Adaptation

Detect user's language and adapt:

- **Spanish input** → Respond in Spanish
- **English input** → Respond in English
- **Mixed** → Match their dominant language

**Note:** The SKILL.md content should always be in **English** for LLM efficiency, but the conversation can be in the user's preferred language.

```
Response example (if user writes in Spanish):

"El contenido del SKILL.md lo escribiré en inglés para mejor
compatibilidad con los LLMs, pero nuestra conversación puede
seguir en español. ¿Te parece bien?"
```

---

## Success Metrics

A successful interactive session:

- ✅ User feels guided, not interrogated
- ✅ Each phase is clear and purposeful
- ✅ User can modify at any point
- ✅ Final skill matches user expectations
- ✅ User understands how to use their new skill
- ✅ Process feels collaborative, not automated
