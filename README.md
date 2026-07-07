# Guia-Prompt-Engineering
Guía práctica para diseñar prompts efectivos en IA generativa: estructura (rol, contexto, tarea, restricciones, formato), técnicas como few-shot y chain of thought, ejemplos y plantilla reutilizable.
# Guía de Prompt Engineering: Cómo Escribir Buenos Prompts para IA Generativa

Esta guía explica la estructura, técnicas y ejemplos para diseñar prompts efectivos que logren que un modelo de inteligencia artificial (como Claude, ChatGPT, Gemini, etc.) entienda exactamente lo que necesitas.

---

## 1. ¿Qué es un prompt?

Un **prompt** es la instrucción o mensaje que le das a un modelo de IA para que genere una respuesta. Un buen prompt reduce la ambigüedad, evita respuestas genéricas y aumenta la probabilidad de obtener exactamente lo que buscas.

---

## 2. Estructura general de un buen prompt

Un prompt sólido normalmente combina estos elementos (no siempre se necesitan todos, pero entre más contexto, mejor resultado):

1. **Rol (Role):** Quién debe "ser" o "actuar como" la IA.
2. **Contexto (Context):** Información de fondo necesaria para entender la tarea.
3. **Tarea/Objetivo (Task):** Qué quieres que haga exactamente.
4. **Especificaciones/Restricciones (Constraints):** Formato, longitud, tono, qué evitar.
5. **Ejemplos (Examples):** Muestras de lo que esperas (opcional, pero muy efectivo).
6. **Formato de salida (Output format):** Cómo quieres que se vea la respuesta (lista, tabla, código, etc.).

### Plantilla base
```
Rol: Actúa como [rol específico].
Contexto: [información relevante de fondo].
Tarea: [qué necesitas que haga, de forma clara y específica].
Restricciones: [tono, longitud, público objetivo, qué no debe incluir].
Formato: [cómo debe estructurarse la respuesta].
Ejemplo (opcional): [muestra de referencia].
```

---

## 3. Explicación de cada componente

### 3.1 Rol
Asignar un rol ayuda a que la IA "enfoque" su conocimiento y estilo de respuesta.

**Ejemplos de roles:**
- "Actúa como un ingeniero de software senior especializado en Python."
- "Actúa como un profesor de historia explicando a estudiantes de secundaria."
- "Actúa como un abogado experto en derecho laboral colombiano."

### 3.2 Contexto
Entre más contexto le des, menos supuestos tendrá que hacer la IA (y menos errores cometerá).

**Ejemplo:**
> "Estoy documentando un proyecto de universidad sobre control de versiones con Git, dirigido a estudiantes que nunca han usado la terminal."

### 3.3 Tarea
Debe ser una instrucción clara, en lo posible con un verbo de acción concreto: *explica, genera, resume, compara, corrige, traduce, clasifica*.

**Mal ejemplo (ambiguo):**
> "Háblame de Git."

**Buen ejemplo (específico):**
> "Explica los comandos básicos de Git para inicializar un repositorio y subirlo a GitHub, paso a paso."

### 3.4 Restricciones / Especificaciones
Aquí defines:
- **Tono:** formal, informal, técnico, didáctico.
- **Longitud:** "máximo 300 palabras", "en 5 pasos".
- **Público objetivo:** principiantes, expertos, niños.
- **Qué evitar:** "sin usar tecnicismos", "sin código, solo teoría".

### 3.5 Ejemplos (few-shot prompting)
Darle a la IA un ejemplo de entrada/salida esperada mejora mucho la precisión, especialmente en tareas de formato específico o estilo de escritura.

**Ejemplo:**
> "Aquí tienes un ejemplo del estilo que busco:
> 'Paso 1: Abre la terminal. Paso 2: Escribe git init.'
> Ahora sigue ese mismo estilo para explicar cómo clonar un repositorio."

### 3.6 Formato de salida
Especifica si quieres:
- Lista numerada o con viñetas.
- Tabla.
- Bloque de código.
- Encabezados en Markdown.
- Cierta cantidad de secciones.

---

## 4. Técnicas adicionales para mejorar tus prompts

| Técnica | Descripción | Ejemplo |
|---|---|---|
| **Chain of thought** | Pedir que razone paso a paso antes de dar la respuesta final. | "Piensa paso a paso antes de responder." |
| **Few-shot prompting** | Dar 1-3 ejemplos de la tarea resuelta. | Ver sección 3.5 |
| **Zero-shot prompting** | Pedir la tarea directamente, sin ejemplos (para tareas simples). | "Traduce esta frase al inglés." |
| **Prompt iterativo** | Refinar el prompt en varias rondas según la respuesta obtenida. | "Hazlo más corto" / "Agrega un ejemplo" |
| **Etiquetas XML** | Usar etiquetas para separar secciones y que el modelo distinga claramente cada parte. | `<contexto>...</contexto>` `<tarea>...</tarea>` |
| **Negative prompting** | Indicar explícitamente qué NO debe hacer. | "No uses lenguaje técnico." |

---

## 5. Ejemplo completo de prompt bien estructurado

```
Rol: Actúa como un experto en ciberseguridad con 10 años de experiencia.

Contexto: Estoy preparando una capacitación para empleados de una empresa 
pequeña que no tienen conocimientos técnicos, sobre buenas prácticas de 
seguridad digital.

Tarea: Genera una lista de 8 recomendaciones prácticas de ciberseguridad 
para el día a día en la oficina.

Restricciones: 
- Usa lenguaje sencillo, sin tecnicismos.
- Cada recomendación debe tener máximo 2 líneas.
- Evita mencionar herramientas de pago.

Formato: Lista numerada, con un título corto en negrita por cada punto.
```

### Resultado esperado (ejemplo de cómo respondería la IA):
1. **Usa contraseñas fuertes** – Combina letras, números y símbolos, y no las repitas en varias cuentas.
2. **Activa la verificación en dos pasos** – Añade una capa extra de seguridad a tus cuentas.
3. *(...y así sucesivamente)*

---

## 6. Errores comunes al escribir prompts

- ❌ Ser demasiado vago ("hazme algo sobre marketing").
- ❌ Pedir varias tareas distintas mezcladas sin separarlas claramente.
- ❌ No indicar el formato de salida y esperar un formato específico.
- ❌ Asumir que la IA conoce contexto que no le diste (por ejemplo, referencias a conversaciones anteriores que no repetiste).
- ❌ No revisar ni iterar sobre la primera respuesta.

---

## 7. Checklist rápida antes de enviar un prompt

- [ ] ¿Definí un rol claro?
- [ ] ¿Di suficiente contexto?
- [ ] ¿La tarea es específica y usa un verbo de acción?
- [ ] ¿Especifiqué tono, longitud y público objetivo?
- [ ] ¿Indiqué el formato de salida deseado?
- [ ] ¿Agregué un ejemplo si la tarea lo requiere?

---

## 8. Plantilla reutilizable (copiar y pegar)

```
Rol: Actúa como [ROL].
Contexto: [CONTEXTO RELEVANTE].
Tarea: [QUÉ NECESITAS QUE HAGA].
Restricciones: [TONO / LONGITUD / PÚBLICO / QUÉ EVITAR].
Formato: [ESTRUCTURA DE LA RESPUESTA].
```

---
