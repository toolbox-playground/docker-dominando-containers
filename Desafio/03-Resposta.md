# Resposta do Exercício-3 Hello World em Docker

**1. Clonar o repositório:**

```
git clone https://github.com/JuGalvaoMiyaki/hello-world
cd hello-world
```

**2. Criar o Dockerfile (conforme instruções):**
```

dockerfile
FROM python:3.10-slim
WORKDIR /app
COPY . /app
CMD ["python", "app.py"]
```

**3.Construir a imagem:**

```
docker build -t hello-world .
```

**4.Executar o container:**

```
docker run --name hello-container hello-world
```

**5.→ Saída esperada:**

```
Código
Hello World
```
**6.Alterar o arquivo para meu-app.py:**

```
mv app.py meu-app.py
```

**7.Editar o conteúdo:**

```
python
print("Hello, Juliana from Docker!")
```

**8.Atualizar o Dockerfile:**

```
dockerfile
FROM python:3.10-slim
WORKDIR /app
COPY . /app
CMD ["python", "meu-app.py"]
```

**9.Reconstruir a imagem:**

```
docker build -t meu-hello:1.0 .
```
**10.Executar o novo container:**

```
docker run --name meu-container meu-hello:1.0
```
```
→ Saída esperada:

Código
Hello, <nome> from Docker!
```
**11.Tente verificar o container rodando:**

```
docker ps 
```
**12.Liste todos os containers criados.**
```
docker ps -a
```
**13.Excluir o container:**

```
docker rm meu-container
```
**14.Excluir a imagem:**

```
docker rmi meu-hello:1.0
docker rmi hello-world
```

**Observações: No exercício-3 de Hello World em Python, o container roda o script, imprime a mensagem e encerra imediatamente. Isso significa que ele não fica ativo em segundo plano como um servidor web (ex.: nginx, banco de dados, api).

Containers de execução rápida: scripts, jobs, tarefas pontuais. Iniciam, fazem o trabalho e terminam.

Containers de execução contínua: serviços como nginx, MySQL, Redis, Flask. Ficam rodando até serem parados manualmente.

Por esse motivo quando executamos docker ps não obtemos o container criado como resposta. 
***