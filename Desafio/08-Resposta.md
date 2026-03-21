 # Resposta Exercício 8 - Dockerigonre - Solução


**📝 Arquivo .dockerignore**

```bash
venv/
__pycache__/
.env
*.pyc
    
dockerignore
# Ambiente virtual (grande e desnecessário)
venv/

# Cache do Python
__pycache__/
*.pyc

# Credenciais e configurações sensíveis
.env

# Arquivos do sistema (opcional)
.DS_Store
```
**🐳 Dockerfile corrigido**
```bash

dockerfile
FROM python:3.9-slim

WORKDIR /app

# Copia apenas os arquivos necessários
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copia o código (o .dockerignore já excluiu o que não presta)
COPY app.py .

EXPOSE 5000

CMD ["python", "app.py"]
```

**🛡️ Por que excluir cada item?**
```bash

Item	Problema	Motivo
venv/	Tamanho	Ambiente virtual local com dependências (a imagem vai instalar as dela)
__pycache__/	Desnecessário	Arquivos compilados do Python, não precisam estar na imagem
.env	SEGURANÇA	Contém senhas e chaves que não devem ser expostas
*.pyc	Desnecessário	Arquivos compilados do Python
```

**📊 Comandos para testar**
```bash


# 1. Construir a imagem
docker build -t bentao/flask-app .

# 2. Verificar o tamanho
docker images bentao/flask-app

# 3. Executar e testar
docker run -p 5000:5000 bentao/flask-app

```

**🎯 Resultado esperado**

```bash
$ docker run -p 5000:5000 bentao/flask-app
 * Serving Flask app 'app'
 * Running on http://0.0.0.0:5000

$ curl http://localhost:5000
🐳 Bem-vindo ao Bentão Flask! 🐳

$ curl http://localhost:5000/saudacao/Maria
Olá Maria, tudo bem?
```