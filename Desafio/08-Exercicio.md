# Exercicio 8 - Dockerignore

**📖 Cenário**

O Bentão está desenvolvendo uma aplicação Flask simples. Um desenvolvedor acidentalmente fez o build da imagem incluindo arquivos que não deveriam estar lá, como o ambiente virtual e um arquivo com credenciais de teste.

**Sua missão: Criar um arquivo .dockerignore para garantir que apenas o necessário vá para a imagem Docker.**

**Clone o repositório: https://github.com/JuGalvaoMiyaki/docker_base**


**📋 Estrutura do Projeto**
```bash
text
bentao-flask-app/
├── venv/                    # Ambiente virtual (NÃO DEVE IR)
├── __pycache__/            # Cache do Python (NÃO DEVE IR)
├── .env                    # Credenciais (NÃO DEVE IR)
├── app.py                  # Aplicação Flask
├── requirements.txt
└── Dockerfile
```


**🐳 Dockerfile inicial (crie seu dockerfile)**
```bash

dockerfile - dica

# ATENÇÃO: Isso copia TUDO, inclusive venv, .env e __pycache__
COPY . .

```

**🎯 Desafio**
```bash

• Crie um arquivo .dockerignore para excluir:

• A pasta venv/ (ambiente virtual)

• A pasta __pycache__/ (cache do Python)

• O arquivo .env (credenciais sensíveis)

• Explique por que cada item deve ser excluído

• Teste se a imagem ficou menor e mais segura
    ** Construa a imagem
    ** Verifique o tamanho
    ** Execute e teste
```