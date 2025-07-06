# replit.md

## Overview

This is a full-stack web application for MeoW Token, a cyberpunk-themed cryptocurrency airdrop platform. The application features a gamified experience where users can complete missions, play games, and earn tokens. It's built with React on the frontend, Express.js on the backend, and uses PostgreSQL with Drizzle ORM for data persistence.

## System Architecture

The application follows a modern full-stack architecture with clear separation between client and server:

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite for fast development and optimized builds
- **UI Components**: Radix UI primitives with shadcn/ui component library
- **Styling**: Tailwind CSS with custom cyberpunk theme variables
- **State Management**: TanStack Query for server state management
- **Routing**: Wouter for lightweight client-side routing
- **Forms**: React Hook Form with Zod validation

### Backend Architecture
- **Framework**: Express.js with TypeScript
- **Database**: PostgreSQL with Neon serverless driver
- **ORM**: Drizzle ORM for type-safe database operations
- **Authentication**: Replit Auth with OpenID Connect
- **Session Management**: Express sessions with PostgreSQL store

### Blockchain Integration
- **Wallet Support**: Solana wallet adapters (Phantom, Solflare, Backpack)
- **Web3 Library**: @solana/web3.js for blockchain interactions
- **External APIs**: CoinGecko API for cryptocurrency price data

## Key Components

### Authentication System
- Replit Auth integration for secure user authentication
- OpenID Connect flow with JWT tokens
- Session persistence in PostgreSQL
- Automatic user creation and profile management

### Mission System
- Dynamic mission creation and management
- Category-based missions (daily check-in, social, GitHub, referral, games, pre-sale)
- Point-based reward system
- Progress tracking and completion validation

### Gaming Platform
- Multiple mini-games with point rewards
- Score tracking and leaderboards
- Cyberpunk-themed game experiences
- Integration with mission completion system

### Wallet Integration
- Multi-wallet support for Solana ecosystem
- Secure wallet connection and management
- Transaction handling for pre-sale purchases
- Wallet address verification and storage

### Pre-Sale System
- Token pre-sale with SOL payment support
- Purchase tracking and history
- Automatic token allocation calculation
- Transaction verification system

## Data Flow

1. **User Authentication**: Users authenticate via Replit Auth, creating a session stored in PostgreSQL
2. **Mission Completion**: Users complete missions, triggering point allocation and progress updates
3. **Game Interactions**: Game scores are saved and contribute to overall user points and mission completion
4. **Wallet Operations**: Wallet connections are verified and stored, enabling pre-sale participation
5. **Leaderboard Updates**: User activities update rankings displayed in real-time leaderboards

## External Dependencies

### Core Dependencies
- **@neondatabase/serverless**: Serverless PostgreSQL driver for Neon database
- **drizzle-orm**: Type-safe ORM for database operations
- **@tanstack/react-query**: Server state management and caching
- **@radix-ui/***: Accessible UI primitive components
- **@solana/wallet-adapter-***: Solana wallet integration libraries

### Development Tools
- **Vite**: Frontend build tool and development server
- **TypeScript**: Type safety across the entire application
- **Tailwind CSS**: Utility-first CSS framework
- **ESBuild**: Fast JavaScript bundling for production

### External APIs
- **CoinGecko API**: Real-time cryptocurrency price data
- **Replit Auth**: Authentication and user management service

## Deployment Strategy

### Development Environment
- Vite development server for frontend with hot module replacement
- Express server with TypeScript compilation via tsx
- Database migrations managed through Drizzle Kit
- Environment variables for database and authentication configuration

### Production Build
- Frontend: Vite builds optimized static assets to `dist/public`
- Backend: ESBuild compiles TypeScript server code to `dist/index.js`
- Database: Drizzle migrations ensure schema consistency
- Static serving: Express serves built frontend assets in production

### Environment Configuration
- `DATABASE_URL`: PostgreSQL connection string (required)
- `SESSION_SECRET`: Secret for session encryption (required)
- `REPL_ID`: Replit environment identifier (required for auth)
- `ISSUER_URL`: OpenID Connect issuer URL (defaults to Replit)

## Local Development Setup

Para rodar este projeto no VS Code local, consulte os arquivos:
- `SETUP_GUIDE.md` - Guia completo de configuração
- `INSTALL_COMMANDS.md` - Comandos detalhados de instalação

### Dependências Principais
- Node.js 18+ 
- PostgreSQL (local ou Neon)
- VS Code com extensões TypeScript/React

### Scripts Disponíveis
- `npm run dev` - Desenvolvimento (frontend + backend)
- `npm run build` - Build para produção  
- `npm run db:push` - Aplicar schema no banco
- `npm run db:studio` - Interface visual do banco

## Changelog

```
Changelog:
- July 01, 2025: Initial setup
- July 01, 2025: Added social media missions and progressive daily check-in system
- July 01, 2025: Created comprehensive local development setup guides
- July 02, 2025: Switched from Replit Auth to Phantom Wallet-only authentication
- July 02, 2025: Implemented cyberpunk design with crypto price tracking (emojis 😻/😿)
- July 02, 2025: Added comprehensive MeoW Token airdrop specification guide
- July 02, 2025: Enhanced dashboard with enterprise-level design (shadows, gradients, hover effects)
- July 02, 2025: Integrated Supabase database while maintaining Phantom Wallet authentication
- July 02, 2025: Implemented unique wallet ranking system to prevent duplicate addresses in leaderboard
- July 02, 2025: Added comprehensive search system to MeoW Rank with "Find My Wallet" feature
- July 02, 2025: Replaced emoji with official Phantom 3D logo with floating animations
- July 02, 2025: Updated hero text to "FUJA DA MATRIX" and removed Leaderboard section title
- July 02, 2025: Implemented Twitter API integration with Bearer Token authentication for mission verification
- July 02, 2025: Updated all Twitter references from @meowtoken to @meowtokenMWT across platform
- July 02, 2025: Implemented simplified mission claim system - all missions now show "Claim Rewards" button after initial action
- July 02, 2025: Reorganized sidebar layout - moved Twitter and wallet connections below navigation, added social media links section
- July 02, 2025: Completed full Portuguese Brazilian localization of Landing page including hero section, statistics, features, and CTAs
- July 02, 2025: Implemented 3D relief header effect with animated "bombado para fora" background using multiple gradient layers, inset shadows, and interactive hover states
- July 02, 2025: Refined header relief effect by removing sharp borders, reducing opacity values, and creating smoother radial gradients for a more natural "bombado" appearance
- July 02, 2025: Created comprehensive internationalization system with flag-based language switching between Portuguese (🇧🇷) and English (🇺🇸)
- July 02, 2025: Implemented cartoon-style flag buttons with 3D beveled frames, sparkle effects, bouncy animations, and cyberpunk color gradients when selected
- July 02, 2025: Enhanced Solana icon with dark background (#1a1a2e) and colorful gradient symbol for better mobile visibility
- July 02, 2025: Added 3D italic effects to crypto price cards with larger borders (border-4), skew transformations, and dynamic colored shadows based on price movement
- July 02, 2025: Replaced logout text with white SVG exit icon featuring cyberpunk glow effects and animations
- July 02, 2025: Redesigned wallet button modal - when connected shows user points and copy wallet address instead of wallet selection options
- July 02, 2025: Completely removed ThemeToggle button and all theme switching functionality - application now uses fixed dark cyberpunk theme only
- July 02, 2025: Implemented advanced iOS deep linking for Phantom wallet with universal links, visibility tracking, and intelligent fallback sequences to improve mobile wallet connection reliability
- July 02, 2025: Fixed header to remain static at top of page (changed from sticky to fixed positioning) with proper spacing adjustments for mobile and desktop layouts
- July 02, 2025: Implemented robust CoinGecko API handling with 1-minute cache, fallback data, and generated chart data to ensure crypto prices always display correctly
- July 02, 2025: Added 24-hour trading volume information to crypto price cards with formatted display (B/M/K abbreviations) and fallback values for reliable data presentation
- July 02, 2025: Optimized header height and spacing - reduced padding to py-2, adjusted mobile layout positioning, and increased content padding-top (pt-48 mobile, pt-32 desktop) plus hero section padding (pt-32 mobile, pt-24 desktop) to ensure adequate spacing between fixed header and action buttons
- July 03, 2025: Moved crypto price cards from Layout (global scroll-following) to fixed position only at top of homepage - cards now stay at top-14 with backdrop blur and cyberpunk styling, no longer follow scroll or cover content on other pages
- July 03, 2025: Fixed crypto cards positioning - changed from fixed to absolute positioning to prevent scroll following, restored full CryptoPrices component with graphs, volume data, and proper sizing, positioned at top-20 with margins to avoid sidebar overlap
- July 03, 2025: Reorganized crypto cards layout - BTC and ETH on first row (2 columns), SOL centered on second row (50% width), improved visual hierarchy and spacing with space-y-4 container
- July 03, 2025: Implemented ultra-compact crypto cards with minimal padding (p-2), reduced fonts, and desktop positioning (left-80) to avoid sidebar overlap, plus adjusted hero section spacing (pt-56 mobile, pt-48 desktop, mt-20/mt-16 content) to prevent card overlap
- July 03, 2025: Optimized crypto card layout for desktop - reduced width (right-32 instead of right-6), decreased max-width (max-w-2xl), and minimized vertical spacing (pt-44 desktop, mt-12) for tighter integration with content below
- July 03, 2025: Enhanced mobile header UX - when sidebar is open, header shows logo + X button alongside language flags, hides wallet button until menu closes, ensures proper z-index layering to prevent header overlap with sidebar content
```

## User Preferences

```
Preferred communication style: Simple, everyday language.
Project Vision: MeoW Token - Cyberpunk-themed cryptocurrency airdrop platform
Design Style: Cyberpunk minimalista with "gatos do futuro" theme
Color Palette: Roxo #9a45fc, Ciano #2ad6d0, Amarelo #ffe118, Fundo #0b0019
Authentication: Phantom Wallet only (Solana blockchain)
Inspirations: Caramelo Token (layout), Raydium (cyberpunk style), Monad (gamification), Fragmetrix (points system)
```

## Project Roadmap

### Phase 1: Pré-Lançamento ✅ COMPLETED
- Site one-page cyberpunk funcionando
- Conexão com Phantom Wallet
- Design responsivo implementado
- Sistema de missões ativo (16 missões)

### Phase 2: Participação no Airdrop 🔄 IN PROGRESS  
- Conexão de carteira funcionando
- Sistema anti-bot básico
- Tarefas de engajamento completas (PENDING)
- Programa de referência (PENDING)
- Integração com APIs sociais (PENDING)

### Phase 3: Distribuição de Recompensas 📅 PLANNED
- Cálculo de recompensas
- Distribuição de tokens MWT
- Comunicação pós-distribuição