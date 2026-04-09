# 📬 Automatización de Cita del Día con IA (n8n + Groq + Slack)

Este repositorio contiene un flujo de trabajo de **n8n** avanzado que no solo envía una cita diaria, sino que utiliza **Inteligencia Artificial** para proporcionar contexto histórico e inspiración personalizada.

El mensaje se envía automáticamente a través de **Slackbot** todos los días laborables a las 8:00 AM.

---

## 🚀 Características principales

- **Programación Inteligente**: Ejecución automática de lunes a viernes a las 8:00 AM.
- **Citas Aleatorias**: Obtención de citas desde la API de [ZenQuotes](https://zenquotes.io/).
- **Agente de IA (LangChain)**: Un agente procesa la cita utilizando el modelo `llama-3` (vía Groq) para:
    - Buscar información sobre el autor en **Wikipedia**.
    - Analizar el contexto de la cita.
    - Generar un mensaje inspirador adicional.
- **Memoria de Corto Plazo**: El agente utiliza una memoria de ventana para mantener coherencia si se realizan ejecuciones seguidas.
- **Integración con Slack**: Publicación formateada directamente en el canal de Slackbot.

---

## 🛠️ Requisitos Técnicos

Para utilizar este flujo, necesitarás configurar las siguientes credenciales en n8n:

1.  **Slack OAuth2 API**: Para enviar los mensajes (Bot User OAuth Token).
2.  **Groq API**: Para el modelo de lenguaje (Llama).
3.  **Conexión a Internet**: Para acceder a Wikipedia y ZenQuotes.

---

## 🧩 Nodos utilizados

- `Schedule Trigger`: Activa el flujo a las 8 AM.
- `If`: Filtra los fines de semana.
- `HTTP Request`: Conecta con `zenquotes.io`.
- `AI Agent` (LangChain): El cerebro del flujo.
    - `Groq Chat Model`: Modelo de lenguaje.
    - `Wikipedia Tool`: Herramienta de búsqueda.
    - `Simple Memory`: Memoria de la sesión.
- `Slack`: Nodo final para el envío del mensaje.

---

## 📦 Instalación

1.  Copia el contenido de `Quote of the day Slack.json`.
2.  En n8n, crea un nuevo flujo y selecciona **Import from JSON**.
3.  Configura tus credenciales de Slack y Groq.
4.  ¡Activa el flujo y empieza el día con inspiración!
