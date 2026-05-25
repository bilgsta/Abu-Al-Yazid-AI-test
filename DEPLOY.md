# Abu Al-Yazid – Personal AI Assistant

> Arabic-first AI assistant platform built with React, Node.js, and Express

## Quick Start

### Prerequisites
- Node.js 20+
- PostgreSQL 16+
- npm or yarn

### Local Development

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/Abu-Al-Yazid-AI.git
   cd Abu-Al-Yazid-AI
   ```

2. **Setup environment variables**
   ```bash
   cp .env.example .env.local
   # Edit .env.local with your configuration
   ```

3. **Install dependencies**
   ```bash
   npm install
   ```

4. **Setup database**
   ```bash
   npm run db:push
   ```

5. **Start development server**
   ```bash
   npm run dev
   ```
   The app will be available at `http://localhost:5000`

### Environment Variables

Required environment variables (see `.env.example` for full list):
- `DATABASE_URL` - PostgreSQL connection string
- `PORT` - Server port (default: 5000)
- `NODE_ENV` - Environment mode (development/production)
- `SESSION_SECRET` - Session encryption key
- `AI_INTEGRATIONS_OPENAI_API_KEY` - OpenAI API key (for Replit AI)

### Building for Production

```bash
npm run build
npm run start
```

## Project Structure

```
├── client/              # React + Vite frontend
│   ├── src/
│   │   ├── pages/      # Page components
│   │   ├── components/ # Reusable components
│   │   └── hooks/      # Custom React hooks
│   └── index.html
├── server/             # Express.js backend
│   ├── routes.ts       # API routes
│   ├── index.ts        # Server entry point
│   └── db.ts          # Database setup
├── shared/             # Shared types and schemas
└── script/             # Build scripts
```

## Available Scripts

- `npm run dev` - Start development server with hot reload
- `npm run build` - Build for production
- `npm run start` - Run production build
- `npm run check` - Type check with TypeScript
- `npm run db:push` - Push database migrations

## Deployment

### Deploy on Replit
1. Fork the repository
2. Open on Replit
3. Create a `.env` file with your configuration
4. Click the "Run" button

### Deploy on GitHub Pages / Vercel / etc.
The project includes GitHub Actions workflows for automatic building and testing. Push to the main branch and GitHub will automatically build and run tests.

## Architecture

### Frontend
- **React 18** with TypeScript
- **Vite** for fast builds
- **Tailwind CSS** for styling
- **Shadcn/ui** for component library
- **TanStack React Query** for data fetching
- RTL support for Arabic

### Backend
- **Express.js** with TypeScript
- **PostgreSQL** with Drizzle ORM
- **Passport.js** for authentication (Replit Auth)
- **Server-Sent Events (SSE)** for AI streaming
- **Multer** for file uploads

### Database
- PostgreSQL with Drizzle ORM
- Zod for schema validation
- Session storage with `connect-pg-simple`

## Database

The project uses PostgreSQL with Drizzle ORM for type-safe database operations.

**Important Tables** (do not drop):
- `sessions` - Session storage for authentication
- `users` - User accounts
- `user_preferences` - User settings

To manage database:
```bash
npm run db:push     # Push schema changes
```

## Troubleshooting

### Build fails with "Could not find the build directory"
- Make sure to run `npm run build` before running the production server
- Check that `dist/public` directory exists after building

### Port 5000 already in use
```bash
# Change port in .env or kill the process using port 5000
lsof -i :5000       # Find process on macOS/Linux
netstat -ano | findstr :5000  # Find process on Windows
```

### Database connection errors
- Ensure PostgreSQL is running
- Check `DATABASE_URL` in `.env.local`
- Run `npm run db:push` to setup tables

## Contributing

1. Create a feature branch (`git checkout -b feature/amazing-feature`)
2. Commit changes (`git commit -m 'Add amazing feature'`)
3. Push to branch (`git push origin feature/amazing-feature`)
4. Open a Pull Request

## License

MIT License - see LICENSE file for details

## Support

For issues and questions, please open an issue on GitHub.
