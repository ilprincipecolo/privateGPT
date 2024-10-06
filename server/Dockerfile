# Usa l'immagine Python
FROM python:3.9-slim

# Imposta la directory di lavoro
WORKDIR /app

# Aggiorna pip
RUN pip install --upgrade pip

# Installa dipendenze di sistema per compilare i pacchetti
RUN apt-get update && apt-get install -y \
    build-essential \
    cmake \
    g++ \
    libc++-dev \
    libopenblas-dev

# Copia i requisiti del progetto
COPY requirements.txt .

# Installa le dipendenze
RUN pip install --no-cache-dir -r requirements.txt

# Copia il codice dell'app
COPY . .

# Aggiungi ENV per il modello
ENV PERSIST_DIRECTORY=/db
ENV MODEL_TYPE=gpt4All
ENV MODEL_PATH=model/ggml-gpt4all-j-v1.3-groovy.bin
ENV EMBEDDINGS_MODEL_NAME=all-MiniLM-L6-v2
ENV MODEL_N_CTX=1000

# Espone la porta del backend (ad esempio 5000)
EXPOSE 5000

# Comando per avviare l'applicazione
CMD ["python", "privateGPT.py"]
