## Resposta Exercicio 7- Contendo uma aplicação maliciosa.
```bash
dockerfile
FROM python:3.11-slim

# Criar usuário não-root para versão segura
RUN useradd -m appuser

WORKDIR /app
COPY app.py .

# Por padrão roda como root (para comparação)
CMD ["python", "-u", "app.py"]
```
**Construir aplicação**

```bash
docker build -t app-maliciosa . 
```

**Rodar aplicação**

*Executar SEM Restrições (Cenário Perigoso)*

```bash

# Rodar sem nenhuma restrição
docker run -d --name app-sem-limites app-maliciosa
```

```bash
##Monitaramento e Logs

*Roda como root (perigoso)

*Tem todas as capacidades do kernel

*Pode consumir toda memória do host


# Monitorar consumo
docker stats app-sem-limites

# Ver logs
docker logs -f app-sem-limites
```

*Executar COM Restrições - Passo a Passo*
```bash

* Garantir que não rode como root

# Adicionar --user appuser
docker run -d --name app-nao-root --user appuser app-maliciosa

*Verificar:


docker exec app-nao-root whoami
# Saída: appuser (não é root!)
```

*Remover capacidades do kernel*

```bash
# Adicionar --cap-drop=ALL (remove todas capacidades)
docker run -d --name app-sem-cap --user appuser --cap-drop=ALL app-maliciosa
```

*Adicionar limites de memória*

```bash
# Adicionar --memory e --memory-swap
docker run -d --name app-com-memoria --user appuser --cap-drop=ALL --memory="256m" --memory-swap="256m" app-maliciosa
```

*Adicionar limites de CPU*

```bash

# Adicionar --cpus
docker run -d --name app-completo --user appuser --cap-drop=ALL --memory="256m" --memory-swap="256m" --cpus="0.5" app-maliciosa
```

*Monitorar ambos os containers:*

```bash
# Ver consumo de recursos
docker stats app-sem-limites app-completo


#Ver logs:

# Sem restrições - vai consumir até o host travar * Ctrl+C para sair *
docker logs -f app-sem-limites

# Com restrições - vai ser morto ao atingir 256MB
docker logs -f app-segura

```

**Desafio 1: Teste de Memória**

```bash

# Container será morto ao estourar 128MB
docker run --rm --memory="128m" --memory-swap="128m" app-maliciosa
```

**Desafio 2: Teste de CPU**

```bash

#2. Rodar com limite de CPU
docker run -d --cpus="0.25" --name test-cpu app-maliciosa

#2.1 Verificar uso (deve ficar em 25%)
docker stats test-cpu

#2.2 Limpar
docker stop test-cpu && docker rm test-cpu
```

**Desafio 3: Limpeza e Remoção**

```bash
Limpeza

# Parar containers
docker stop app-sem-limites app-completo

# Remover containers
docker rm app-sem-limites app-completo

# Remover imagem
docker rmi app-maliciosa
```

