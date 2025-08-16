# Go GraphQL API

Esta aplicação implementa uma **API GraphQL em Go** para gerenciamento de cursos e categorias.

## Estrutura do Projeto

- `cmd/server/`: Código do servidor principal.
- `graph/`: Esquema GraphQL, resolvers e modelos.
- `internal/database/`: Lógica de acesso ao banco de dados.
- `data.db`: Banco de dados SQLite.
- `gqlgen.yml`: Configuração do gqlgen.

## Pré-requisitos

- Go >= 1.20
- SQLite instalado (opcional, mas recomendado para inspecionar `data.db`)
- `git`

## Como Executar

1. Clone o repositório:

```sh
git clone https://github.com/victorluizskt/go-graphql.git
cd go-graphql
```

2. Instale as dependências:

```sh
go mod tidy
```

3. Gere o código GraphQL (caso tenha alterado o schema):

```sh
go run github.com/99designs/gqlgen generate
```

4. Inicie o servidor:

```sh
go run cmd/server/server.go
```

5. Acesse o **playground GraphQL**: [http://localhost:8081](http://localhost:8081)

## Funcionalidades

- Consultar cursos e categorias.
- Criar, atualizar e remover cursos e categorias via GraphQL.
- Relacionamento `Category -> Courses` e `Course -> Category`.

## Exemplos de Queries e Mutations

### Criar categoria

```graphql
mutation {
  createCategory(input: {name: "Tecnologia", description:"Cursos de TI"}) {
    id
    name
    description
  }
}
```

### Criar curso

```graphql
mutation {
  createCourse(input: {name: "Full Cycle", description: "Medium", categoryId: "31ac5728-8102-461d-84ce-74937f81f4c7"}) {
    id
    name
  }
}
```

### Consultar categorias

```graphql
query {
  categories {
    id
    name
  }
}
```

### Consultar categorias com cursos

```graphql
query {
  categories {
    id
    name
    courses {
      id
      name
    }
  }
}
```

### Consultar cursos com categoria

```graphql
query {
  courses {
    id
    name
    description
    category {
      name
    }
  }
}
```

## Tecnologias Utilizadas

- Go
- gqlgen
- SQLite
