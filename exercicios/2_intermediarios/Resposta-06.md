## Resposta Exercicio 06 -     Multi Stage Build 
```bash
🐳 Dockerfile.slim (imagem simples)
dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --upgrade pip && pip install -r requirements.txt
COPY . .
CMD ["python", "app.py"]
```
```bash
🐳 Dockerfile (multi-stage: build + runtime)
dockerfile
# Etapa 1: Build
FROM python:3.11-slim AS builder
WORKDIR /app
COPY requirements.txt .
RUN pip install --upgrade pip && pip install -r requirements.txt
COPY . .

# Etapa 2: Runtime
FROM python:3.11-alpine AS runtime
WORKDIR /app
COPY --from=builder /app .
CMD ["python", "app.py"]

```
```bash
🚀 Comandos para construir
Imagem Slim (sem multi-stage):

docker build -t python-slim-app -f Dockerfile.slim .

Imagem Build (primeira etapa):

docker build -t python-build-app --target builder -f Dockerfile .

Imagem Runtime (final multi-stage):

docker build -t python-runtime-app -f Dockerfile .

▶️ Comandos para rodar
Slim:

docker run --rm python-slim-app

Build (não tem CMD por padrão, então forçamos a saída):

docker run --rm python-build-app python app.py

Runtime:

docker run --rm python-runtime-app
Saída esperada em todos os casos:

Código
Hello Multi-Stage Build!
```
```bash
🔍 Comparação de imagens
docker images
```
```bash
Explicação

✅ O que os alunos devem aprender
A imagem slim e a build são pesadas (~120 MB).

A imagem runtime é bem menor (~50 MB).

A etapa build serve para instalar dependências e rodar testes, mas não é usada em produção.

A etapa runtime é a que deve ser usada em produção, pois é enxuta e contém apenas o necessário.
```


