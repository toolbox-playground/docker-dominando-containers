# Resposta - Exercício 4: Container com Nginx

## PARTE 1: Container com Aplicação Python

# 1. Clone o repositório
```
git clone https://github.com/JuGalvaoMiyaki/hello-world
cd hello-world
```

# 2. Crie o Dockerfile
```
Dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY . .
CMD ["python", "app.py"]
```


# 3. Construa a imagem
```
docker build -t hello-world:1.0 .
```

# 4. Mude a tag
```
docker tag hello-world-python1.0 hello-world:2.0
```

# 5. Execute o container
```
docker run --name meu-container hello-world
```

# 6. Verifique o container
```
docker ps -a
```
```bash
# Resposta: Aparece com status "Exited (0)" porque executou e saiu
```

# 7. Veja a saída
```bash
# Resposta: Mostra a mensagem do programa Python
```

## PARTE 2: Container com Nginx


# 1. Execute o nginx
```
docker run -d -p 8080:80 --name meu-nginx nginx
```

# 2. Verifique se está rodando
```
docker ps
```
```bash
# Resposta: SIM!
```
# 3. Liste todos os containers
```
docker ps -a
```
```bash
# Resposta: Mostra ambos containers (python exited e nginx up)
```
# 4. Acesse no navegador
```bash
# Abra http://localhost:8080
# Resposta: Página "Welcome to nginx!"
```

# 5. Pare o container
```
docker stop meu-nginx
```

# 6. Remova os containers
```
docker rm meu-container-python
docker rm meu-nginx

# OU
docker rm -f meu-container-python meu-nginx
```

# 7. Remova as imagens
```
docker rmi hello-world-python
```