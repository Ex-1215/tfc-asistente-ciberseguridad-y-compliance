# TFC: Asistente de Ciberseguridad y Compliance con IA
**Programa #IMPACT — #include13**
**Fundación GoodJob**

---

## 📝 Descripción del Proyecto
Este repositorio contiene el desarrollo técnico y la arquitectura del Trabajo Fin de Curso (TFC), consistente en un asistente conversacional funcional de ciberseguridad y cumplimiento normativo diseñado específicamente para la organización de referencia **MIDTECH S.A.**

El asistente automatiza la auditoría y análisis de políticas internas alineándolas con tres normativas críticas de ciberseguridad: **GDPR (Reglamento General de Protección de Datos), ISO 27001 (Sistema de Gestión de Seguridad de la Información) y el ENS (Esquema Nacional de Seguridad)**. Su objetivo es optimizar la toma de decisiones, mitigar riesgos legales y operativos, y agilizar la respuesta ante auditorías técnicas.

---

## 🛠️ Decisiones Tecnológicas y Justificación de Arquitectura

El sistema se ha estructurado bajo un patrón de diseño **RAG (Generación Aumentada por Recuperación)** implementado completamente en modalidad *No-Code/Low-Code*, garantizando un despliegue ágil, un mantenimiento sencillo y el aislamiento de datos confidenciales.

* **Capa de Interfaz (Front-end):** Chat integrado o bot conversacional para proporcionar un entorno intuitivo de interacción en lenguaje natural para los empleados de MIDTECH S.A.
* **Capa de Orquestación y Lógica:** **n8n / Make**. Actúa como el motor principal del sistema, gestionando el flujo completo de datos, la interceptación de mensajes del usuario, las peticiones de búsqueda documental y la construcción dinámica del contexto del prompt.
* **Capa del Modelo de Lenguaje (LLM):** Modelo de Inteligencia Artificial conectado mediante API Key, seleccionado por su avanzada capacidad de razonamiento lógico-normativo y su excelente ventana de contexto para el análisis legal.
* **Capa de Base de Conocimiento (RAG):** Repositorio documental en la nube donde se indexan las políticas de seguridad de la empresa y los textos oficiales de las normativas de referencia para evitar alucinaciones en el modelo.

---

## 📁 Estructura del Repositorio

Para facilitar la evaluación de la arquitectura técnica, la información se ha organizado bajo la siguiente estructura limpia de directorios:

* `/prompts`: Contiene el archivo `prompt_sistema_completo.txt` con el System Prompt unificado del asistente que gobierna el comportamiento del LLM y delimita sus cuatro capacidades funcionales.
* `/orquestacion`: Contiene el archivo `.json` que almacena la exportación real de la estructura de nodos y lógica de automatización diseñada.
* `/arquitectura`: Contiene el diagrama de flujo y mapa visual que describe las conexiones entre las distintas herramientas de software que componen la infraestructura del asistente.

---

## ⚙️ Capacidades Implementadas y Validadas

El asistente ejecuta de forma integrada las cuatro capacidades core exigidas en el proyecto a través de un único prompt del sistema robusto:
1. **Capacidad 1 - Análisis Normativo:** Interpretación de políticas corporativas bajo el marco normativo de GDPR, ISO 27001 y ENS.
2. **Capacidad 2 - Detección de Riesgos (Gap Analysis):** Identificación de brechas de cumplimiento técnico u organizativo y alertas tempranas.
3. **Capacidad 3 - Consultoría de Auditoría:** Respuestas automatizadas con evidencias y referencias bibliográficas precisas ante dudas del equipo auditor.
4. **Capacidad 4 - Plan de Mejora Continua:** Generación de recomendaciones de seguridad jerarquizadas bajo criterios de prioridad y criticidad de impacto.
