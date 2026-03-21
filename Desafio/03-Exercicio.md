# Exercicio 3 - Hello World em Docker.

Dizem que todos que estão começando a aprender algo em desenvolvimento deve realizar
um exercício com o famoso Hello World para não ficar amaldiçoado no seu aprendizado. 

Vamos executar um Hello World em Docker?

**1. Baixe o seguinte repositório em git:**

```
https://github.com/JuGalvaoMiyaki/hello-world
```

**2. Crie um arquivo Dockerfile:**

```
# Usar uma imagem base do Python
FROM python:3.10-slim

# Definir diretório de trabalho
WORKDIR /app

# Copiar os arquivos do repositório para dentro da imagem
COPY . /app

# Comando padrão para rodar o programa
CMD ["python", "app.py"]

```

**3. Construa a imagem Docker:**

```
docker build -t hello-world .
```

**4. Execute o Container.**

```
docker run --name <nome-do-container> hello-world

```

**5. Verifique a saída.**

**6. Altere o nome do arquivo onde está o código Hello-World para meu-app.py**

**7. Altere a mensagem de Hello World para : "Hello, <insira seu nome> from Docker!"**

**8. Altere as configurações necessárias no Dockerfile.**

**9. Construa outro container.**

**10. Rode o container.**

**11. Tente verificar o container criado.**

**12. Tente verificar todos os containers criados.**

**13. Exclua os containers.**

**14. Exclua as imagens.**


