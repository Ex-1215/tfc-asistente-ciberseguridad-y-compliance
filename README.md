# TFC: Asistente de Ciberseguridad y Compliance con IA

**Programa #IMPACT — #include13 Fundación GoodJob**

---

## 📝 Descripción del Proyecto

Este repositorio contiene el desarrollo técnico del Trabajo Fin de Curso (TFC), cuyo objetivo es construir un asistente conversacional especializado en ciberseguridad y cumplimiento normativo para la organización de referencia **MIDTECH S.A.**

La solución ha sido diseñada para analizar documentación corporativa, detectar incumplimientos regulatorios, responder preguntas de auditoría y proponer medidas de mejora basadas en evidencias documentales.

Para garantizar respuestas fundamentadas y minimizar las alucinaciones del modelo, se ha implementado una arquitectura **RAG (Retrieval-Augmented Generation)** que combina un modelo LLM con una base de conocimiento construida a partir de documentación normativa y de la política de seguridad de MIDTECH.

Las normativas utilizadas como referencia durante el proyecto son:

* GDPR (Reglamento General de Protección de Datos)
* ISO 27001
* ENS (Esquema Nacional de Seguridad)

---

## 🎯 Objetivo del Asistente

El asistente ha sido diseñado para ayudar a responsables de seguridad, compliance y auditoría a identificar riesgos y evaluar el grado de cumplimiento normativo de una organización mediante lenguaje natural.

Las funcionalidades implementadas permiten:

✅ Analizar políticas de seguridad corporativas.

✅ Detectar riesgos e incumplimientos regulatorios.

✅ Responder preguntas de auditoría basadas en documentación real.

✅ Generar propuestas de mejora priorizadas.

---

## 🔧 Stack Tecnológico

| Componente         | Tecnología Utilizada                 |
| ------------------ | ------------------------------------ |
| Modelo LLM         | OpenAI GPT-5.4-mini                   |
| Orquestación       | n8n                                  |
| Base Vectorial     | Supabase Vector Store                |
| Embeddings         | OpenAI Embeddings                    |
| Gestión Documental | Google Drive                         |
| Arquitectura       | RAG (Retrieval-Augmented Generation) |
| Interfaz           | n8n Chat                             |

---

## 🛠️ Decisiones Tecnológicas y Justificación

### 🤖 Modelo LLM: OpenAI GPT-5.4-mini

Se ha seleccionado GPT-5.4-mini por ofrecer una excelente relación entre rendimiento, velocidad de respuesta y coste operativo. Este modelo tiene una capacidad de razonamiento suficiente para tareas de análisis documental, consultas normativas y generación de recomendaciones de cumplimiento.

Su integración con n8n y OpenAI permite procesar consultas sobre documentación corporativa y normativa de forma eficiente, proporcionando respuestas estructuradas y fundamentadas en el contexto recuperado por el sistema RAG.

### 🔄 Orquestación: n8n

n8n actúa como núcleo de la solución, coordinando tanto la indexación documental como el flujo conversacional del asistente.

Su uso permite integrar servicios externos, automatizar procesos y gestionar la interacción entre el modelo LLM y la base vectorial.

### ☁️ Gestión Documental: Google Drive

Google Drive se utiliza como repositorio central para almacenar la documentación normativa y los documentos corporativos que posteriormente son procesados por el sistema.

### 🗄️ Base Vectorial: Supabase Vector Store

Los documentos son transformados en embeddings mediante OpenAI y almacenados en Supabase para permitir búsquedas semánticas eficientes durante las consultas del usuario.

---

## 🏗️ Arquitectura Implementada

La solución se compone de dos workflows principales desarrollados en n8n.

### Workflow 1 — Indexación Automática de Documentos

Este flujo se encarga de alimentar la base de conocimiento del asistente.

**Funcionamiento:**

1. Se detecta automáticamente la subida de un nuevo documento en Google Drive.
2. El archivo es descargado por n8n.
3. El documento es procesado mediante un Data Loader.
4. OpenAI genera los embeddings semánticos del contenido.
5. Los fragmentos son almacenados en Supabase Vector Store.

De esta forma, cualquier documento añadido a la carpeta configurada queda disponible automáticamente para futuras consultas.

---

### Workflow 2 — Asistente Conversacional RAG

Este flujo gestiona la interacción con el usuario y la generación de respuestas.

**Funcionamiento:**

1. El usuario envía una consulta mediante el chat.
2. El nodo wait retiene la consulta enviada por el chat durante 10 segundos y la pasa al asistente. Esto se hace para evitar congestionar la API del modelo LLM con muchas solicitudes.
3. El AI Agent recibe la petición.
4. Supabase Vector Store recupera los fragmentos más relevantes mediante búsqueda semántica.
5. GPT-5.4-mini recibe los fragmentos recuperados junto con la consulta del usuario.
6. El modelo genera una respuesta basada en la documentación indexada.
7. La memoria conversacional conserva el contexto reciente del diálogo.
8. El usuario recibe una respuesta fundamentada y trazable.

Esta arquitectura permite responder utilizando información real almacenada en la base documental en lugar de depender exclusivamente del conocimiento interno del modelo.

---

## ⚙️ Capacidades Implementadas

El asistente integra las cuatro capacidades obligatorias definidas en el Trabajo Fin de Curso.

### 📋 Capacidad 1 — Análisis de Políticas de Seguridad

Analiza la política corporativa de MIDTECH identificando:

* Áreas cubiertas.
* Nivel de detalle de cada área.
* Controles existentes.
* Ámbitos no contemplados.

Las conclusiones se apoyan en evidencias localizadas dentro del propio documento.

---

### 🚨 Capacidad 2 — Detección de Riesgos e Incumplimientos

Compara la política de seguridad frente a las normativas indexadas para identificar brechas de cumplimiento.

Para cada hallazgo se proporciona:

* Área normativa afectada.
* Carencia detectada.
* Nivel de criticidad.
* Referencia normativa aplicable.

---

### 💬 Capacidad 3 — Respuesta a Preguntas de Auditoría

Permite formular preguntas en lenguaje natural relacionadas con:

* GDPR.
* ISO 27001.
* ENS.
* Política de seguridad de MIDTECH.

Las respuestas incluyen referencias explícitas a la documentación utilizada durante la consulta.

---

### 📈 Capacidad 4 — Propuestas de Mejora

Genera recomendaciones priorizadas para aumentar el nivel de cumplimiento y madurez de seguridad de la organización.

Cada propuesta incorpora:

* Acción recomendada.
* Justificación normativa.
* Prioridad.
* Esfuerzo estimado.

---

## 📚 Base de Conocimiento

La base documental utilizada durante el proyecto está compuesta por:

* GDPR
* ISO 27001
* ENS
* Política de Seguridad de MIDTECH S.A.

Todos los documentos han sido indexados mediante OpenAI Embeddings y almacenados en Supabase Vector Store para permitir su recuperación semántica durante las consultas.

---

## 📁 Estructura del Repositorio

```text
.
├── diagramas_de_flujo/
│   ├── Diagrama de flujo (Workflow principal chatbot n8n).png
│   └── Flux diagram (indexación documentos en Supabase).png
├── prompt_utilizado/
│   ├── system_prompt_sistema_completo.txt
├── workflows/
│   ├── Main workflow (chatbot).json
│   └── RAG workflow (upload Drive to Supabase).json
└──

```

---

## 🔍 Flujo General de Funcionamiento

1. El usuario realiza una consulta o solicita un análisis.
2. n8n recibe y procesa la petición.
3. Supabase recupera los fragmentos más relevantes mediante búsqueda semántica.
4. GPT-5.4-mini utiliza el contexto recuperado para construir la respuesta.
5. El asistente genera una respuesta fundamentada en la documentación indexada.
6. El usuario recibe una respuesta trazable y alineada con la normativa correspondiente.

---

## 🚀 Posibles Mejoras Futuras

* Incorporación de normativa NIS2.
* Inclusión de LOPDGDD dentro de la base documental.
* Generación automática de informes PDF.
* Dashboard de riesgos y cumplimiento.
* Exportación automática de evidencias para auditorías.

---

## 👨‍🎓 Autor

Trabajo desarrollado como parte del Trabajo Fin de Curso del programa **#IMPACT #include13** de la **Fundación GoodJob**.

El proyecto tiene fines exclusivamente académicos y de demostración tecnológica.
