# Deployment

This project is a static, single-file HTML app (`school_management_system.html`) with no build step. It is hosted on **Vercel**, deployed via Vercel's GitHub integration.

## How deploys happen

- The GitHub repo (`sengchhunyeang/school-ai-build-system`, branch `main`) is connected to a Vercel project.
- Every push to `main` triggers an automatic production deploy — no manual build or CLI step is required.
- Pushes to other branches / pull requests get their own Vercel preview deployments.

## Routing

`vercel.json` rewrites the site root to the app file, since Vercel otherwise has no `index.html` to serve by default:

```json
{
  "rewrites": [
    { "source": "/", "destination": "/school_management_system.html" }
  ]
}
```

Visiting the deployed domain's `/` loads `school_management_system.html` directly. No other routes are configured.

## First-time project setup (if reconnecting)

1. In the Vercel dashboard, "Add New Project" → import the `sengchhunyeang/school-ai-build-system` GitHub repo.
2. Framework preset: **Other** (no build command, no output directory — it's static files served as-is).
3. Leave build/output settings blank; Vercel just serves the repo contents with the `vercel.json` rewrite applied.
4. Deploy — subsequent pushes to `main` redeploy automatically.

## Manual deploy (optional, via Vercel CLI)

```bash
npm i -g vercel
vercel login
vercel --prod
```

Run this from the repo root. Only needed if you want to deploy without pushing to GitHub (e.g. testing local changes before committing).

## Checking deploy status

Check the **Deployments** tab of the project in the Vercel dashboard for build/deploy logs and the live production URL.
