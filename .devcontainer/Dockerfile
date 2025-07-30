# https://hub.docker.com/r/ollama/ollama
# docker run -d -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama

# Base image
FROM python:3.10-slim-buster
# FROM ollama/ollama

# Set environment variables
# ENV 

# Install system dependencies
RUN apt-get update && apt-get install -y --no-install-recommends

# Create a non-root user and add to sudoers
# RUN groupadd -g 1000 user && \
#     useradd -m -u 1000 -g 1000 -s /bin/bash user && \
#     echo "user ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# Ensure the user owns their home directory
# RUN chown -R user:user /home/user

# Set working directory
WORKDIR /contAInerWorkspace

# Copy the requirements file into the container
COPY requirements.txt .

# Install the dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application code into the container
COPY . .

# Download model and tokenizer (adjust based on your chosen model)
RUN python -c "from transformers import AutoTokenizer, AutoModelForCausalLM; AutoTokenizer.from_pretrained('google/gemma-2b'); AutoModelForCausalLM.from_pretrained('google/gemma-2b')"

# Command to run the application
CMD ["python", "main.py"]

# Switch to non-root user
# USER user

# Expose application ports
# EXPOSE 8081 4002
