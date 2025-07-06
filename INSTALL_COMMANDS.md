# Comandos de Instalação Completos

## 📥 Downloads Necessários

### 1. Node.js (OBRIGATÓRIO)
```
https://nodejs.org/
- Baixe a versão LTS (Long Term Support)
- Windows: node-v20.x.x-x64.msi
- macOS: node-v20.x.x.pkg
- Linux: Siga instruções do site
```

### 2. Git (OBRIGATÓRIO)
```
https://git-scm.com/downloads
- Windows: Git-2.x.x-64-bit.exe
- macOS: Geralmente já vem instalado
- Linux: sudo apt-get install git
```

### 3. VS Code (OBRIGATÓRIO)
```
https://code.visualstudio.com/
- Windows: VSCodeUserSetup-x64-1.x.x.exe
- macOS: Visual Studio Code.app
- Linux: .deb ou .rpm
```

### 4. PostgreSQL (ESCOLHA UMA OPÇÃO)

#### Opção A: PostgreSQL Local
```
https://www.postgresql.org/download/
- Windows: postgresql-15.x-windows-x64.exe
- macOS: PostgreSQL-15.x-osx.dmg
- Linux: sudo apt-get install postgresql
```

#### Opção B: Neon (Recomendado - mais fácil)
```
https://neon.tech/
- Criar conta gratuita
- Criar novo projeto
- Copiar connection string
```

## 🔧 Instalação Passo a Passo

### Passo 1: Verificar Instalações
```bash
# Verificar se Node.js foi instalado
node --version
# Deve mostrar: v20.x.x ou superior

# Verificar se npm foi instalado
npm --version
# Deve mostrar: 10.x.x ou superior

# Verificar se Git foi instalado
git --version
# Deve mostrar: git version 2.x.x
```

### Passo 2: Criar Projeto
```bash
# Criar pasta do projeto
mkdir meow-token-airdrop
cd meow-token-airdrop

# Inicializar projeto (se não tiver package.json)
npm init -y
```

### Passo 3: Instalar TODAS as Dependências

#### Copie e cole este comando completo:
```bash
npm install @hookform/resolvers @jridgewell/trace-mapping @neondatabase/serverless @radix-ui/react-accordion @radix-ui/react-alert-dialog @radix-ui/react-aspect-ratio @radix-ui/react-avatar @radix-ui/react-checkbox @radix-ui/react-collapsible @radix-ui/react-context-menu @radix-ui/react-dialog @radix-ui/react-dropdown-menu @radix-ui/react-hover-card @radix-ui/react-label @radix-ui/react-menubar @radix-ui/react-navigation-menu @radix-ui/react-popover @radix-ui/react-progress @radix-ui/react-radio-group @radix-ui/react-scroll-area @radix-ui/react-select @radix-ui/react-separator @radix-ui/react-slider @radix-ui/react-slot @radix-ui/react-switch @radix-ui/react-tabs @radix-ui/react-toast @radix-ui/react-toggle @radix-ui/react-toggle-group @radix-ui/react-tooltip @replit/vite-plugin-cartographer @replit/vite-plugin-runtime-error-modal @solana/wallet-adapter-backpack @solana/wallet-adapter-base @solana/wallet-adapter-phantom @solana/wallet-adapter-react @solana/wallet-adapter-react-ui @solana/wallet-adapter-solflare @solana/web3.js @tailwindcss/typography @tailwindcss/vite @tanstack/react-query @types/connect-pg-simple @types/express @types/express-session @types/memoizee @types/node @types/passport @types/passport-local @types/react @types/react-dom @types/ws @vitejs/plugin-react autoprefixer class-variance-authority clsx cmdk connect-pg-simple date-fns drizzle-kit drizzle-orm drizzle-zod embla-carousel-react esbuild express express-session framer-motion input-otp lucide-react memoizee memorystore nanoid next-themes openid-client passport passport-local postcss react react-day-picker react-dom react-hook-form react-icons react-resizable-panels recharts tailwind-merge tailwindcss tailwindcss-animate tsx tw-animate-css typescript vaul vite wouter ws zod zod-validation-error
```

### Passo 4: Configurar Scripts no package.json

Adicione estes scripts no seu `package.json`:

```json
{
  "scripts": {
    "dev": "NODE_ENV=development tsx server/index.ts",
    "build": "vite build && esbuild server/index.ts --bundle --platform=node --outfile=dist/index.js --external:pg-native",
    "start": "node dist/index.js",
    "db:generate": "drizzle-kit generate",
    "db:push": "drizzle-kit push",
    "db:studio": "drizzle-kit studio",
    "client": "vite",
    "server": "tsx server/index.ts"
  }
}
```

### Passo 5: Criar Arquivos de Configuração

#### 1. Criar `.env` na raiz:
```env
# Cole este conteúdo no arquivo .env
DATABASE_URL="postgresql://usuario:senha@localhost:5432/meow_token_db"
SESSION_SECRET="super-secret-session-key-min-32-characters-long-12345"
NODE_ENV=development
PORT=5000
REPL_ID="local-development"
ISSUER_URL="https://replit.com/oidc"
REPLIT_DOMAINS="localhost:5000"
```

#### 2. Criar `vite.config.ts`:
```typescript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'
import path from 'path'

export default defineConfig({
  plugins: [react()],
  resolve: {
    alias: {
      '@': path.resolve(__dirname, './client/src'),
      '@shared': path.resolve(__dirname, './shared'),
      '@assets': path.resolve(__dirname, './attached_assets'),
    },
  },
  root: './client',
  build: {
    outDir: '../dist/public'
  },
  server: {
    port: 5173
  }
})
```

#### 3. Criar `tailwind.config.ts`:
```typescript
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./client/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {
      colors: {
        'cyber-dark': '#0a0a0f',
        'cyber-darker': '#050507',
        'cyber-purple': '#9d4edd',
        'cyber-pink': '#ff006e',
        'cyber-cyan': '#00f5ff',
        'cyber-green': '#39ff14',
        'cyber-yellow': '#ffff00',
        'cyber-red': '#ff073a',
        'cyber-gray': '#a0a0a0',
      }
    },
  },
  plugins: [],
}
```

#### 4. Criar `drizzle.config.ts`:
```typescript
import { defineConfig } from 'drizzle-kit';

export default defineConfig({
  schema: './shared/schema.ts',
  out: './drizzle',
  dialect: 'postgresql',
  dbCredentials: {
    url: process.env.DATABASE_URL!,
  },
});
```

#### 5. Criar `postcss.config.js`:
```javascript
export default {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
}
```

### Passo 6: Configurar Banco de Dados

#### Se usando PostgreSQL local:
```bash
# Criar usuário e banco
sudo -u postgres createuser --interactive
sudo -u postgres createdb meow_token_db

# Ou no Windows (abrir SQL Shell):
CREATE DATABASE meow_token_db;
CREATE USER meow_user WITH PASSWORD 'sua_senha';
GRANT ALL PRIVILEGES ON DATABASE meow_token_db TO meow_user;
```

#### Se usando Neon:
1. Vá em https://neon.tech/
2. Crie conta
3. Crie projeto
4. Copie a connection string
5. Cole no `.env` como `DATABASE_URL`

### Passo 7: Executar Configurações Iniciais
```bash
# Aplicar schema no banco
npm run db:push

# Popular missões iniciais
npx tsx scripts/seed-missions.ts
```

### Passo 8: Rodar o Projeto
```bash
# Rodar desenvolvimento (frontend + backend)
npm run dev

# Acessar:
# Frontend: http://localhost:5173
# Backend: http://localhost:5000
```

## 🔍 APIs Necessárias

### 1. CoinGecko (Preços Crypto) - GRATUITA
- Não precisa de API key
- Limit: 50 requests/minuto
- Endpoint: https://api.coingecko.com/api/v3/

### 2. Solana RPC - GRATUITA
- Mainnet: https://api.mainnet-beta.solana.com
- Devnet: https://api.devnet.solana.com

### 3. Replit Auth (Opcional para local)
- Apenas necessário em produção
- No desenvolvimento local pode ser pulado

## ⚠️ Problemas Comuns

### "command not found: npm"
- Node.js não foi instalado corretamente
- Reinicie o terminal/VS Code

### "EADDRINUSE: port already in use"
```bash
# Windows
netstat -ano | findstr :5000
taskkill /PID [NUMBER] /F

# macOS/Linux
lsof -ti:5000 | xargs kill -9
```

### "Cannot connect to database"
- Verifique se PostgreSQL está rodando
- Confirme connection string no `.env`
- Teste conexão: `npm run db:studio`

### "Module not found"
```bash
# Limpar e reinstalar
rm -rf node_modules package-lock.json
npm install
```

## ✅ Verificação Final

Execute estes comandos para confirmar que tudo está funcionando:

```bash
# 1. Verificar dependências
npm list

# 2. Verificar banco
npm run db:studio

# 3. Rodar projeto
npm run dev

# 4. Acessar http://localhost:5173
```

Se tudo estiver verde, seu projeto está pronto! 🎉