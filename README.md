# go-rest-api
Simple RESTful API With Golang using **Gorm** and **Gin**.
## Stack utilizada

**Back-end:** Go, Docker, PostgreSQL


## GIN
O Gin é uma estrutura da Web Go usada para criar APIs RESTful de alto desempenho. 
É baseado na estrutura Martini e é simples, flexível e rápido. 
O Gin pode navegar pelas rotas da API mais rapidamente que o Martini e suporta middleware, tornando-o popular entre os desenvolvedores.

## GORM
Gorm, por outro lado, é uma biblioteca Go Object-Relational Mapping ( ORM ) que simplifica as interações do banco de dados, como criar, ler, atualizar e excluir registros. 
Ele suporta vários bancos de dados, incluindo MySQL, PostgreSQL e SQLite, e fornece uma interface unificada para trabalhar com eles.
## Instalação GO [Ubuntu/Wsl]
```bash
1. sudo apt-get update
2. wget https://go.dev/dl/go1.21.0.linux-amd64.tar.gz
3. sudo tar -xvf go1.21.0.linux-amd64.tar.gz
4. sudo mv go /usr/local
5. export GOROOT=/usr/local/go
6. export GOPATH=$HOME/go
7. export PATH=$GOPATH/bin:$GOROOT/bin:$PATH
8. source ~/.profile
9. go version
```



## Rodando localmente

*Lembre-se de ter o PGSQL instalado em sua máquina para o GO poder criar o banco e executar as migrations. Você pode rodar o pgsql atráves do docker e apenas configurar as credenciais no arquivo **[initializes/database.go]***

Clone o projeto

```bash
  git clone https://github.com/xikaojr/go-rest-api
```

Entre no diretório do projeto

```bash
  cd go-rest-api
```

Digite em seu terminal o seguinte comando para instalar os módulos gin/gorm.

```bash
go get github.com/gin-gonic/gin gorm.io/gorm
```

Baixando driver postgres
```bash
go get gorm.io/driver/postgres
```

Execute a criação das tabelas no banco

```bash
go run migrate/migrate.go
```

Inicie o servidor

```bash
  go run main.go
```


## Documentação da API

#### Cria um registro de 'Post'

```http
  POST /post/
```

| Parâmetro   | Tipo       | Descrição                                   |
| :---------- | :--------- | :------------------------------------------ |
| `title`      | `string` | **Obrigatório**. O título do seu post |
| `body`      | `string` | **Obrigatório**. O conteúdo do seu post |


#### Retorna todos os posts criados

```http
  GET /posts
```

#### Retorna um unico post

```http
  GET /posts/${id}
```

| Parâmetro   | Tipo       | Descrição                                   |
| :---------- | :--------- | :------------------------------------------ |
| `id`      | `string` | **Obrigatório**. O ID do item que você quer retornar |

#### Atualiza um unico post

```http
  PATCH /post/${id}
```

| Parâmetro   | Tipo       | Descrição                                   |
| :---------- | :--------- | :------------------------------------------ |
| `id`      | `string` | **Obrigatório**. O ID do item que você quer atualizar |

#### Delete um unico post

```http
  DELETE /post/${id}
```

| Parâmetro   | Tipo       | Descrição                                   |
| :---------- | :--------- | :------------------------------------------ |
| `id`      | `string` | **Obrigatório**. O ID do item que você quer deletar |

## Referência

 - [Gin Gonic](https://gin-gonic.com/docs/)
