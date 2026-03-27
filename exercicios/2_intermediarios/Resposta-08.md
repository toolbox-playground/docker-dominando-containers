## Resposta exercicio 8 - Otimização de cache layers

**🐳 Dockerfile.good (otimizado)**

```dockerfile
FROM python:3.11-slim
WORKDIR /app

# Copia apenas requirements primeiro
COPY requirements.txt dev-requirements.txt ./
RUN pip install --upgrade pip && \
    pip install -r requirements.txt && \
    pip install -r dev-requirements.txt

# Só depois copia o restante do código
COPY . .
CMD ["python", "app.py"]
```

*👉 Vantagem: se você mudar apenas o código (app.py ou test_app.py), o cache das dependências é reaproveitado.*

**Etapa 1**

```bash
docker build -t python-cache-bad -f Dockerfile.bad .
docker build -t python-cache-good -f Dockerfile.good .

docker run --rm python-cache-good
```

**Etapa 2**

```bash
docker build -t python-cache-bad -f Dockerfile.bad .
docker build -t python-cache-good -f Dockerfile.good .

```

```

🔍 O que realmente muda

Dockerfile.bad: qualquer alteração invalida o cache → reinstala dependências → build lento.

Dockerfile.good: alterações só no código reaproveitam cache das dependências → build rápido.

✅ Aprendizado

O cache de camadas só mostra diferença quando você reconstrói a imagem após pequenas alterações.

O ganho está em não repetir etapas pesadas (como instalar pacotes) se nada mudou nelas.

A saída “Using cache” no build é o indicador de que a versão otimizada foi mais rápida.
```
