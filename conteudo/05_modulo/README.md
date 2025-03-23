
# Exercício Prático: Redes no Docker

Este guia mostra como criar uma **rede personalizada** no Docker, conectar dois containers a ela e testar a comunicação entre eles usando `ping`.

## 1. Criando uma Rede Personalizada

Use o comando abaixo para criar uma rede chamada `minharede`:

```bash
docker network create minharede
```

Você pode verificar a rede criada com:

```bash
docker network ls
```

## 2. Executando Dois Containers na Mesma Rede

Inicie dois containers com nomes distintos e conectados à rede `minharede`:

```bash
docker run -dit --name container1 --network minharede ubuntu
docker run -dit --name container2 --network minharede ubuntu
```

Esses containers estarão rodando com o Ubuntu em modo interativo (`-it`) e em segundo plano (`-d`).

## 3. Acessando um dos Containers

Acesse o terminal do primeiro container:

```bash
docker exec -it container1 bash
```

## 4. Testando a Comunicação com `ping`

Dentro do `container1`, use o comando `ping` para testar a comunicação com o `container2`:

```bash
ping container2
```

Você verá respostas indicando que os containers estão se comunicando corretamente.

Para sair do terminal, pressione `Ctrl+C` e depois digite:

```bash
exit
```

## 5. Limpando os Recursos (opcional)

Após os testes, você pode remover os containers e a rede:

```bash
docker rm -f container1 container2
docker network rm minharede
```