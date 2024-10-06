# Fase 1: Build dell'applicazione Next.js
FROM node:16 AS builder

# Imposta la directory di lavoro
WORKDIR /app

# Copia i file di package.json e package-lock.json
COPY package*.json ./

# Installa le dipendenze
RUN npm install

# Copia tutto il resto dell'applicazione
COPY . .

# Costruisci l'app per la produzione
RUN npm run build

# Fase 2: Configurazione NGINX per servire l'applicazione
FROM nginx:alpine

# Copia la configurazione NGINX personalizzata
COPY ./nginx.conf /etc/nginx/conf.d/default.conf

# Copia i file buildati da Next.js nella cartella che serve NGINX
COPY --from=builder /app/.next /usr/share/nginx/html/.next
COPY --from=builder /app/public /usr/share/nginx/html

# Espone la porta 80
EXPOSE 80

# Avvia NGINX
CMD ["nginx", "-g", "daemon off;"]
