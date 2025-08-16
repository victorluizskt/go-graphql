# Go GraphQL API

Esta aplicação implementa uma API GraphQL em Go para gerenciamento de cursos e categorias.

## Estrutura do Projeto

- `cmd/server/`: Código do servidor principal.
- `graph/`: Esquema GraphQL, resolvers e modelos.
- `internal/database/`: Lógica de acesso ao banco de dados.
- `data.db`: Banco de dados SQLite.
- `gqlgen.yml`: Configuração do gqlgen.

## Como Executar

1. Instale as dependências:
   ```sh
   go mod tidy
   ```

2. Inicie o servidor:
   ```sh
   go run cmd/server/server.go
   ```

3. Acesse o playground GraphQL em `http://localhost:8081`.

## Principais Funcionalidades

- Consultar cursos e categorias.
- Criar, atualizar e remover cursos e categorias via GraphQL.

## Tecnologias Utilizadas

- Go
- gqlgen
- SQLite

## Scripts Úteis

- Gerar código GraphQL:
  ```sh
  go run github.com/99designs/gqlgen generate
  ```

##