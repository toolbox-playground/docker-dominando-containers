# Exercicio 2 - Welcome to Docker.

Vamos fazer um container simples para receber as boas vindas do Docker?

**1. Abra o terminal e escreva os comando baseados em :**
* Executar um container em segundo plano ->  -d
* Expor a porta do container e do seu computador local -> 8080:80
* Imagem para executar o container: docker/welcome-to-docker


**2. Verifique se seu container está sendo executado.** 

```
docker ps
```

**3. Verifique no seu browser se sua aplicação está sendo executada.**

**4. Pare a execução do seu container.** 

```
docker stop <the-container-id>
``