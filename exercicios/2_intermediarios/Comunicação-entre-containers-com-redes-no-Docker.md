## Objetivo
Compreender como funciona a comunicação entre containers dentro de uma rede Docker, utilizando nomes ao invés de endereços IP.

## Descrição do desafio
Você deverá criar um ambiente onde dois containers consigam se comunicar entre si.
Um dos containers deve atuar como um servidor web, enquanto o outro será responsável por realizar requisições para esse servidor.
A comunicação entre eles deve acontecer utilizando o nome do container, e não o endereço IP.

# Requesitos 
- Criar uma rede Docker personalizada
- Subir um container com um servidor web (ex: Nginx)
- Subir um segundo container capaz de realizar requisições HTTP
- Garantir que ambos estejam conectados à mesma rede
- Realizar uma requisição entre os containers utilizando o nome do container servidor

# Exploração do Exercício

- Como descobrir o IP de um container
- Se é possível acessar o servidor utilizando o IP
- Quais redes existem no Docker
- Quais containers estão conectados à rede criada

# Teste de erro 

- Rodar um container que não esteja conectado à mesma rede

# Resolução

1. Criar uma rede Docker

```docker network create minha-rede```

2. Subir um container com Nginx
```
docker run -d \
  --name servidor-web \
  --network minha-rede \
  nginx
  
```