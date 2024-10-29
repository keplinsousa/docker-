# Portainer Docker Compose Setup

Este diretório contém a configuração do Portainer utilizando Docker Compose, que fornece uma interface gráfica para gerenciar contêineres Docker.

## Configuração do Compose

O `docker-compose.yml` está configurado para iniciar um container com o Portainer Community Edition (CE), uma ferramenta para gerenciamento de contêineres Docker.

### Estrutura

-   **Imagem**: `portainer/portainer-ce`
-   **Serviço**: Portainer para gerenciamento de containers via interface gráfica
-   **Volumes**: Volume persistente para os dados do Portainer
-   **Portas**: A interface gráfica do Portainer é acessível via porta 9003

### Exposição de Portas

-   **Porta 9000 (no container)**: Porta padrão do Portainer CE.
-   **Porta 9003 (no host)**: Porta mapeada no host, através da qual o Portainer pode ser acessado no navegador.

### Volumes

-   `/var/run/docker.sock:/var/run/docker.sock`: Volume necessário para que o Portainer se comunique com o Docker Engine no host.
-   `portainer_data:/data`: Volume persistente que armazena os dados do Portainer, incluindo informações sobre os contêineres gerenciados.

### Reinício Automático

O Portainer está configurado com a política de reinício `always`, garantindo que ele seja reiniciado automaticamente em caso de falha ou quando o Docker for reiniciado.

## Como Usar

### Inicializando o Portainer

Para iniciar o Portainer com o `docker-compose.yml` fornecido:
```shel
docker-compose up -d
```
Isso iniciará o container em segundo plano.

### Acessando o Portainer

Uma vez que o serviço esteja em execução, o Portainer pode ser acessado no navegador via:
```shel
http://localhost:9003
```
Na primeira vez que você acessar, será solicitado que você crie um usuário administrador.

### Parando o Portainer

Para parar e remover o container do Portainer:
```shel
docker-compose down
```
Os dados do Portainer, incluindo as configurações e os registros de contêineres, serão mantidos no volume persistente.