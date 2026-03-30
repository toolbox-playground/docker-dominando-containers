## Objetivo
Compreender como orquestrar múltiplos containers (aplicação + banco de dados) utilizando Docker Compose, garantindo comunicação entre serviços e persistência de dados.

## Descrição do desafio
Você deverá criar um ambiente completo contendo:
Uma aplicação (backend simples)
Um banco de dados (ex: PostgreSQL)
A aplicação deve se conectar ao banco utilizando o nome do serviço, e não IP.
Além disso, os dados do banco devem permanecer mesmo após a recriação dos containers.

# Requesitos 
- Utilizar Docker Compose para subir os serviços
- Criar pelo menos dois serviços:
aplicação
banco de dados
- Garantir que os containers estejam na mesma rede
- Configurar variáveis de ambiente para conexão com o banco
- Utilizar o nome do serviço do banco como host
- Configurar volume para persistência de dados
- Subir e derrubar o ambiente utilizando Docker Compose


# Resolução

1. Criar uma pasta do projeto

```mkdir app-docker```

2. Criar o arquivo da aplicação

Crie um arquivo app.js:

```touch app.js```

3. Adicionar código da aplicação 

```
const express = require('express');
const { Client } = require('pg');

const app = express();

const client = new Client({
  host: 'db',
  user: 'postgres',
  password: '1234',
  database: 'postgres'
});

client.connect();

app.get('/', async (req, res) => {
  const result = await client.query('SELECT NOW()');
  res.send(result.rows);
});

app.listen(3000, () => {
  console.log('App rodando na porta 3000');
});
```

4. Criar package.json

```touch package.json```

5.  Adicionar código package.json

```
{
  "name": "docker-app",
  "version": "1.0.0",
  "main": "app.js",
  "dependencies": {
    "express": "^4.18.2",
    "pg": "^8.11.0"
  }
}
```

5. Criar Dockerfile

```touch Dockerfile```

6. Adicionar Dockerfile

```
FROM node:18

WORKDIR /app

COPY package.json .
RUN npm install

COPY . .

CMD ["node", "app.js"]
```

 7. Criar docker-compose.yml

```touch docker-compose.yml```

8. Adicionando docker-compose.yml

```
version: '3.8'

services:
  app:
    build: .
    ports:
      - "3000:3000"
    depends_on:
      - db

  db:
    image: postgres
    environment:
      POSTGRES_PASSWORD: 1234
    volumes:
      - pgdata:/var/lib/postgresql
    ports:
      - "5433:5432"

volumes:
  pgdata:
```

# Rodando o projeto

