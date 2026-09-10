# Sistema de prospección: 100+ leads en una hora

**Video:** "Empezaste un negocio… pero te faltan clientes?" (13 de agosto) · Palabra clave: `LEADS`

## Qué hace

Le pasás a Claude el perfil de tu cliente ideal y en una hora te trae más de 100 prospectos con nombre, mail y teléfono. Después los contacta en automático con n8n. Resultado real: más de 12 reuniones en una semana.

## Cómo funciona (a alto nivel)

1. **Scraping de leads**: Claude arma la consulta de búsqueda a partir de tu perfil de cliente ideal y usa una herramienta de scraping (ej. Apify) para traer los datos.
2. **Enriquecimiento**: por cada prospecto, completa nombre, mail y teléfono disponibles.
3. **Outreach automático**: n8n toma la lista y manda el primer contacto (mail o WhatsApp) sin que lo hagas a mano.

> ⚠️ Santiago: el video menciona Claude + Apify + n8n para armar esto, pero no tengo el prompt exacto ni el workflow de n8n que usás. Si me pasás eso (el prompt de búsqueda, o el JSON del workflow), arreglo esta carpeta con el sistema real en vez de la descripción general.

## Cómo lo uso en el bot

Cuando alguien comenta `LEADS`, se le manda este contenido por privado (después de seguir la cuenta).
