# Construindo e Executando sua Própria Imagem Docker

Este guia mostra como criar sua própria imagem Docker a partir de um `Dockerfile` e executar um container baseado nela.

## 1. Criando o Dockerfile

Antes de tudo, crie um arquivo chamado `Dockerfile` no diretório do seu projeto.

Exemplo básico de `Dockerfile` com NGINX:

```Dockerfile
FROM nginx:latest
COPY index.html /usr/share/nginx/html/index.html
```

Também crie um arquivo `index.html` com o conteúdo desejado para exibir no navegador.

## 2. Construindo a Imagem Docker

No terminal, estando no mesmo diretório do `Dockerfile`, execute:

```bash
docker build -t minha-imagem .
```

- O `-t minha-imagem` define o nome da imagem.
- O `.` indica que o contexto de build é o diretório atual.

## 3. Rodando um Container com a Imagem Criada

Depois que a imagem for criada com sucesso, execute um container baseado nela:

```bash
docker run -d -p 8080:80 minha-imagem
```

- O `-d` executa o container em segundo plano.
- O `-p 8080:80` mapeia a porta 80 do container para a porta 8080 do host.

## 4. Acessando no Navegador

Abra o navegador e acesse:

```
http://localhost:8080
```

Você verá o conteúdo da sua página `index.html`.

## 5. Verificando Containers e Imagens

Veja os containers em execução:

```bash
docker ps
```

Veja todas as imagens:

```bash
docker images
```