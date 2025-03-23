# Docker

Este guia contém instruções simples para testar o funcionamento do Docker localmente utilizando a imagem oficial do **nginx**.

## 1. Verificando as Imagens Locais

Antes de começar, veja quais imagens já estão disponíveis no seu Docker:

```bash
docker images
```

## 2. Baixando a Imagem do NGINX

Baixe a imagem oficial do nginx:

```bash
docker pull nginx
```

## 3. Iniciando um Container com o NGINX

Execute um container em segundo plano (modo *detached*) e exponha a porta 80 do container na porta 8080 do host:

```bash
docker run -d -p 8080:80 nginx
```

## 4. Verificando se o Servidor Está Funcionando

Abra o navegador e acesse:

```
http://localhost:8080
```

Você deverá ver a página padrão do nginx.

## 5. Listando os Containers

Veja os containers em execução:

```bash
docker ps
```

Veja todos os containers (inclusive os parados):

```bash
docker ps -a
```

## 6. Parando e Removendo o Container

Identifique o `CONTAINER ID` do nginx e execute:

```bash
docker stop <CONTAINER_ID>
docker rm <CONTAINER_ID>
```

Substitua `<CONTAINER_ID>` pelo ID correspondente.

## 7. Removendo a Imagem do NGINX

Após os testes, você pode remover a imagem local do nginx:

```bash
docker rmi <IMAGE_ID>
```

Substitua `<IMAGE_ID>` pelo ID da imagem nginx.
