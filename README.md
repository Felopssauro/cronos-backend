# Cronos Backend

API do SCA UEPA (NestJS + Prisma + PostgreSQL) para conexão com o banco de dados.

## Contribuindo

### Pré-requisitos

- Docker
- Docker Compose

### Desenvolvimento com Docker

Execute a partir da raiz do repositório (`cronos-webapp/`) ou utilize o mesmo comando para subir o container apenas do backend:

```bash
docker compose -f docker-compose.dev.yml up --build -d
```

### Variáveis de ambiente

Definidas no compose de desenvolvimento:

- `DATABASE_URL`
- `JWT_SECRET`

é necessário criar um arquivo `.env` com essas variáveis.

### Estrutura

- `src/main.ts`: bootstrap do NestJS e CORS.
- `src/app.module.ts`: registro dos módulos.
- `prisma/schema.prisma`: modelos e relações.
- `prisma/migrations/`: migrações.

### Convenções

- Módulos NestJS por domínio (ex.: `professor/`, `disciplina/`).
- DTOs/Services/Controllers conforme padrão NestJS.
