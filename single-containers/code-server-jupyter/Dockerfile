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

# Cria um usuário "ubuntu"
RUN useradd -m -s /bin/bash ubuntu && \
    echo "ubuntu ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# Troca para o novo usuário
USER ubuntu    

# Define o diretório de trabalho para os projetos
WORKDIR /home/ubuntu/projects

# Instalar o Code-Server (VS Code Server)
RUN curl -fsSL https://code-server.dev/install.sh | sh

# Copia o arquivo de configuração para o local adequado
COPY --chown=ubuntu:ubuntu config.yaml /home/ubuntu/.config/code-server/config.yaml

# Expõe a porta padrão do code-server
EXPOSE 8080

# Comando para iniciar o code-server sem usuário extra
CMD ["code-server", "--bind-addr", "0.0.0.0:8080"]
