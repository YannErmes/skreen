# Vercel Deployment Guide

## Pre-Deployment Checklist

This project is now configured for Vercel deployment. Follow these steps to deploy:

### 1. Environment Variables
Set up the following environment variables in Vercel project settings:

- `SUPABASE_PUBLISHABLE_KEY` - Your Supabase publishable key
- `SUPABASE_URL` - Your Supabase project URL  
- `VITE_SUPABASE_PROJECT_ID` - Your Supabase project ID
- `VITE_SUPABASE_PUBLISHABLE_KEY` - Your Supabase publishable key (client-side)
- `VITE_SUPABASE_URL` - Your Supabase project URL (client-side)

Reference: See `.env.example` for the format.

### 2. Build Configuration
- **Build Command**: `npm run build`
- **Output Directory**: `dist`
- **Install Command**: `npm install`

These are already configured in `vercel.json`.

### 3. Deployment Steps

1. Push your code to GitHub (or your Git provider)
2. Go to [Vercel Dashboard](https://vercel.com/dashboard)
3. Click "Add New..." → "Project"
4. Import your repository
5. Accept default settings (the `vercel.json` will be used automatically)
6. Add your environment variables in Project Settings → Environment Variables
7. Deploy

### 4. Node.js Version
The project requires Node.js 20 or higher. This is already specified in `package.json` under `engines`.

### 5. Key Files for Deployment
- `vercel.json` - Vercel configuration
- `.vercelignore` - Files to exclude from deployment
- `.env.example` - Environment variables template
- `package.json` - Build scripts and dependencies

## Troubleshooting

### Build Fails with Type Errors
Run `npm install` and `npm run build` locally to verify the build works:
```bash
npm install
npm run build
```

### Environment Variables Not Loading
Make sure all `VITE_*` prefixed variables are added to Vercel. Vite requires the `VITE_` prefix for client-side environment variables.

### WebSocket Connection Issues  
If the signaling server uses WebSockets, ensure:
- Your Vercel project allows WebSocket connections (they're enabled by default)
- The signaling URL is properly configured on the client side

## Local Testing Before Deployment

```bash
# Install dependencies
npm install

# Build the project
npm run build

# Preview the build
npm run preview
```

## Important Notes

- This is a TanStack Start full-stack application
- The build outputs to the `dist` directory
- Make sure all Supabase credentials are valid and don't commit `.env`
- Test locally with `npm run build` before deploying
