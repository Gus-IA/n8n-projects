# 🌤️ Boletín Diario Personalizado con Agente de IA (n8n + Groq)

Este repositorio contiene un flujo de trabajo de **n8n** que implementa un agente de IA avanzado capaz de actuar como un asistente editorial matutino. El agente recopila datos en tiempo real de múltiples fuentes y redacta un mini-boletín informativo personalizado.

El resultado se envía automáticamente a través de **Slackbot** cada mañana a las 8:00 AM.

---

## 🚀 Capacidades del Agente

El agente utiliza el modelo **Llama 3.3 70B** (vía Groq) para realizar las siguientes tareas de forma autónoma:

1.  **Clima Local**: Consulta el estado del tiempo en San Francisco (u otra ciudad configurada) mediante la API de **OpenWeatherMap**.
2.  **Curación de Noticias**: Busca y selecciona de 2 a 3 noticias positivas en tendencia usando **SerpAPI**.
3.  **Cultura General**: Realiza búsquedas en **Wikipedia** para incluir un dato curioso o "fun fact" relevante al día.
4.  **Redacción Creativa**: Formatea toda la información como un boletín de correo electrónico elegante en formato Markdown.

---

## 🛠️ Requisitos de Configuración

Para poner en marcha este flujo, es necesario configurar las siguientes credenciales en n8n:

- **Groq API**: Acceso al modelo `llama-3.3-70b-versatile`.
- **SerpAPI**: Para las búsquedas de noticias en Google.
- **OpenWeatherMap API**: Para obtener datos meteorológicos.
- **Slack OAuth2 API**: Para el envío automatizado a Slackbot.

---

## 🧩 Estructura del Flujo

- `Schedule Trigger`: Ejecuta el flujo diariamente a las 8:00 AM.
- `AI Agent` (LangChain): Orquesta las herramientas de IA.
    - `Groq Chat Model`: El motor de procesamiento de lenguaje natural.
    - `OpenWeatherMap Tool`: Herramienta de datos climáticos.
    - `SerpAPI Tool`: Herramienta de búsqueda web.
    - `Wikipedia Tool`: Herramienta de consulta enciclopédica.
    - `Simple Memory`: Mantiene el contexto de ejecuciones anteriores para evitar repeticiones.
- `Slack Node`: Canal de salida para el boletín final.

---

## 📦 Cómo empezar

1.  Importa el archivo `OpenWeather AI Agent.json` en tu instancia de n8n.
2.  Configura las cuatro credenciales requeridas mencionadas anteriormente.
3.  Ajusta el prompt del `AI Agent` si deseas cambiar la ciudad o el estilo del boletín.
4.  Activa el workflow.
