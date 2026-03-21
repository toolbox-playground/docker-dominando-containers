# Exercicio 5 - Crie um container com base em Flask


**Clone o seguinte repositório em git:**

```
https://github.com/JuGalvaoMiyaki/hello-world
```

**PARTE 1:**

```bash
# Monte um arquivo chamado Dockerfile com base nas dicas abaixo:

# Use uma imagem base oficial do Python (exemplo: python:3.10-slim)

# Defina um diretório de trabalho dentro do container (exemplo: /app)

# Copie o arquivo requirements.txt para o container e instale as dependências usando pip    # install -r requirements.txt

# Copie o arquivo app.py para o container

# Exponha a porta 5000 (a mesma que o Flask usa)

# Defina o comando para rodar a aplicação (python app.py)
```

**PARTE 2:**

```bash

Após criar o Dockerfile, execute os seguintes comandos no terminal:

# Construir a imagem Docker:

# Rodar o container mapeando a porta 5000:

# Testar no navegador acessando:

```
```
text
http://localhost:5000/
```


**PARTE 3:**

```bash

# Modifique a mensagem no app.py para "Olá, Docker!" e reconstrua a imagem para ver a alteração refletida no navegador.

# Pare o container atual (Ctrl+C no terminal onde está rodando) e rode o container novamente # com a flag --rm para que ele seja removido automaticamente ao parar.

# Experimente rodar o container em modo "detached" (em segundo plano).

# Depois, liste os containers.

# Pare o container.

```