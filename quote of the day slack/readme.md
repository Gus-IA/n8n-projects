# n8n Slack Workflow: Quote Of The Day Bot

Este repositorio contiene un workflow de **n8n** que envía automáticamente mensajes a Slack usando la app **Quote Of The Day Bot**.

---

## Descripción

El flujo realiza lo siguiente:

1. Se activa manualmente o mediante un trigger (puede ser cron, webhook, etc.).
2. Obtiene el contenido del mensaje (en este ejemplo, una “cita del día”).
3. Envía el mensaje a un canal de Slack utilizando la app **Quote Of The Day Bot**.
4. Permite enviar a canales públicos, privados (si el bot está invitado) o mensajes directos.

---

## Requisitos

- Una cuenta de [n8n](https://n8n.io/) configurada y accesible.
- App de Slack **Quote Of The Day Bot** creada e instalada en tu workspace.
- Token de bot de Slack con los siguientes scopes:
  - `chat:write`
  - `chat:write.public`
  - `channels:read`
  - `groups:read` (si se envía a canales privados)
- Canal de Slack donde la app tenga permiso para enviar mensajes.

---

## Configuración del workflow

1. Exporta este workflow en JSON desde n8n o importa el archivo `quote_of_the_day.json` desde este repositorio.
2. En el nodo **Slack – Send Message**, configura:
   - **Resource:** `Message`
   - **Operation:** `Send`
   - **Channel:** el **ID del canal** de Slack (no usar `#nombre-canal` para evitar errores `restricted_action_read_only_channel`).
3. Conecta las credenciales de Slack usando el token de la app.
4. Configura el trigger que prefieras (manual, cron, webhook, etc.).
5. Ejecuta el workflow para probar que el mensaje llegue al canal seleccionado.


