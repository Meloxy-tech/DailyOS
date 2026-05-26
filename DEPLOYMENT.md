# DEPLOYMENT.md

## Pre-Deployment Checklist

### Environment Setup
- [ ] `.env.local` configured with all required variables
- [ ] Database migrations run: `npm run db:push`
- [ ] Database seeded: `npm run db:seed`
- [ ] All secrets in GitHub (VERCEL_TOKEN, etc.)

### Code Quality
- [ ] No linting errors: `npm run lint`
- [ ] Types pass: `npm run type-check`
- [ ] Build succeeds: `npm run build`
- [ ] Tests pass: `npm test`

### Security
- [ ] Dependencies up to date: `npm audit`
- [ ] No sensitive data in code
- [ ] Environment variables not committed
- [ ] CORS properly configured

### Performance
- [ ] Build size reasonable
- [ ] Images optimized
- [ ] No console errors/warnings
- [ ] Lighthouse score > 80

## Deploying to Vercel

### Initial Setup
1. Create Vercel account: https://vercel.com
2. Connect GitHub repository
3. Add environment variables in Vercel dashboard
4. Deploy

### Environment Variables Needed
