# Agente de WhatsApp con AgentKit

**Video:** "Empezaste un negocio… pero te faltan clientes?" (13 de agosto) · Palabra clave: `LEADS` / `TRES`

## Qué es

Open source. Claude Code te entrevista sobre tu negocio y te genera un agente de WhatsApp completo (código + config + prueba local).

## Requisitos

- Python 3.11+
- Claude Code instalado
- API key de Anthropic
- Cuenta WhatsApp API (Meta Cloud API o Twilio)

## El repo

👉 https://github.com/Hainrixz/whatsapp-agentkit

## Pasos

1. `git clone https://github.com/Hainrixz/whatsapp-agentkit.git`
2. `cd whatsapp-agentkit`
3. `bash start.sh`
4. `claude`
5. Dentro de Claude Code escribí: `/build-agent`
6. Respondé las preguntas (negocio, horarios, tono, servicios, etc.)
7. Probá el agente en el simulador local
8. Cuando esté bien, conectalo a Meta o Twilio y desplegá

## Importante

- El kit es gratis (MIT).
- La API de Anthropic se paga por uso.
- WhatsApp tiene costos según el proveedor (Meta/Twilio).

## Cómo lo uso en el bot

Cuando alguien comenta `LEADS` o `TRES`, se le manda este contenido por privado (después de seguir la cuenta).
