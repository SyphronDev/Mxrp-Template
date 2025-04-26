# Guía de Eventos 🎮

Esta guía explica cómo trabajar con eventos en el bot.

## 📝 Estructura Básica

```javascript
import { Events } from 'discord.js';

export default {
  name: Events.EventName,
  once: false, // Opcional: true si el evento debe ejecutarse solo una vez
  
  async execute(...args) {
    // Lógica del evento
  }
};
```

## 🔄 Eventos Comunes

### Ready
```javascript
export default {
  name: Events.ClientReady,
  once: true,
  
  execute(client) {
    console.log(`¡Bot listo! Conectado como ${client.user.tag}`);
  }
};
```

### MessageCreate
```javascript
export default {
  name: Events.MessageCreate,
  
  execute(message) {
    if (message.author.bot) return;
    // Procesar mensaje
  }
};
```

### InteractionCreate
```javascript
export default {
  name: Events.InteractionCreate,
  
  async execute(interaction) {
    if (!interaction.isCommand()) return;
    // Manejar comando
  }
};
```

## 🛡️ Eventos de Moderación

### GuildMemberAdd
```javascript
export default {
  name: Events.GuildMemberAdd,
  
  async execute(member) {
    const channel = member.guild.systemChannel;
    if (!channel) return;
    
    await channel.send(`¡Bienvenido ${member} al servidor!`);
  }
};
```

### GuildMemberRemove
```javascript
export default {
  name: Events.GuildMemberRemove,
  
  execute(member) {
    console.log(`${member.user.tag} ha dejado el servidor`);
  }
};
```

## 🎵 Eventos de Voz

### VoiceStateUpdate
```javascript
export default {
  name: Events.VoiceStateUpdate,
  
  execute(oldState, newState) {
    // Manejar cambios en canales de voz
  }
};
```

## ⚡ Mejores Prácticas

1. Mantén los eventos organizados por categoría
2. Usa try-catch para manejar errores
3. Implementa logging para debugging
4. Optimiza para rendimiento
5. Valida permisos necesarios

## 🔍 Debugging

```javascript
import chalk from 'chalk';

console.log(chalk.blue(`[Event] ${eventName} triggered`));
console.log(chalk.yellow('Event data:', eventData));
```