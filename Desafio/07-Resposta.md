# Resposta do Exercício 7 - Sua imagem Docker com aplicação Flask - Passo a Passo Completo

**📁 Estrutura de arquivos**

```bash
Crie uma pasta para o projeto com esta estrutura:

text
bentao-flask/
├── app.py
├── requirements.txt
└── Dockerfile
```

**📝 Arquivo Dockerfile**
```bash
dockerfile
# Imagem base oficial do Python (versão slim para ser mais leve)
FROM python:3.9-slim

# Define o diretório de trabalho dentro do container
WORKDIR /app

# Copia apenas o requirements primeiro (aproveita cache do Docker)
COPY requirements.txt .

# Instala as dependências
RUN pip install --no-cache-dir -r requirements.txt

# Copia o código da aplicação
COPY app.py .

# Informa que a aplicação usa a porta 5000
EXPOSE 5000

# Comando para executar a aplicação
CMD ["python", "app.py"]
```

**🚀 Comandos para executar o desafio**

1. Construir a imagem (substitua seu-usuario):

```bash
docker build -t seu-usuario/bentao-flask:1.0 .
```

2. Testar localmente:

```bash
# Executar o container
docker run -p 5000:5000 seu-usuario/bentao-flask:1.0
```

3. Testar as rotas (em outro terminal):

```bash
# Testar rota principal
curl http://localhost:5000
# Deve retornar: 🐳 Bem-vindo ao Bentão! 🐳

# Testar rota com parâmetro
curl http://localhost:5000/saudacao/Maria
# Deve retornar: Olá Maria, seja bem-vindo ao Bentão Docker!

# Testar no navegador também
# Abra: http://localhost:5000
# Abra: http://localhost:5000/saudacao/João
```

4. Fazer login no Docker Hub:

```bash
docker login
# Digite seu usuário e senha quando solicitado
```
5. Publicar a imagem:

```bash
docker push seu-usuario/bentao-flask:1.0

```
