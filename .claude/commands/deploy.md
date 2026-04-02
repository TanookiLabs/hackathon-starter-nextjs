Deploy the app: commit, push to GitHub, then deploy to Vercel with the CLI.

Steps:

1. If prisma/schema.prisma has changed, run `npm run db:push` to sync the local dev database first
2. Commit all changes to git with a descriptive commit message that summarizes what was changed
3. Push to GitHub: `git push origin main`
4. Deploy to Vercel: `npx vercel --prod`
5. Show the deployment URL when done.
6. Explain: Vercel runs `prisma generate && prisma db push && next build`, so the production database schema is updated automatically during every deploy. No manual migration step needed.
7. Remind the user: make sure their environment variables are set in Vercel (AUTH_SECRET, DATABASE_URL, DIRECT_URL). They can check with `npx vercel env ls` and add missing ones with `npx vercel env add <NAME> production`.
