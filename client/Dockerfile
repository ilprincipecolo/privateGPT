# Usa l'immagine di Node.js
FROM node:19

# Imposta la directory di lavoro
WORKDIR /app

# Copia i file di package e package-lock
COPY package*.json ./

# Installa le dipendenze
RUN npm install

# Copia il resto dell'applicazione
COPY . .

# Costruisce l'applicazione per la produzione
RUN npm run build

# Usa un server nginx per servire il contenuto
FROM nginx:alpine

# Copia la configurazione personalizzata di NGINX
COPY ./nginx.conf /etc/nginx/conf.d/default.conf

COPY --from=0 /app/build /usr/share/nginx/html

# Espone la porta 80
EXPOSE 80

# Avvia NGINX
CMD ["nginx", "-g", "daemon off;"]

