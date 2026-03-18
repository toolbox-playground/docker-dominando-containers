# Exercício 6 – Criar e Publicar Imagem no Docker Hub: 

**Crie um Dockerfile**

Crie um arquivo Dockerfile que utilize a imagem base alpine:latest.
Este Dockerfile deve executar o comando echo "Bem-vindo ao Bentão!" . Construa a imagem com a tag bentao/hello:1.0 e execute um container a partir dela.

**Publicando no Docker Hub** 

Após construir a imagem bentao/hello:1.0, faça login no Docker Hub (crie uma conta se necessário) e publique esta imagem em seu repositório público. Em seguida, apague a imagem local e faça o download dela novamente a partir do Docker Hub para testar.

***Desafio extra**

Executar comando diferente com docker run  
Execute outro comando dentro da mesma imagem: Sobrescreva o CMD.


