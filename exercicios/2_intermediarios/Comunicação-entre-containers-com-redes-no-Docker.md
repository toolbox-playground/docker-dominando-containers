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
3. Subir um container cliente (temporário)
```
docker run -it --rm \
  --network minha-rede \
  curlimages/curl \
  sh
```
4. Testar a comunicação
```curl http://servidor-web```

# Resultado esperado

Você deve ver o HTML padrão do Nginx.

Isso acontece porque:
O Docker resolve automaticamente o nome servidor-web
Não precisamos usar IP

# Parte de investigação do exercício:

1. Descobrir o IP do container
```docker inspect servidor-web```

2. Procurar por:

```IPAddress```

# Testar acesso via IP

1. No container cliente:

```curl http://172.21.0.2```

Testei o acesso via IP e não funcionou porque o IP do container pertence a uma rede interna do Docker.
Essa rede é isolada, permitindo comunicação apenas entre containers que estão conectados a ela.
Como o teste foi feito a partir da máquina host (meu Mac), não foi possível acessar diretamente esse IP.

2.  Listar redes

```docker network ls```

3. Inspecionar a rede criada

```docker network inspect minha-rede```

# Teste de erro 

1. Peça para rodarem um container fora da rede:

```docker run -it --rm curlimages/curl sh```

Não houve resposta, pois o container está fora da rede. 
