# Exercício 7 - Sua imagem Docker com aplicação Flask


Você acaba de entrar no time de desenvolvimento do Bentão e sua primeira tarefa é criar um container Docker para a nova aplicação Flask da empresa. O time de infraestrutura disponibilizou o código da aplicação e pediu para você containerizar e publicar no Docker Hub para que outros times possam testar.


**Sua missão:**

```bash

* Faça um git clone do repositório: https://github.com/JuGalvaoMiyaki/docker_base

* Criar um Dockerfile profissional para esta aplicação Flask

* Construir a imagem localmente com a tag: seu-usuario-dockerhub/bentao-flask:1.0

* Executar e testar a aplicação localmente

* Publicar a imagem no Docker Hub para toda a equipe acessar

* Documentar todos os comandos utilizados
```

**📋 Regras e dicas:**
```bash
Use uma imagem base leve e segura (Python 3.9 slim é uma boa escolha)

Lembre-se de expor a porta correta (5000)

O container deve ficar em execução contínua (o Flask já faz isso por padrão)

Teste localmente ANTES de publicar

Substitua seu-usuario-dockerhub pelo seu nome de usuário real
```