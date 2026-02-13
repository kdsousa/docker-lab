# Imagem base
FROM ubuntu:22.04

# Atualizar pacotes e instalar dependências essenciais
RUN apt update && apt install -y \
    curl \
    wget \
    sudo \
    gnupg \
    software-properties-common \
    python3 \
    python3-pip \
    python3-venv \
    && rm -rf /var/lib/apt/lists/*

# Cria um usuário "ubuntu" e garante permissões na pasta de trabalho
RUN useradd -m -s /bin/bash ubuntu && \
    echo "ubuntu ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# Troca para o novo usuário
USER ubuntu    

# Define o diretório de trabalho
WORKDIR /home/ubuntu/notebooks

# Instalar o Code-Server
RUN curl -fsSL https://code-server.dev/install.sh | sh

# Instala o kernel do Jupyter para o Python
RUN pip3 install --no-cache-dir ipykernel

# Instala a extensão do Jupyter e Python diretamente no code-server
RUN code-server --install-extension ms-python.python
RUN code-server --install-extension ms-toolsai.jupyter

# Copia o arquivo de configuração
COPY --chown=ubuntu:ubuntu config.yaml /home/ubuntu/.config/code-server/config.yaml

# Expõe a porta
EXPOSE 8080

# Comando para iniciar
CMD ["code-server", "--bind-addr", "0.0.0.0:8080", "."]
