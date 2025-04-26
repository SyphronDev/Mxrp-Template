# 🚀 Guía de Inicio

Esta guía te ayudará a configurar y ejecutar el bot de Discord.

## Requisitos Previos

- Node.js 16.9.0 o superior
- MongoDB
- Token de bot de Discord
- Bun (opcional, pero recomendado)

## Instalación

1. Clona el repositorio:
```bash
git clone https://github.com/tuusuario/discord-bot-template
```

2. Instala las dependencias:
```bash
bun install
# o
npm install
```

3. Crea un archivo `.env`:
```env
Token=tu_token_de_discord
MongoURI=tu_uri_de_mongodb
Developer=tu_id_de_discord
```

4. Inicia el bot:
```bash
bun run start
# o
npm run start
```

## Estructura del Proyecto

```
src/
├── Commands/     # Comandos del bot
├── Events/      # Manejadores de eventos
├── Functions/   # Funciones utilitarias
├── Handlers/    # Manejadores de sistemas
├── Schemas/     # Esquemas de MongoDB
└── Utils/       # Utilidades generales
```

## Siguientes Pasos

- [Crear tu primer comando](COMMANDS.md)
- [Manejar eventos](EVENTS.md)
- [Configurar la base de datos](DATABASE.md)