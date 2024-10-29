# Usar uma imagem base do Ubuntu
FROM ubuntu:20.04

# Definir variáveis de ambiente para evitar prompts interativos
ENV DEBIAN_FRONTEND=noninteractive

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

# Instalar o Code-Server (VS Code Server)
RUN curl -fsSL https://code-server.dev/install.sh | sh

# Criar um usuário para rodar o Code-Server
RUN useradd -m coder && echo "coder:coder" | chpasswd && adduser coder sudo
USER coder
WORKDIR /home/coder

# Instalar o Jupyter e o ipykernel globalmente
RUN pip3 install --upgrade pip \
    && pip3 install jupyter ipykernel

# Criar diretório para projetos
RUN mkdir -p /home/coder/projects

# Copiar o arquivo de configuração para o diretório do Code-Server
COPY config.yaml /home/coder/.config/code-server/config.yaml

# Expor a porta padrão do Code-Server
EXPOSE 8080

# Iniciar o Code-Server com o diretório de projetos como workspace
CMD ["code-server", "/home/coder/projects"]
