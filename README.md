# 🧠 RAG en n8n (Recuperación Aumentada de Información)

Este repositorio contiene un workflow funcional en **n8n** que permite responder preguntas sobre el contenido de documentos PDF y Google Docs, usando técnicas de **Recuperación Aumentada con Generación (RAG)**, almacenamiento vectorial en **Supabase** y un modelo de lenguaje alojado en **Groq**.

---

## 🎯 Objetivo del proyecto

Permitir que un usuario suba documentos a Google Drive y luego consulte su contenido usando lenguaje natural, gracias a un flujo automatizado que:
- Extrae texto de archivos.
- Genera embeddings con **Ollama**.
- Almacena vectores en Supabase.
- Usa un LLM para generar respuestas a partir del contenido procesado.

---

## ⚙️ Tecnologías utilizadas

- [n8n](https://n8n.io) – Plataforma de automatización.
- [Supabase](https://supabase.com) – Base de datos con pgvector.
- [Ollama](https://ollama.com) – Generador de embeddings (`nomic-embedding-text`).
- [Groq](https://groq.com) – Motor para el modelo de lenguaje `qwen-qwq-32b`.
- Google Drive – Fuente de archivos para procesar.

---

## 📂 Estructura del flujo

- **Detección automática** de archivos nuevos o actualizados en una carpeta de Google Drive.
- **Extracción del contenido** según tipo de archivo.
- **Transformación a vectores** (embeddings) y almacenamiento en Supabase.
- **Interfaz de chat** que consulta estos vectores y genera respuestas con el LLM.
- Archivos procesados se **mueven a una carpeta auxiliar** para evitar duplicaciones.

---

## 🧑‍💻 Uso básico

1. Instala y configura n8n (Docker, local o cloud).
2. Configura tus credenciales (Google Drive, Supabase, Groq, Ollama).
3. Crea dos carpetas en Google Drive:
   - Una para archivos a procesar.
   - Otra para mover los archivos ya tratados.
4. Importa el archivo `.json` del workflow a n8n.
5. Activa el flujo.
6. Sube un archivo a la carpeta correspondiente.
7. Haz preguntas al agente desde el nodo de chat o vía webhook.

> ⚠️ **Importante:** Sube un archivo a la vez. Si subes varios, solo el último será procesado.

---

## 📄 Documentación completa

Consulta el archivo [`Documentacion_RAG_Local_PDF.docx`](./Documentacion_RAG_Local_PDF.docx) incluido en este repositorio para obtener:

- Descripción detallada de todos los nodos.
- Explicación del flujo paso a paso.
- Manual de usuario.
- Notas sobre configuraciones y limitaciones.

---

## 📝 Notas

- Puedes modificar los modelos de embeddings o LLM según tus preferencias.
- El flujo está optimizado para un solo archivo a la vez.
- El workflo no esta preparado para usar archivos Excel.

---



