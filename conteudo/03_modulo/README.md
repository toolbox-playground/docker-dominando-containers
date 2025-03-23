# Testes com Volumes no Docker

## 1. Baixando a Imagem do Ubuntu

Use o comando abaixo para baixar a imagem oficial do Ubuntu:

```bash
docker pull ubuntu
```

## 2. Executando um Container Interativo

Inicie um container Ubuntu no modo interativo:

```bash
docker run -it ubuntu
```

Você entrará no terminal do container. Para sair, digite `exit`.

## 3. Criando um Volume no Docker

Crie um volume nomeado chamado `meuvolume`:

```bash
docker volume create meuvolume
```

## 4. Executando um Container com o Volume Montado

Monte o volume criado no diretório `/dados` dentro do container:

```bash
docker run -it -v meuvolume:/dados ubuntu
```

## 5. Escrevendo um Arquivo Dentro do Volume

Dentro do container, execute:

```bash
echo "Olá, volume Docker!" > /dados/mensagem.txt
cat /dados/mensagem.txt
```

Você verá o conteúdo: `Olá, volume Docker!`

## 6. Saindo e Removendo o Container

Digite `exit` para sair do container, então:

Liste os containers parados:

```bash
docker ps -a
```

Pare e remova o container usado (caso necessário):

```bash
docker rm <CONTAINER_ID>
```

## 7. Verificando a Persistência do Volume

Crie um **novo container** e monte novamente o mesmo volume:

```bash
docker run -it -v meuvolume:/dados ubuntu
```

Dentro do container, execute:

```bash
cat /dados/mensagem.txt
```
