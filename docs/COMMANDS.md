# Guía de Comandos

Esta guía explica cómo crear y gestionar comandos en el bot.

## 📝 Estructura Básica

```javascript
import { SlashCommandBuilder } from 'discord.js';

export default {
  data: new SlashCommandBuilder()
    .setName('comando')
    .setDescription('Descripción del comando'),
  
  cooldown: 5, // Opcional: cooldown en segundos
  developer: false, // Opcional: true para comandos de desarrollador
  
  async execute(interaction, client) {
    // Lógica del comando
  }
};
```

## 🔧 Tipos de Comandos

### Comandos Simples
```javascript
export default {
  data: new SlashCommandBuilder()
    .setName('ping')
    .setDescription('Comprueba la latencia del bot'),
    
  async execute(interaction, client) {
    await interaction.reply(`Pong! 🏓 Latencia: ${client.ws.ping}ms`);
  }
};
```

### Comandos con Opciones
```javascript
export default {
  data: new SlashCommandBuilder()
    .setName('usuario')
    .setDescription('Muestra información de un usuario')
    .addUserOption(option => 
      option
        .setName('target')
        .setDescription('Usuario a consultar')
        .setRequired(true)
    ),
    
  async execute(interaction, client) {
    const user = interaction.options.getUser('target');
    // Tu código aquí
  }
};
```

### Subcomandos
```javascript
export default {
  data: new SlashCommandBuilder()
    .setName('config')
    .setDescription('Configura el bot')
    .addSubcommand(subcommand =>
      subcommand
        .setName('prefix')
        .setDescription('Cambia el prefijo')
        .addStringOption(option =>
          option
            .setName('nuevo')
            .setDescription('Nuevo prefijo')
            .setRequired(true)
        )
    ),
    
  async execute(interaction, client) {
    const subcommand = interaction.options.getSubcommand();
    // Manejar subcomandos
  }
};
```

## 🎨 Embeds

```javascript
import { EmbedBuilder } from 'discord.js';

const embed = new EmbedBuilder()
  .setColor('#0099ff')
  .setTitle('Título')
  .setDescription('Descripción')
  .addFields(
    { name: 'Campo 1', value: 'Valor 1' },
    { name: 'Campo 2', value: 'Valor 2' }
  )
  .setTimestamp();

await interaction.reply({ embeds: [embed] });
```

## 🔄 Paginación

```javascript
const pages = [embed1, embed2, embed3];
const pagination = new client.Pagination(interaction)
  .addPages(pages)
  .hideIndexButton(false);
await pagination.display();
```

## ⚡ Mejores Prácticas

1. Usa try-catch para manejar errores
2. Implementa cooldowns para comandos pesados
3. Valida permisos antes de ejecutar
4. Usa respuestas efímeras cuando sea apropiado
5. Mantén los comandos modulares y reutilizables

## 🔍 Debugging

```javascript
console.log(chalk.cyan(`[Debug] Comando: ${interaction.commandName}`));
console.log(chalk.yellow(`[Debug] Opciones:`, interaction.options.data));
```

## 📚 Referencias

- [Discord.js Guide](https://discordjs.guide/)
- [Discord.js Documentation](https://discord.js.org/)