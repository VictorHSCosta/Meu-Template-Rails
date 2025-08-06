# Configuração de Variáveis de Ambiente

Este projeto usa a gem `dotenv-rails` para gerenciar as variáveis de ambiente de forma segura.

## Setup Inicial

1. Copie o arquivo `.env.example` para `.env`:
   ```bash
   cp .env.example .env
   ```

2. Edite o arquivo `.env` com suas credenciais reais:
   ```env
   DB_HOST=localhost
   DB_PORT=5432
   DB_USERNAME=postgres
   DB_PASSWORD=sua_senha_aqui
   ```

## Variáveis Disponíveis

### Database
- `DB_HOST`: Host do banco de dados (padrão: localhost)
- `DB_PORT`: Porta do banco de dados (padrão: 5432)
- `DB_USERNAME`: Usuário do banco de dados
- `DB_PASSWORD`: Senha do banco de dados
- `DB_NAME_DEVELOPMENT`: Nome do banco de desenvolvimento
- `DB_NAME_TEST`: Nome do banco de testes
- `DB_NAME_PRODUCTION`: Nome do banco de produção
- `TEMPLATE_RAILS_DATABASE_PASSWORD`: Senha específica para produção

### Rails
- `RAILS_MAX_THREADS`: Número máximo de threads (padrão: 5)

## Como Funciona

A gem `dotenv-rails` carrega automaticamente as variáveis do arquivo `.env` quando a aplicação inicia. Estas variáveis ficam disponíveis através do hash `ENV` em toda a aplicação.

Exemplo de uso:
```ruby
# No database.yml
username: <%= ENV.fetch("DB_USERNAME") { "postgres" } %>

# Em qualquer lugar do código Ruby
host = ENV["DB_HOST"]
```

## Segurança

- O arquivo `.env` está no `.gitignore` e **nunca deve ser commitado**
- Use o `.env.example` como template para outros desenvolvedores
- Em produção, configure as variáveis diretamente no servidor/container

## Comandos Úteis

```bash
# Verificar se as variáveis estão sendo carregadas
rails runner "puts ENV['DB_USERNAME']"

# Rodar migrações com as novas configurações
rails db:create
rails db:migrate
```
