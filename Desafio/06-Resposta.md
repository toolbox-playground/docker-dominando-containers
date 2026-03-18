# Resposta Exericicio 6 – Criar e Publicar Imagem no Docker Hub

```bash
Parte 1 – Criar a imagem
Dockerfile (usando Alpine):

dockerfile
FROM alpine:latest

CMD echo "Bem-vindo ao Bentão!"

Construir a imagem com a tag:

docker build -t bentao/hello:1.0 .

Executar o contêiner:

docker run bentao/hello:1.0

Saída esperada no terminal:
Bem-vindo ao Bentão!

Parte 2 – Publicar no Docker Hub
Login no Docker Hub:


docker login
→ Digite seu usuário e senha do Docker Hub.

Enviar a imagem para o Docker Hub:


docker push bentao/hello:1.0
Isso publica a imagem no repositório público do usuário bentao.

Parte 3 – Testar o repositório
Remover a imagem local:

docker rmi bentao/hello:1.0

Baixar novamente do Docker Hub:

docker pull bentao/hello:1.0

Executar para testar:

docker run bentao/hello:1.0

Saída esperada novamente:
Bem-vindo ao Bentão!

Desafio:

docker run bentao/hello:1.0 echo "Testando outro comando!"
```