# Usando a imagem base oficial do code-server
FROM codercom/code-server:latest

# Crie um diretório de trabalho
WORKDIR /home/coder/projects

# Copie o arquivo de configuração personalizado para o code-server
COPY config.yaml /home/coder/.config/code-server/config.yaml

# Exponha a porta padrão do code-server
EXPOSE 8080

# Inicie o code-server
CMD ["code-server", "--bind-addr", "0.0.0.0:8080", "/home/coder/projects"]