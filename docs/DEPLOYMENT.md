# Guía de Despliegue 🚀

Esta guía explica cómo desplegar el bot en diferentes plataformas.

## ☁️ Heroku

1. Crear cuenta en Heroku
2. Instalar Heroku CLI
3. Configurar variables de entorno:
   ```bash
   heroku config:set Token=tu_token
   heroku config:set MongoURI=tu_uri
   ```
4. Desplegar:
   ```bash
   git push heroku main
   ```

## 🖥️ VPS

1. Conectar por SSH
2. Instalar dependencias:
   ```bash
   curl -fsSL https://bun.sh/install | bash
   ```
3. Clonar repositorio
4. Configurar PM2:
   ```bash
   pm2 start index.js --name discord-bot
   ```

## 🐳 Docker

```dockerfile
FROM oven/bun:1

WORKDIR /app
COPY package.json .
COPY bun.lockb .

RUN bun install

COPY . .

CMD ["bun", "start"]
```

## 📝 Variables de Entorno

Crear archivo `.env`:
```env
Token=tu_token_de_discord
MongoURI=tu_uri_de_mongodb
Developer=tu_id_de_discord
```

## ⚡ Optimización

1. Usar caché cuando sea posible
2. Implementar rate limiting
3. Monitorear uso de recursos
4. Configurar logs
5. Implementar health checks