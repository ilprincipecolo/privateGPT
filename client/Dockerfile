# Usa l'immagine di Node.js per la build
FROM node:19

# Imposta la directory di lavoro
WORKDIR /app

# Copia i file di package.json e package-lock.json
COPY package*.json ./

# Installa le dipendenze
RUN npm install

# Copia il resto dell'applicazione
COPY . .

# Costruisci l'applicazione per la produzione
RUN npm run build

# Espone la porta 3000 per Next.js
EXPOSE 3000

# Avvia Next.js in modalità produzione
CMD ["npm", "run", "start"]
