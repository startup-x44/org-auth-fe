# Frontend - Auth ServiceThis is a [Next.js](https://nextjs.org) project bootstrapped with [`create-next-app`](https://nextjs.org/docs/app/api-reference/cli/create-next-app).



Next.js frontend application for the Authentication Service.## Getting Started



## PrerequisitesFirst, run the development server:



- Node.js v18+ (recommended: v22.21.1)```bash

- Yarn package managernpm run dev

- Backend API running on `http://localhost:8080` (or configured URL)# or

yarn dev

## Quick Start# or

pnpm dev

### 1. Install Dependencies# or

bun dev

```bash```

yarn install

```Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.



### 2. Environment SetupYou can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.



Copy the example environment file and configure it:This project uses [`next/font`](https://nextjs.org/docs/app/building-your-application/optimizing/fonts) to automatically optimize and load [Geist](https://vercel.com/font), a new font family for Vercel.



```bash## Learn More

cp .env.example .env.local

```To learn more about Next.js, take a look at the following resources:



Edit `.env.local` and set your environment variables:- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.

- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

```env

NEXT_PUBLIC_API_URL=http://localhost:8080You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js) - your feedback and contributions are welcome!

NODE_ENV=development

```## Deploy on Vercel



See [ENV_VARIABLES.md](./ENV_VARIABLES.md) for detailed environment variable documentation.The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.



### 3. Run Development ServerCheck out our [Next.js deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying) for more details.


```bash
yarn dev
```

The application will be available at [http://localhost:3000](http://localhost:3000)

### 4. Build for Production

```bash
yarn build
```

### 5. Start Production Server

```bash
yarn start
```

## Available Scripts

- **`yarn dev`** - Start development server with hot reload
- **`yarn build`** - Build optimized production bundle
- **`yarn start`** - Start production server (requires build first)
- **`yarn lint`** - Run ESLint to check code quality

## Project Structure

```
frontend/
├── public/              # Static assets
├── src/
│   ├── app/            # Next.js App Router pages
│   │   ├── auth/       # Authentication pages (login, register, etc.)
│   │   ├── oauth/      # OAuth authorization flow
│   │   ├── superadmin/ # Superadmin dashboard pages
│   │   └── user/       # User dashboard pages
│   ├── components/     # React components
│   │   ├── layout/     # Layout components
│   │   └── ui/         # Reusable UI components
│   ├── contexts/       # React contexts (AuthContext, etc.)
│   ├── hooks/          # Custom React hooks
│   ├── lib/            # Utility libraries
│   │   ├── api/        # API client functions
│   │   ├── auth.ts     # Authentication service
│   │   └── csrf.ts     # CSRF token management
│   ├── providers/      # React providers
│   ├── stores/         # State management
│   ├── types/          # TypeScript type definitions
│   └── utils/          # Utility functions
├── .env.local          # Local environment variables (not committed)
├── .env.example        # Environment variables template
├── .env.production     # Production environment variables
└── ENV_VARIABLES.md    # Environment variables documentation
```

## Features

### Authentication
- User registration and login
- Email verification
- Password reset
- Multi-organization support
- Organization selection flow

### OAuth 2.1 + PKCE
- OAuth authorization flow
- PKCE (Proof Key for Code Exchange)
- Client application management
- Scope-based permissions

### Superadmin Features
- User management
- Organization management
- RBAC (Role-Based Access Control)
- System permissions
- Dashboard and analytics

### User Features
- Profile management
- Organization membership
- API key management
- OAuth2 application management
- Role and permission viewing

## Configuration

### API URL

The frontend communicates with the backend API. Configure the API URL in `.env.local`:

**Development:**
```env
NEXT_PUBLIC_API_URL=http://localhost:8080
```

**Production (same origin):**
```env
NEXT_PUBLIC_API_URL=
```

**Production (different domain):**
```env
NEXT_PUBLIC_API_URL=https://api.yourdomain.com
```

### CSRF Protection

The application uses CSRF tokens for secure state-changing requests. The CSRF implementation is in `src/lib/csrf.ts`.

## Development

### Running with Backend

1. Start the backend server (in project root):
```bash
cd ..
./dev.sh  # or your backend start command
```

2. Start the frontend (in a new terminal):
```bash
cd frontend
yarn dev
```

3. Access the application at http://localhost:3000

### Hot Reload

Next.js development server supports hot module replacement (HMR). Changes to code will automatically reload in the browser.

### TypeScript

The project uses TypeScript for type safety. TypeScript errors will be shown during development and build.

## Troubleshooting

### API Connection Issues

**Problem:** API requests fail with CORS errors
- **Solution:** Ensure backend CORS is configured to allow `http://localhost:3000`

**Problem:** 401 Unauthorized errors
- **Solution:** Check that tokens are being stored correctly in localStorage
- Clear browser localStorage and login again

### Build Issues

**Problem:** Build fails with font errors
- **Solution:** Fonts have been configured to use Inter and JetBrains Mono from Google Fonts
- Check internet connection if build fails

**Problem:** TypeScript errors
- **Solution:** Run `yarn` to ensure all dependencies are installed
- Check `tsconfig.json` configuration

### Development Server Issues

**Problem:** Port 3000 already in use
- **Solution:** Kill the process using port 3000 or use a different port:
  ```bash
  yarn dev -p 3001
  ```

**Problem:** Environment variables not updating
- **Solution:** Restart the development server after changing `.env` files
- Clear browser cache if needed

## Tech Stack

- **Framework:** Next.js 16.0.3 (App Router)
- **Runtime:** React 19
- **Language:** TypeScript 5
- **Styling:** Tailwind CSS 4
- **State Management:** Zustand
- **Data Fetching:** TanStack Query (React Query)
- **HTTP Client:** Axios
- **UI Components:** Radix UI
- **Notifications:** Sonner
- **Theme:** next-themes

## License

Proprietary - BlockSure Auth Service
