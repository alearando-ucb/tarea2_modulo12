# Etapa 1: Dependencias y Build
FROM node:20-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci  # Aquí instalas todo para poder correr tests o builds

# Etapa 2: Imagen final de Producción
FROM node:20-alpine
WORKDIR /app
COPY package*.json ./
# Instalamos SOLO producción desde cero
RUN npm ci --omit=dev 

# Copiamos solo el código fuente, NO los node_modules del builder
COPY . . 

EXPOSE 3000
CMD ["node", "src/server.js"]
