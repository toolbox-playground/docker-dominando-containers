## Objetivo
Compreender como funciona a persistência de dados em containers utilizando volumes no Docker.

## Descrição do desafio
Você deverá criar um ambiente com um banco de dados em container e validar o comportamento dos dados em dois cenários:
- Sem utilização de volume
- Com utilização de volume
O objetivo é observar o que acontece com os dados quando o container é removido e recriado.


# Requesitos 
- Subir um container com um banco de dados (ex: PostgreSQL)
- Criar um banco, tabela e inserir dados
- Remover o container e subir novamente sem volume
- Validar o comportamento dos dados
- Criar um volume Docker
- Subir o mesmo banco utilizando o volume
- Repetir o processo de criação de dados
- Remover e recriar o container utilizando o mesmo volume
- Validar se os dados permanecem

# Resolução

1. Rodar um container com PostgreSQL (SEM volume)

```
docker run -d \
  --name meu-postgres \
  -e POSTGRES_PASSWORD=1234 \
  -p 5432:5432 \
  postgres
```

2. Acessar o banco de dados

```docker exec -it meu-postgres psql -U postgres```

3. Criar banco

```CREATE DATABASE teste;```

4. Conectar

```\c teste```

5. Criar tabela
```
CREATE TABLE usuarios (
  id SERIAL PRIMARY KEY,
  nome TEXT
);
```

6. Inserir dado

```INSERT INTO usuarios (nome) VALUES ('testando');```

7. Validar

```SELECT * FROM usuarios;```

8. Remover o container

```docker rm -f meu-postgres```

9. Subir novamente o container (SEM volume)

```
docker run -d \
  --name meu-postgres \
  -e POSTGRES_PASSWORD=1234 \
  -p 5432:5432 \
  postgres

```

10. Acessar novamente o banco

```docker exec -it meu-postgres psql -U postgres```

11. Verificar os dados
```\l```

O banco teste NÃO estará lá
Os dados foram perdidos, porque o container foi removido e os dados estavam dentro dele.


# Solução com Volume

 1. Criar um volume
