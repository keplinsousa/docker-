# VS Code Server com Jupyter Notebook em Container Docker

Este repositório contém o Dockerfile para um container que executa o VS Code Server com suporte ao Jupyter Notebook. O container é baseado na imagem `ubuntu:20.04`, com o Code-Server e Jupyter instalados globalmente, permitindo que você gerencie múltiplos projetos isoladamente com ambientes virtuais.

## Recursos

- VS Code Server acessível via navegador.
- Jupyter Notebook integrado ao VS Code Server.
- Configuração de autenticação por senha para acesso seguro.
- Suporte para múltiplos projetos com ambientes virtuais independentes.

## Estrutura do Projeto

- `Dockerfile`: Define a imagem do container, incluindo instalação do Code-Server, Jupyter, Python, e dependências necessárias.
- `config.yaml`: Arquivo de configuração do Code-Server, incluindo as definições de autenticação e porta.

## Configuração e Uso

### Pré-requisitos

- **Docker**: Certifique-se de ter o Docker instalado no sistema. [Instalar Docker](https://docs.docker.com/get-docker/)

### Configuração do Arquivo `config.yaml`

No arquivo `config.yaml`, personalize a senha de autenticação do VS Code Server.

```yaml
bind-addr: 0.0.0.0:8080
auth: password
password: "YOUR_PASSWORD"  # Substitua YOUR_PASSWORD pela senha desejada
cert: false
