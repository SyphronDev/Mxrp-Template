# Guía de Base de Datos 📊

Esta guía explica cómo trabajar con MongoDB en el bot.

## 🔧 Configuración

```javascript
import mongoose from 'mongoose';

mongoose.connect(process.env.MongoURI, {
  useNewUrlParser: true,
  useUnifiedTopology: true
});

mongoose.connection.on('connected', () => {
  console.log('MongoDB conectado');
});
```

## 📝 Esquemas

### Usuario
```javascript
import mongoose from 'mongoose';

const userSchema = new mongoose.Schema({
  userId: { type: String, required: true, unique: true },
  balance: { type: Number, default: 0 },
  inventory: [{ type: String }],
  lastDaily: Date
});

export default mongoose.model('User', userSchema);
```

### Servidor
```javascript
const guildSchema = new mongoose.Schema({
  guildId: { type: String, required: true, unique: true },
  prefix: { type: String, default: '!' },
  welcomeChannel: String,
  autoRole: String
});
```

## 🔄 Operaciones CRUD

### Crear
```javascript
const user = await User.create({
  userId: interaction.user.id,
  balance: 100
});
```

### Leer
```javascript
const user = await User.findOne({ userId: interaction.user.id });
```

### Actualizar
```javascript
await User.updateOne(
  { userId: interaction.user.id },
  { $inc: { balance: 100 } }
);
```

### Eliminar
```javascript
await User.deleteOne({ userId: interaction.user.id });
```

## 🛡️ Mejores Prácticas

1. Usa índices para optimizar consultas
2. Implementa validación de datos
3. Maneja errores de conexión
4. Usa transacciones cuando sea necesario
5. Mantén la consistencia de datos