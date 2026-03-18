# Resposta Exercicio 2: 

# 1. Execute o comando:

```
docker run -d -p 8080:80 docker/welcome-to-docker
```

```
docker run -d: executa o docker em segundo plano
-p 8080:80 : expõe as portas necessárias
docker/welcome-to-docker: baixa uma imagem do docker
```

# 2. Verifique se o container está sendo executado:

```
docker ps
```

# 3. Verifique se está sendo executado no browser:

```
http://localhost:8080
```

# 4. Pare a execução do container:

```
docker stop <the-container-id>
```
