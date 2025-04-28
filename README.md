# nginx-docker-full-cycle
Este projeto tem como objetivo configurar e executar um servidor Nginx utilizando Docker. Abaixo está a documentação detalhada de todos os componentes do projeto:

## Estrutura do Projeto

O projeto é composto pelos seguintes arquivos e diretórios:

```
/home/etica/workspace/nginx-docker-full-cycle/
├── docker-compose.yml
├── Dockerfile
├── html/
│   └── index.html
└── README.md
```

### 1. `html/index.html`

Este arquivo contém o conteúdo HTML que será servido pelo servidor Nginx. Ele é um simples arquivo HTML que pode ser personalizado conforme necessário. Exemplo de conteúdo:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Servidor Nginx</title>
</head>
<body>
    <h1>Bem-vindo ao servidor Nginx!</h1>
</body>
</html>
```

### 2. `Dockerfile`

O `Dockerfile` é usado para criar a imagem Docker personalizada para o servidor Nginx. Ele copia os arquivos HTML para o diretório padrão do Nginx e expõe a porta 80. Exemplo de conteúdo:

```dockerfile
# Usando a imagem base do Nginx
FROM nginx:latest

# Copiando os arquivos HTML para o diretório padrão do Nginx
COPY html /usr/share/nginx/html

# Expondo a porta 80
EXPOSE 80
```

### 3. `docker-compose.yml`

O arquivo `docker-compose.yml` é usado para orquestrar o contêiner do Nginx. Ele define o serviço Nginx e mapeia a porta 80 do contêiner para a porta 8080 do host. Exemplo de conteúdo:

```yaml
version: '3.8'

services:
  nginx:
    build:
      context: .
      dockerfile: Dockerfile
    ports:
      - "8080:80"
```

## Como Executar o Projeto

Siga os passos abaixo para executar o projeto:

1. Certifique-se de ter o Docker e o Docker Compose instalados em sua máquina.
2. Navegue até o diretório do projeto:
   ```bash
   cd /home/etica/workspace/nginx-docker-full-cycle/
   ```
3. Construa e inicie os serviços usando o Docker Compose:
   ```bash
   docker-compose up --build
   ```
4. Acesse o servidor Nginx no navegador em: [http://localhost:8080](http://localhost:8080).

## Conclusão

Este projeto demonstra como configurar um servidor Nginx simples utilizando Docker e Docker Compose. Ele pode ser expandido para incluir configurações mais complexas ou outros serviços conforme necessário.
