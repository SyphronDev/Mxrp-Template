# Ejemplos de Código 📚

Colección de ejemplos prácticos para funcionalidades comunes.

## 🎮 Comandos de Juego

### Economía
```javascript
export default {
  data: new SlashCommandBuilder()
    .setName('balance')
    .setDescription('Ver tu balance'),
    
  async execute(interaction, client) {
    const user = await User.findOne({ userId: interaction.user.id });
    const balance = user?.balance || 0;
    
    const embed = new EmbedBuilder()
      .setTitle('💰 Balance')
      .setDescription(`Tienes $${balance}`);
      
    await interaction.reply({ embeds: [embed] });
  }
};
```

### Sistema de Niveles
```javascript
export default {
  data: new SlashCommandBuilder()
    .setName('rank')
    .setDescription('Ver tu nivel'),
    
  async execute(interaction, client) {
    const user = await Level.findOne({ userId: interaction.user.id });
    const level = user?.level || 1;
    const xp = user?.xp || 0;
    
    // Crear canvas con barra de progreso
    // ...
  }
};
```

## 🛠️ Utilidades

### Recordatorios
```javascript
export default {
  data: new SlashCommandBuilder()
    .setName('recordatorio')
    .setDescription('Crear un recordatorio')
    .addStringOption(option =>
      option
        .setName('tiempo')
        .setDescription('Tiempo (1h, 30m, etc.)')
        .setRequired(true)
    )
    .addStringOption(option =>
      option
        .setName('mensaje')
        .setDescription('Mensaje del recordatorio')
        .setRequired(true)
    ),
    
  async execute(interaction, client) {
    const tiempo = interaction.options.getString('tiempo');
    const mensaje = interaction.options.getString('mensaje');
    
    // Parsear tiempo y crear recordatorio
    // ...
  }
};
```

### Sistema de Tickets
```javascript
export default {
  data: new SlashCommandBuilder()
    .setName('ticket')
    .setDescription('Crear un ticket de soporte'),
    
  async execute(interaction, client) {
    // Crear canal privado
    const channel = await interaction.guild.channels.create({
      name: `ticket-${interaction.user.username}`,
      type: ChannelType.GuildText,
      permissionOverwrites: [
        {
          id: interaction.guild.id,
          deny: [PermissionsBitField.Flags.ViewChannel],
        },
        {
          id: interaction.user.id,
          allow: [PermissionsBitField.Flags.ViewChannel],
        },
      ],
    });
    
    // Enviar mensaje inicial
    // ...
  }
};
```

## 🎵 Música

### Reproducir
```javascript
export default {
  data: new SlashCommandBuilder()
    .setName('play')
    .setDescription('Reproducir música')
    .addStringOption(option =>
      option
        .setName('canción')
        .setDescription('Nombre o URL de la canción')
        .setRequired(true)
    ),
    
  async execute(interaction, client) {
    const query = interaction.options.getString('canción');
    
    // Conectar a canal de voz
    // Buscar y reproducir música
    // ...
  }
};
```

## 🔍 Búsqueda

### Wikipedia
```javascript
export default {
  data: new SlashCommandBuilder()
    .setName('wiki')
    .setDescription('Buscar en Wikipedia')
    .addStringOption(option =>
      option
        .setName('búsqueda')
        .setDescription('Término a buscar')
        .setRequired(true)
    ),
    
  async execute(interaction, client) {
    const término = interaction.options.getString('búsqueda');
    
    // Realizar búsqueda
    // Mostrar resultados
    // ...
  }
};
```