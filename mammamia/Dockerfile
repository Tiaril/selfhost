#Use an official Python runtime as a parent image
FROM python:3.11-slim-bullseye

# Set the working directory in the container to /app
WORKDIR /app

# Install git + tesseract
RUN apt-get update && \
    apt-get install -y tesseract-ocr libtesseract-dev git && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Clone the repository
RUN git clone --branch main https://github.com/Tiaril/MammaMia .

# ❌ RIMOSSO: ADD esterno (causa 404)
# ADD https://raw.githubusercontent.com/nihon77/stremio-selfhosted/... update_domains.py

# Install Python deps
RUN pip install --no-cache-dir -r requirements.txt
RUN pip install --no-cache-dir pytesseract

EXPOSE 8080

# Run startup scripts
CMD python update_domains.py && python run.py

