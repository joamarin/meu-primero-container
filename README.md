
# Minha Primeira Aplicação em Contêineres com Docker

Este projeto demonstra como criar, executar e compartilhar uma aplicação em contêiner usando Docker.

---

## Pré-requisitos

Antes de começar, certifique-se de que você tem os seguintes programas instalados:

1. **Docker Desktop**: [Baixe aqui](https://www.docker.com/get-started/)
2. **Git**: [Baixe aqui](https://git-scm.com/)
3. **Conta no Docker Hub**: [Crie aqui](https://hub.docker.com/)
4. **Conta no GitHub**: [Crie aqui](https://github.com/)

---

## Passo a Passo

### 1. Clonar o Repositório da Aplicação
Baixe o código da aplicação de exemplo
Fonte original do código: https://docs.docker.com/get-started/
```bash
git clone https://github.com/docker/getting-started-app.git
```

---

### 2. Criar o Dockerfile
No diretório da aplicação, crie um arquivo chamado `Dockerfile` com o seguinte conteúdo:
```dockerfile
FROM node:lts-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]
EXPOSE 3000
```

---

### 3. Construir a Imagem Docker
Gere a imagem Docker a partir do `Dockerfile`:
```bash
docker build -t getting-started .
```

---

### 4. Listar Imagens Criadas
Verifique se a imagem foi criada:
```bash
docker images
```

---

### 5. Executar o Contêiner
Inicie o contêiner com a aplicação:
```bash
docker run -it -p 3000:3000 getting-started
```
Acesse a aplicação em: [http://localhost:3000](http://localhost:3000)

---

### 6. Renomear a Imagem para o Docker Hub
Renomeie a imagem para o formato esperado pelo Docker Hub:
```bash
docker tag getting-started:latest jcamar/meu_primeiro_docker:latest
```

---

### 7. Fazer Login no Docker Hub
Autentique-se na sua conta Docker Hub:
```bash
docker login
```

---

### 8. Enviar a Imagem para o Docker Hub
Suba a imagem para o Docker Hub:
```bash
docker push jcamar/meu_primeiro_docker:latest
```

---

### 9. Baixar Imagem do Docker Hub
Colegas podem baixar a imagem com:
```bash
docker pull jcamar/meu_primeiro_docker:latest
```

---

### 10. Executar Imagem Baixada
Depois de baixar, os colegas podem executar a imagem:
```bash
docker run -d -p 8080:80 jcamar/meu_primeiro_docker:latest
```

---

### 11. Exportar Imagem como Arquivo `.tar`
Salve a imagem como um arquivo `.tar` para compartilhamento manual:
```bash
docker save -o getting_started.tar getting-started:latest
```

---

## Finalização

Siga estas etapas para preparar, compartilhar e executar sua aplicação em contêiner. Este projeto abrange conceitos fundamentais do Docker, incluindo a criação de imagens, execução de contêineres e compartilhamento de aplicações.

Para mais informações, consulte a [Documentação do Docker](https://docs.docker.com/get-started/).