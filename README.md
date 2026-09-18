# MessageLive

MessageLive é uma aplicação de chat em tempo real com autenticação de usuários, criação de salas e comunicação via WebSockets. O projeto foi desenvolvido com Node.js, TypeScript, Express, Socket.IO e Prisma com PostgreSQL.

## 🚀 Funcionalidades

- Registro e login de usuários
- Autenticação com JWT
- Criação de salas
- Chat em tempo real com Socket.IO
- Persistência de dados com Prisma + PostgreSQL
- API REST para gerenciamento de usuários e salas

## 🛠️ Tecnologias

- Node.js
- TypeScript
- Express
- Socket.IO
- Prisma ORM
- PostgreSQL
- JWT
- bcrypt
- CORS

## 📦 Requisitos

Antes de iniciar, certifique-se de ter instalado:

- Node.js 18 ou superior
- npm ou yarn
- PostgreSQL

## ⚙️ Instalação

1. Clone o repositório:

```bash
git clone <url-do-repositorio>
cd messageLive
```

2. Instale as dependências:

```bash
npm install
```

3. Crie um arquivo `.env` na raiz do projeto com as variáveis de ambiente:

```env
DATABASE_URL="postgresql://usuario:senha@localhost:5432/messagelive?schema=public"
PORT=5000
JWT_SECRET="sua-chave-secreta"
```

> Ajuste a URL do PostgreSQL conforme seu ambiente local.

4. Gere o cliente Prisma e configure o banco:

```bash
npx prisma generate
npx prisma db push
```

Ou, se preferir usar migrations:

```bash
npx prisma migrate dev
```

## ▶️ Executando a aplicação

Para iniciar o servidor em modo de desenvolvimento:

```bash
npm run dev
```

A aplicação ficará disponível em:

```bash
http://localhost:5000
```

## 📡 Rotas da API

### Health check

```http
GET /
```

Retorna uma mensagem confirmando que o servidor está funcionando.

### Registro

```http
POST /register
```

Body esperado:

```json
{
  "name": "Daniel",
  "email": "daniel@email.com",
  "password": "123456"
}
```

### Login

```http
POST /login
```

Body esperado:

```json
{
  "email": "daniel@email.com",
  "password": "123456"
}
```

### Criação de sala

```http
POST /createRoom
```

Requer autenticação via token JWT no header:

```http
Authorization: Bearer <token>
```

## 🔌 WebSocket

O projeto também expõe eventos Socket.IO para comunicação em tempo real, como:

- `join`
- `sendMessage`
- `logout`
- `userList`
- `message`
- `setUser`

Esses eventos permitem que usuários entrem no chat, enviem mensagens e recebam atualizações em tempo real.

## 🧱 Estrutura do projeto

```bash
src/
├── application/
│   ├── controllers/
│   ├── repository/
│   └── usecases/
├── infra/
│   ├── database/
│   └── websocket/
├── middleware/
├── routes/
├── services/
├── @types/
├── server.ts
└── ...
```

## 🗃️ Prisma

O schema principal define os modelos:

- `User`
- `Room`

O arquivo de configuração está em:

```bash
prisma/schema.prisma
```

## 📝 Observações

- A aplicação usa `@prisma/client` para acesso ao banco PostgreSQL.
- O projeto está estruturado em camadas para facilitar manutenção e evolução.
- A autenticação é exigida para algumas rotas sensíveis, como criação de salas.

## 🤝 Contribuição

Sinta-se à vontade para abrir issues ou pull requests com melhorias, correções e novas funcionalidades.

## 📄 Licença

Este projeto está sob a licença ISC.
