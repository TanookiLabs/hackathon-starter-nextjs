Deploy the app: commit, push to main, then push to the production branch which triggers Vercel to build and deploy. Database schema migrations run automatically during the Vercel build.

This project uses two branches:
- `main` — where you work. Pushing here does NOT deploy.
- `production` — what Vercel deploys. Pushing here triggers a build.

Steps:

1. If prisma/schema.prisma has changed, run `npm run db:push` to sync the local dev database first
2. Commit all changes to git with a descriptive commit message that summarizes what was changed
3. Push to main: `git push origin main`
4. Push main to production to trigger the deploy: `git push origin main:production`
5. Confirm the Vercel deployment is building. Show the deployment URL when done.
6. Explain: Vercel runs `prisma generate && prisma db push && next build`, so the production database schema is updated automatically during every deploy. No manual migration step needed.
7. Remind the user: make sure their environment variables are set in Vercel Settings (AUTH_SECRET, DATABASE_URL, DIRECT_URL). The DATABASE_URL and DIRECT_URL in Vercel should point to the production Supabase project, not the dev one.
