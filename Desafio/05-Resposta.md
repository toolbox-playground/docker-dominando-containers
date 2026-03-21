# Resposta do Exercício 5 - Crie um container com base em Flask

**Parte 1:**


Dockerfile exemplo
# Usar imagem base oficial do Python
FROM python:3.10-slim

# Definir diretório de trabalho dentro do container
WORKDIR /app

# Copiar o arquivo requirements.txt e instalar as dependências
COPY requirements.txt /app/
RUN pip install -r requirements.txt

# Copiar o código da aplicação para o container
COPY app.py /app/

# Expor a porta 5000 para acesso externo
EXPOSE 5000

# Comando para rodar a aplicação Flask
CMD ["python", "app.py"]

**Parte 2:**

**Construir e rodar o container**

1. Construir a imagem Docker
```bash
docker build -t flask-ola-mundo .
```
2. Rodar o container mapeando a porta 5000
```bash
docker run -p 5000:5000 flask-ola-mundo
```
3. Testar no navegador
Acesse o endereço:

text
http://localhost:5000/

**Parte 3:**

**Modificar a mensagem**
```
Altere a mensagem no arquivo app.py para "Olá, Docker!"
```

**Reconstrua a imagem para aplicar a alteração:**

```bash
docker build -t flask-ola-mundo .
```
**Testar a flag --rm**

```bash
docker run --rm -p 5000:5000 flask-ola-mundo
```

**Modo detached (segundo plano)**

```bash
docker run -d -p 5000:5000 flask-ola-mundo
```
**Liste os containers em execução:**

```bash
docker ps
```
**Pare o container usando o ID exibido no comando anterior:**

```bash
docker stop <container_id>
```