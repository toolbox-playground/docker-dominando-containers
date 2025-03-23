# Boas Práticas com Docker

Este guia mostra como analisar imagens Docker, otimizar um `Dockerfile` para reduzir o tamanho da imagem e executar containers com um usuário não-root por segurança.

---

## 1. Analisando uma Imagem com `docker inspect`

Use o `docker inspect` para obter **detalhes estruturais** da imagem (configurações, camadas, volumes, etc):

```bash
docker inspect nginx
```

Esse comando retorna um JSON com metadados da imagem/container.

---

## 2. Visualizando o Histórico de Camadas com `docker history`

Veja como a imagem foi construída camada por camada:

```bash
docker history nginx
```

Isso mostra o tamanho e a instrução Dockerfile usada em cada camada.

---

## 3. Melhorando um Dockerfile

### Dockerfile original (ineficiente):

```Dockerfile
FROM node:18

RUN apt update
RUN apt install -y curl
RUN mkdir /app
COPY . /app
RUN cd /app && npm install
```

### Dockerfile otimizado (menos camadas e tamanho menor):

```Dockerfile
FROM node:18

RUN apt update && apt install -y curl && rm -rf /var/lib/apt/lists/*

WORKDIR /app
COPY . .
RUN npm install
```

> 🔎 Dicas:
> - Combine comandos `RUN` para reduzir camadas.
> - Use `WORKDIR` ao invés de `cd`.
> - Remova caches de pacotes (`apt` ou `npm`) quando possível.

---

## 4. Executando Container sem Permissões Root

### Criando um Dockerfile com usuário não-root:

```Dockerfile
FROM node:18

# Cria um usuário de aplicação
RUN useradd -m appuser

# Define o diretório de trabalho
WORKDIR /app

# Copia os arquivos da aplicação
COPY . .

# Instala as dependências
RUN npm install

# Muda para o usuário não-root
USER appuser

CMD ["node", "index.js"]
```

---

## 5. Validando Permissões Dentro do Container

Rode o container:

```bash
docker build -t minha-app .
docker run -it minha-app bash
```

Dentro do container, verifique o usuário atual:

```bash
whoami
```

A saída deve ser:

```
appuser
```

E verifique se não é root:

```bash
id
```

O UID deve **ser diferente de 0** (UID 0 = root).
