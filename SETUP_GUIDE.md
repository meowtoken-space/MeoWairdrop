# Guia Completo - Configuração do Projeto MeoW Token

## 📋 Pré-requisitos

### 1. Softwares Necessários

1. **Node.js** (versão 18 ou superior)
   - Download: https://nodejs.org/
   - Versão recomendada: LTS (Long Term Support)

2. **Git**
   - Download: https://git-scm.com/
   - Para clonar o repositório

3. **VS Code**
   - Download: https://code.visualstudio.com/
   - IDE principal para desenvolvimento

4. **PostgreSQL** (banco de dados)
   - Download: https://www.postgresql.org/download/
   - Ou use um serviço como Neon (https://neon.tech/) para PostgreSQL na nuvem

### 2. Extensões VS Code Recomendadas

```
- TypeScript Vue Plugin (Volar)
- ES7+ React/Redux/React-Native snippets
- Auto Rename Tag
- Bracket Pair Colorizer
- GitLens
- Prettier - Code formatter
- ESLint
- Thunder Client (para testar APIs)
```

## 🚀 Instalação Passo a Passo

### Passo 1: Clonar/Baixar o Projeto

```bash
# Se o projeto estiver no GitHub
git clone [URL_DO_REPOSITORIO]
cd meow-token-airdrop

# Ou crie uma pasta e copie todos os arquivos manualmente
mkdir meow-token-airdrop
cd meow-token-airdrop
```

### Passo 2: Instalar Dependências

```bash
# Instalar todas as dependências do projeto
npm install
```

### Passo 3: Configurar Banco de Dados

#### Opção A: PostgreSQL Local
```bash
# Instalar PostgreSQL localmente
# Windows: Baixar do site oficial
# macOS: brew install postgresql
# Linux: sudo apt-get install postgresql

# Criar banco de dados
createdb meow_token_db
```

#### Opção B: Neon (Recomendado - PostgreSQL na nuvem)
1. Acesse: https://neon.tech/
2. Crie uma conta gratuita
3. Crie um novo projeto
4. Copie a connection string

### Passo 4: Configurar Variáveis de Ambiente

Crie um arquivo `.env` na raiz do projeto:

```env
# Banco de Dados
DATABASE_URL="postgresql://usuario:senha@localhost:5432/meow_token_db"
# Ou se usando Neon:
# DATABASE_URL="postgresql://[usuario]:[senha]@[host]/[database]?sslmode=require"

# Configurações do Servidor
PORT=5000
NODE_ENV=development

# Autenticação Replit (para produção)
SESSION_SECRET="seu-secret-super-seguro-aqui-min-32-chars"
REPL_ID="seu-repl-id"
ISSUER_URL="https://replit.com/oidc"
REPLIT_DOMAINS="localhost:5000"

# PostgreSQL (se usando local)
PGHOST=localhost
PGPORT=5432
PGUSER=seu_usuario
PGPASSWORD=sua_senha
PGDATABASE=meow_token_db
```

### Passo 5: Configurar Banco de Dados

```bash
# Executar migrações/criar tabelas
npm run db:push

# Semear dados iniciais (missões)
npx tsx scripts/seed-missions.ts
```

### Passo 6: Instalar Dependências Adicionais (se necessário)

```bash
# Se alguma dependência estiver faltando, instale:
npm install @neondatabase/serverless
npm install drizzle-orm
npm install @tanstack/react-query
npm install @radix-ui/react-accordion
npm install @radix-ui/react-alert-dialog
npm install @radix-ui/react-avatar
npm install @radix-ui/react-button
npm install @radix-ui/react-card
npm install @radix-ui/react-dialog
npm install @radix-ui/react-dropdown-menu
npm install @radix-ui/react-form
npm install @radix-ui/react-label
npm install @radix-ui/react-progress
npm install @radix-ui/react-select
npm install @radix-ui/react-separator
npm install @radix-ui/react-slider
npm install @radix-ui/react-switch
npm install @radix-ui/react-tabs
npm install @radix-ui/react-toast
npm install @radix-ui/react-tooltip
npm install @solana/wallet-adapter-base
npm install @solana/wallet-adapter-react
npm install @solana/wallet-adapter-react-ui
npm install @solana/wallet-adapter-phantom
npm install @solana/wallet-adapter-solflare
npm install @solana/wallet-adapter-backpack
npm install @solana/web3.js
npm install lucide-react
npm install react-hook-form
npm install @hookform/resolvers
npm install zod
npm install tailwindcss
npm install autoprefixer
npm install postcss
npm install vite
npm install @vitejs/plugin-react
npm install tsx
npm install typescript
npm install wouter
npm install nanoid
npm install date-fns
npm install framer-motion
npm install class-variance-authority
npm install clsx
npm install tailwind-merge
```

## 🔧 APIs e Serviços Externos

### 1. CoinGecko API (Preços de Criptomoedas)
- **Gratuita** - Não precisa de API key para uso básico
- Limite: 50 calls/minuto
- URL: https://api.coingecko.com/api/v3/

### 2. Replit Auth (Autenticação)
- Para desenvolvimento local, você pode pular temporariamente
- Para produção no Replit, é automático

### 3. Solana RPC (Blockchain)
- **Gratuita** - Endpoints públicos disponíveis
- Mainnet: https://api.mainnet-beta.solana.com
- Devnet: https://api.devnet.solana.com

## 🏃 Comandos para Rodar

### Desenvolvimento
```bash
# Rodar o projeto completo (frontend + backend)
npm run dev

# Ou rodar separadamente:
# Backend apenas
npm run server

# Frontend apenas (em outro terminal)
npm run client
```

### Produção
```bash
# Build do projeto
npm run build

# Rodar versão de produção
npm start
```

### Banco de Dados
```bash
# Aplicar mudanças no schema
npm run db:push

# Gerar migrações
npm run db:generate

# Visualizar banco (Drizzle Studio)
npm run db:studio
```

## 📁 Estrutura do Projeto

```
meow-token-airdrop/
├── client/                 # Frontend React
│   ├── src/
│   │   ├── components/     # Componentes UI
│   │   ├── pages/         # Páginas da aplicação
│   │   ├── hooks/         # Custom hooks
│   │   ├── lib/           # Utilitários
│   │   └── index.css      # Estilos globais
├── server/                # Backend Express
│   ├── db.ts             # Configuração do banco
│   ├── routes.ts         # Rotas da API
│   ├── storage.ts        # Operações do banco
│   └── index.ts          # Servidor principal
├── shared/               # Código compartilhado
│   └── schema.ts         # Schema do banco de dados
├── scripts/              # Scripts utilitários
│   └── seed-missions.ts  # Povoar missões
├── package.json          # Dependências
├── vite.config.ts       # Configuração Vite
├── tailwind.config.ts   # Configuração Tailwind
└── .env                 # Variáveis de ambiente
```

## 🌐 URLs de Acesso

Após rodar `npm run dev`:

- **Frontend**: http://localhost:5173
- **Backend API**: http://localhost:5000
- **Drizzle Studio**: http://localhost:4983 (se rodar `npm run db:studio`)

## 🔍 Testando a Aplicação

1. **Acesse**: http://localhost:5173
2. **Faça login** (se configurou Replit Auth)
3. **Teste funcionalidades**:
   - Check-in diário
   - Visualizar missões
   - Conectar carteira Solana
   - Jogar mini-games
   - Ver leaderboard

## ❗ Possíveis Problemas e Soluções

### Erro de Banco de Dados
```bash
# Recriar tabelas
npm run db:push
npx tsx scripts/seed-missions.ts
```

### Porta já em uso
```bash
# Matar processo na porta
# Windows
netstat -ano | findstr :5000
taskkill /PID [PID_NUMBER] /F

# macOS/Linux
lsof -ti:5000 | xargs kill -9
```

### Dependências em conflito
```bash
# Limpar cache e reinstalar
rm -rf node_modules package-lock.json
npm install
```

## 📞 Suporte

Se tiver problemas:
1. Verifique se todas as dependências estão instaladas
2. Confirme se o banco de dados está rodando
3. Verifique o arquivo `.env`
4. Consulte os logs no terminal para erros específicos

## 🎯 Próximos Passos

Após configurar:
1. Customize o design/cores
2. Configure APIs de redes sociais
3. Implemente verificações de missões
4. Configure webhook para check-ins
5. Deploy para produção (Vercel, Netlify, etc.)