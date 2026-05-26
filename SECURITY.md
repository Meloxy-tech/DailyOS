# SECURITY.md
# Security Policy

## Reporting a Vulnerability

If you discover a security vulnerability, please email security@dailyos.dev

**Do not** disclose vulnerabilities publicly until we've addressed them.

## Security Measures

### Authentication
- Email/password via Supabase
- Google OAuth 2.0
- Secure session tokens
- Password reset with email verification

### Data Protection
- HTTPS encryption in transit
- PostgreSQL with encrypted sensitive data
- Secure environment variables
- No sensitive data in localStorage

### API Security
- CORS configuration
- CSRF protection
- Rate limiting
- Input validation
- SQL injection prevention (Prisma ORM)

### Infrastructure
- Vercel with automatic HTTPS
- DDoS protection via Vercel
- Automated dependency updates
- Security scanning with CodeQL
