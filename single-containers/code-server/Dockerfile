# Imagem base
FROM ubuntu:22.04

# Atualiza o sistema e instala dependências
RUN apt update -y && apt upgrade -y && \
    apt install -y curl sudo

# Cria um usuário "ubuntu"
RUN useradd -m -s /bin/bash ubuntu && \
    echo "ubuntu ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# Troca para o novo usuário
USER ubuntu

# Define o diretório de trabalho para os projetos
WORKDIR /home/ubuntu/projects

# Baixa e instala o code-server (agora como usuário ubuntu)
RUN curl -fsSL https://code-server.dev/install.sh | sh

# Copia o arquivo de configuração para o local adequado
COPY --chown=ubuntu:ubuntu config.yaml /home/ubuntu/.config/code-server/config.yaml

# Expõe a porta do code-server
EXPOSE 4277

# Comando para iniciar o code-server
CMD ["code-server", "--bind-addr", "0.0.0.0:4277"]
