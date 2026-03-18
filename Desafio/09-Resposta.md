# Resposta Exercicio 9 - Modo Detetive

Passo 1: Baixar a imagem

```bash
docker pull nginx:alpine
```

Passo 2: Investigar com docker inspect

```bash
docker image inspect nginx:alpine
# Depois procure visualmente por: Os, ExposedPorts, Cmd
```
```bash
docker history nginx:alpine
# Veja a lista de camadas
```
```bash
docker images nginx:alpine
# Veja o tamanho na coluna SIZE
```

**Respostas esperadas**

```bash
SO base: Linux (Alpine)

Portas expostas: 80/tcp

Comando padrão: ["nginx", "-g", "daemon off;"]

Número de camadas: ~7 camadas

Tamanho: ~40MB
```