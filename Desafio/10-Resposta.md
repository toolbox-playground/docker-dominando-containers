# Resposta Exercicio 10 - Comandos Dentro de um Container

**Arquivo Dockerfile:**
```bash
dockerfile
FROM python:3.9-slim

WORKDIR /app
COPY app.py /app

RUN pip install flask

CMD ["python", "app.py"]
```

**Resposta Esperada**
```bash
Passo 1 – Criar a imagem:

docker build -t flask-app .

Passo 2 – Iniciar o contêiner em segundo plano:

docker run -d --name meu_flask -p 5000:5000 flask-app

Passo 3 – Verificar se o contêiner está rodando:

docker ps

Passo 4 – Executar comandos dentro do contêiner:

Abrir um shell:
docker exec -it meu_flask bash

Listar arquivos:
ls /app

Verificar versão do Python:
python --version

Criar um arquivo dentro do contêiner
docker exec meu_flask bash -c "echo 'Teste dentro do container' > /app/teste.txt"

Ler o conteúdo criado dentro do container
docker exec meu_flask cat /app/teste.txt

Parar o contêiner:
docker stop meu_flask
```


