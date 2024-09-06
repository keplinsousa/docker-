# MinIO Docker Compose Setup

Este diretório contém a configuração do MinIO usando Docker Compose, que permite criar um serviço de armazenamento S3 em contêiner para desenvolvimento.

## Configuração do Compose

O `docker-compose.yml` foi configurado para subir um container com o MinIO e um console de gerenciamento.

### Estrutura

-   **Imagem**: `minio/minio:latest`
-   **Serviço**: MinIO com console de administração
-   **Volumes**: Volume persistente para dados em `/data`
-   **Rede**: Usando rede `minio_default` para comunicação entre containers

### Variáveis de Ambiente

-   `MINIO_ACCESS_KEY`: Chave de acesso usada para autenticação. 
-   `MINIO_SECRET_KEY`: Chave secreta usada para autenticação.

### Exposição de Portas

-   Porta `9000`: Porta do servidor MinIO (não exposta externamente neste exemplo, mas pode ser adicionada se necessário).
-   Porta `9001`: Porta do console do MinIO, exposta no host para gerenciamento da interface de administração.

### Volumes
O volume persistente `minio-data` está sendo utilizado para garantir que os dados armazenados no MinIO não sejam perdidos quando o container for interrompido ou reiniciado.

### Rede

A rede `minio_default` está configurada com o driver `bridge` para isolar o tráfego do container e permitir comunicação com outros serviços na mesma rede.

## Como Usar

### Inicializando o MinIO

Para iniciar o MinIO usando o `docker-compose.yml` fornecido:
``` shel
docker-compose up -d
```
Isso iniciará o container em segundo plano.

### Acessando o Console de Administração

Uma vez que o serviço esteja em execução, o console de administração pode ser acessado no navegador através da URL:
```shel
http://localhost:9001
```

### Parando o MinIO

Para parar e remover o container MinIO:
```shel
docker-compose down
```

Isso desligará o container e manterá os dados armazenados no volume persistente.