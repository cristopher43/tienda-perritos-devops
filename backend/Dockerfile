FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install --omit=dev && npm cache clean --force
COPY server.js ./

FROM node:18-alpine
WORKDIR /app
COPY --from=builder /app ./
USER node
EXPOSE 3001
CMD ["node", "server.js"]