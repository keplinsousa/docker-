# Code_Server

### Descrição do Projeto

Este projeto configura um ambiente de desenvolvimento remoto utilizando o  [code-server](https://github.com/coder/code-server) dentro de um container Docker. O code-server permite que você acesse um editor de código (Visual Studio Code) diretamente do navegador, facilitando o desenvolvimento em servidores remotos.

### Estrutura do Projeto
```shel
        code_server
        ├── config.yaml
        ├── Dockerfile
        └── README.md
```
- **Dockerfile**: Define a configuração do ambiente Docker para o code-server.
- **config.yaml**: Arquivo de configuração personalizado para o code-server.
- **README.md**: Documentação do projeto.

### Pré-requisitos

- Docker instalado no seu sistema.
- Acesso a um servidor remoto ou ambiente local para executar o container.

### Como Usar
#### 1. Clonando o Repositório
```shel
git clone https://github.com/keplinsousa/code_server_com_docker.git
cd repositorio
```

#### 2. Configurações
Edite o arquivo **config.yaml** para definir a senha de acesso ao code-server:
```yaml
bind-addr: 0.0.0.0:8080
auth: password
password: "YOUR_PASSWORD_HERE"
cert: false
```

#### 3. Construir a Imagem Docker
No diretório do projeto, execute o seguinte comando para construir a imagem Docker:
```shel
docker build -t code-server .
```


#### 4. Executar o Container
Depois de construir a imagem, você pode rodar o container com o seguinte comando:
```shel
docker run -d -p 8080:8080 -v /caminho/para/seus/projetos:/home/coder/projects --name code_server meu_code_server
```

#### 5. Acessar o Code-Server
```shel
http://localhost:8080
```

Caso não tenha permissão para criar pasta/documentos, rodar o seguinte comando:
```shel
sudo chmod -R 777 /home/coder/projects
```

#### 6. Parar o Container
Para parar o container, use:
```shel
docker stop code_server
```
E para removê-lo:
```shel
docker rm code_server
```

### Contribuições
Contribuições são bem-vindas! Sinta-se à vontade para abrir issues ou enviar pull requests.