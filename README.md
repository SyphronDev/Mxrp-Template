# Discord.js Bot Template 🤖

Este es un template educativo para crear bots de Discord usando Discord.js v14. Está diseñado para ayudarte a aprender los conceptos fundamentales del desarrollo de bots.

## 🚀 Características

- Sistema de comandos modular y escalable
- Manejo de eventos organizado
- Sistema de cooldowns para comandos
- Registro detallado de comandos y eventos
- Soporte para subcomandos
- Sistema de paginación para embeds
- Formateo de moneda
- Integración con MongoDB

## 📋 Requisitos

- Node.js 16.9.0 o superior
- MongoDB
- Token de bot de Discord
- Bun (opcional, pero recomendado)

## 🛠️ Instalación

1. Clona este repositorio
```bash
git clone https://github.com/SyphronDev/Mxrp-Template.git
```

2. Instala las dependencias
```bash
bun install
# o
npm install
```

3. Crea un archivo `.env` en la raíz del proyecto:
```env
Token=tu_token_de_discord
MongoURI=tu_uri_de_mongodb
Developer=tu_id_de_discord
```

4. Inicia el bot
```bash
bun run start
# o
npm run start
```

## 📚 Estructura del Proyecto

```
src/
├── Commands/         # Comandos del bot
├── Events/          # Manejadores de eventos
├── Functions/       # Funciones utilitarias
├── Handlers/        # Manejadores de sistemas
├── Schemas/         # Esquemas de MongoDB
└── Utils/           # Utilidades generales
```

## 🎓 Guía de Aprendizaje

### 1. Creando Comandos

Los comandos se crean en la carpeta `src/Commands`. Ejemplo de estructura:

```javascript
import { SlashCommandBuilder } from 'discord.js';

export default {
  data: new SlashCommandBuilder()
    .setName('ping')
    .setDescription('Responde con Pong!'),
    
  async execute(interaction, client) {
    await interaction.reply('Pong! 🏓');
  }
};
```

### 2. Manejando Eventos

Los eventos se manejan en `src/Events`. Ejemplo:

```javascript
import { Events } from 'discord.js';

export default {
  name: Events.MessageCreate,
  async execute(message, client) {
    if (message.author.bot) return;
    // Tu código aquí
  }
};
```

### 3. Usando el Sistema de Paginación

```javascript
const pages = [embed1, embed2, embed3];
const pagination = new client.Pagination(interaction)
  .addPages(pages)
  .hideIndexButton(false);
await pagination.display();
```

## 📖 Recursos de Aprendizaje

- [Documentación de Discord.js](https://discord.js.org/)
- [Guía de Discord.js](https://discordjs.guide/)
- [Discord Developers Portal](https://discord.com/developers/docs)
- [MongoDB Documentation](https://docs.mongodb.com/)

## 🤝 Contribuyendo

Las contribuciones son bienvenidas! Por favor, lee las [guías de contribución](CONTRIBUTING.md) antes de enviar un pull request.

## 📝 Licencia

Este proyecto está bajo la Licencia GNU GPL v3 - mira el archivo [LICENSE](LICENSE) para más detalles.

## 🔗 Enlaces Útiles

- [Discord.js Server](https://discord.gg/djs)
- [Node.js Documentation](https://nodejs.org/docs)
- [Bun Documentation](https://bun.sh/docs)
