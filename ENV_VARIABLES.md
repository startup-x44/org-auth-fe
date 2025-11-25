# Frontend Environment Variables

This document describes the environment variables used by the frontend application.

## Required Variables

### `NEXT_PUBLIC_API_URL`
- **Description**: The base URL for the authentication service API
- **Development**: `http://localhost:8080`
- **Production**: Your production API URL or empty string for same-origin requests
- **Required**: Yes
- **Public**: Yes (prefixed with `NEXT_PUBLIC_`)

## Optional Variables

### `NODE_ENV`
- **Description**: The Node.js environment
- **Values**: `development`, `production`, `test`
- **Default**: Set automatically by Next.js
- **Required**: No (automatically set)

### Feature Flags

#### `NEXT_PUBLIC_ENABLE_OAUTH`
- **Description**: Enable/disable OAuth2 features
- **Default**: `true`
- **Required**: No

#### `NEXT_PUBLIC_ENABLE_API_KEYS`
- **Description**: Enable/disable API key management features
- **Default**: `true`
- **Required**: No

### Application Metadata

#### `NEXT_PUBLIC_APP_NAME`
- **Description**: Application name displayed in the UI
- **Default**: `BlockSure Auth`
- **Required**: No

#### `NEXT_PUBLIC_APP_VERSION`
- **Description**: Application version
- **Default**: `1.0.0`
- **Required**: No

## Environment Files

The project uses multiple environment files for different scenarios:

- **`.env.local`**: Local development overrides (not committed to git)
- **`.env.example`**: Template file showing all available variables
- **`.env.production`**: Production-specific configuration

## Setup Instructions

1. Copy the example file to create your local environment file:
   ```bash
   cp .env.example .env.local
   ```

2. Update `NEXT_PUBLIC_API_URL` in `.env.local` to match your backend API:
   ```
   NEXT_PUBLIC_API_URL=http://localhost:8080
   ```

3. (Optional) Configure additional variables as needed

## Usage in Code

Environment variables are used throughout the application:

### API Configuration
The API URL is used in:
- `/src/lib/auth.ts` - Main authentication service
- `/src/lib/api/admin-api.ts` - Admin API calls
- `/src/lib/api/superadmin.ts` - Superadmin API calls
- `/src/app/oauth/authorize/page.tsx` - OAuth authorization flow
- Other API-related components

### Example Usage
```typescript
const API_BASE = process.env.NEXT_PUBLIC_API_URL || 'http://localhost:8080';
```

## Security Notes

⚠️ **Important**: Only variables prefixed with `NEXT_PUBLIC_` are exposed to the browser. Never store sensitive information (API keys, secrets) in `NEXT_PUBLIC_` variables.

## Deployment

When deploying to production:

1. Set `NEXT_PUBLIC_API_URL` to your production API URL
2. Set `NODE_ENV=production`
3. Configure any additional production-specific variables
4. Never commit `.env.local` to version control

## Troubleshooting

### API calls failing
- Verify `NEXT_PUBLIC_API_URL` points to the correct backend
- Check if backend is running on the specified URL
- Ensure CORS is properly configured on the backend

### Environment variables not updating
- Restart the Next.js development server after changing `.env` files
- Clear browser cache if values seem stale
- Check that variables are prefixed with `NEXT_PUBLIC_` for client-side use
