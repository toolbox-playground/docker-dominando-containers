Claro, Thiago! Aqui está o `README.md` com um exercício completo para **criar, publicar e testar uma imagem personalizada baseada no NGINX**, seguindo o mesmo estilo de Markdown que você tem usado:

---

# Criando e Publicando uma Imagem Personalizada com NGINX

Este guia mostra como criar uma imagem Docker personalizada baseada no **NGINX**, fazer login no **Docker Hub**, publicar a imagem e testá-la em outro ambiente.

---

## 1. Criando um `Dockerfile` Personalizado

Crie um diretório e adicione os seguintes arquivos:

### `Dockerfile`
```Dockerfile
FROM nginx:latest

COPY index.html /usr/share/nginx/html/index.html
```

### `index.html`
```html
<!DOCTYPE html>
<html>
  <head>
    <title>Minha Página Personalizada</title>
  </head>
  <body>
    <h1>Olá! Esta é minha imagem NGINX personalizada.</h1>
  </body>
</html>
```

---

## 2. Construindo a Imagem

No terminal, execute o seguinte comando no diretório onde está o `Dockerfile`:

```bash
docker build -t seu-usuario/minha-nginx:1.0 .
```

Substitua `seu-usuario` pelo seu nome de usuário no Docker Hub.

---

## 3. Fazendo Login no Docker Hub

Execute o comando abaixo e forneça suas credenciais:

```bash
docker login
```

Se o login for bem-sucedido, você verá a mensagem:  
`Login Succeeded`

---

## 4. Publicando a Imagem no Docker Hub

Depois de fazer login, publique a imagem com o comando:

```bash
docker push seu-usuario/minha-nginx:1.0
```

Você poderá ver a imagem no seu repositório Docker Hub em:  
`https://hub.docker.com/r/seu-usuario/minha-nginx`

---

## 5. Testando em Outro Ambiente ou Máquina

Em outro ambiente ou máquina com Docker instalado, execute:

```bash
docker pull seu-usuario/minha-nginx:1.0
docker run -d -p 8080:80 seu-usuario/minha-nginx:1.0
```

Acesse no navegador:

```
http://localhost:8080
```

Você verá a página personalizada da sua imagem.

---

## 6. Finalizando

Para parar e remover o container:

```bash
docker ps
docker stop <CONTAINER_ID>
docker rm <CONTAINER_ID>
```

---

Se quiser, posso incluir um `docker-compose.yml` para facilitar a execução, ou adicionar autenticação para imagens privadas. Deseja isso também?