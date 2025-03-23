Claro, Thiago! Aqui está um `README.md` no mesmo estilo que você está seguindo, com um exemplo prático de uso do `docker-compose` para rodar um **servidor web com um banco de dados** (usando **NGINX + PHP + MySQL** como exemplo):

---

# Docker Compose: Servidor Web com Banco de Dados

Este guia mostra como utilizar `docker-compose` para rodar um ambiente completo com servidor web e banco de dados.

## 1. Criando o Arquivo `docker-compose.yml`

Crie um arquivo chamado `docker-compose.yml` com o seguinte conteúdo:

```yaml
version: '3.8'

services:
  web:
    image: php:8.1-apache
    container_name: servidor-web
    ports:
      - "8080:80"
    volumes:
      - ./app:/var/www/html
    depends_on:
      - db

  db:
    image: mysql:5.7
    container_name: banco-dados
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: minhaapp
      MYSQL_USER: usuario
      MYSQL_PASSWORD: senha
    volumes:
      - db_data:/var/lib/mysql

volumes:
  db_data:
```

Crie também uma pasta `app/` com um arquivo `index.php` para testar:

```php
<?php
$servername = "db";
$username = "usuario";
$password = "senha";
$database = "minhaapp";

// Testando conexão
$conn = new mysqli($servername, $username, $password, $database);

if ($conn->connect_error) {
  die("Conexão falhou: " . $conn->connect_error);
}
echo "Conectado com sucesso ao banco de dados!";
?>
```

## 2. Subindo os Containers

No terminal, execute:

```bash
docker-compose up -d
```

Esse comando irá baixar as imagens, criar a rede e iniciar os containers.

## 3. Testando a Conexão

Abra seu navegador e acesse:

```
http://localhost:8080
```

Se tudo estiver funcionando, você verá a mensagem:

```
Conectado com sucesso ao banco de dados!
```

Você também pode verificar os logs com:

```bash
docker-compose logs -f
```

## 4. Derrubando os Serviços

Para parar e remover os containers, volumes e a rede criada:

```bash
docker-compose down
```

---

Se quiser, posso adaptar esse exemplo para usar PostgreSQL, Node.js ou outro stack que você prefira. É só falar!