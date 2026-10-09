<div align="center">

<img src="./assets/joinclubs.logo.png" alt="JoinClubs logo" width="260" />

# JoinClubs

### Find your club. Build your squad.

A bilingual matchmaking and recruitment platform built for the<br />
**EA SPORTS FC Pro Clubs** community.

[![English](https://img.shields.io/badge/EN-ENGLISH-2563EB?style=for-the-badge)](#internationalization)
[![Português](https://img.shields.io/badge/PT--BR-PORTUGUÊS-16A34A?style=for-the-badge)](#internationalization)

**[Open JoinClubs](https://joinclubs.vercel.app/pt)**

</div>

## About the project

JoinClubs was designed to solve a common Pro Clubs problem: finding the right people to play with without relying on scattered group chats, random drop-in matches, or incomplete recruitment posts.

Players can present how and when they play. Teams can publish exactly what they need. Both sides can search with focused filters, compare profiles, send requests, and manage accepted connections in one place.

> JoinClubs is an independent community project and is not affiliated with or endorsed by Electronic Arts.

## Main features

### Player and team discovery

- Separate directories for available players and recruiting teams.
- Shareable searches with filters for position, platform, region, nationality, language, level, archetype, and game edition.
- Detailed cards and profile modals designed for quick comparison.
- Support for EA SPORTS FC 26 and FC 27 profile data.

### Rich Pro Clubs profiles

- Main and secondary positions, playing region, platform, division, language, nationality, and availability.
- Player playstyle, schedule, gametags, Discord contact, and connection notes.
- Up to three player archetypes with level progression.
- Optional YouTube highlight with privacy-enhanced, click-to-load playback.
- Team openings with desired positions and archetypes.

### Requests and connections

- Player-to-player friend requests.
- Team invitations, join requests, and direct recruitment flows.
- Dedicated **Requests** and **Connections** areas with status feedback and navigation indicators.
- Accepted-contact management, removal actions, and optional email or Discord notifications.

### Authentication and account management

- Email and password authentication.
- Google and Discord OAuth through Supabase Auth.
- Cloudflare Turnstile verification on email/password registration and sign-in.
- Linked-provider management, password and email settings, and account deletion.
- Game-edition preference stored per account.

### Privacy, safety, and moderation

- Independent visibility controls for Discord and gametags.
- Contact information available publicly only when the owner allows it, or through an accepted connection.
- In-app profile reporting with evidence links and moderation review.
- Account suspension support and a protected administration area.
- Persistent per-account anti-spam limits for reports, profile changes, privacy controls, invitations, requests, and other sensitive actions.
- User-facing cooldown messages that show when a blocked action can be attempted again.
- Localized privacy and data-protection notice.

### International experience

- Complete interface in English and Brazilian Portuguese.
- Localized routes, metadata, validation, nationalities, filters, and dynamic messages.
- Route-preserving language switcher with a remembered language preference.
- Responsive dark interface with reduced-motion support and accessible interaction states.

## How it works

1. **Create a profile** — add the information that matters in Pro Clubs: positions, platform, archetypes, level, region, language, and schedule.
2. **Find the right fit** — use focused filters to discover compatible players or teams.
3. **Connect and play** — send an invitation or request, accept the connection, and access the contact details shared with you.

## Tech stack

<div align="center">

[![Next.js](https://img.shields.io/badge/NEXT.JS_16-000000?style=for-the-badge&logo=nextdotjs&logoColor=white)](https://nextjs.org/)
[![React](https://img.shields.io/badge/REACT_19-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TYPESCRIPT-3178C6?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/TAILWIND_CSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)
[![Supabase](https://img.shields.io/badge/SUPABASE-3FCF8E?style=for-the-badge&logo=supabase&logoColor=white)](https://supabase.com/)
[![PostgreSQL](https://img.shields.io/badge/POSTGRESQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![next-intl](https://img.shields.io/badge/NEXT--INTL-1E293B?style=for-the-badge&logo=translate&logoColor=white)](https://next-intl.dev/)
[![Lucide](https://img.shields.io/badge/LUCIDE-F56565?style=for-the-badge&logo=lucide&logoColor=white)](https://lucide.dev/)
[![ESLint](https://img.shields.io/badge/ESLINT-4B32C3?style=for-the-badge&logo=eslint&logoColor=white)](https://eslint.org/)
[![Vercel](https://img.shields.io/badge/VERCEL-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://vercel.com/)
[![Cloudflare Turnstile](https://img.shields.io/badge/CLOUDFLARE_TURNSTILE-F38020?style=for-the-badge&logo=cloudflare&logoColor=white)](https://developers.cloudflare.com/turnstile/)

</div>

| Layer | Technologies |
| --- | --- |
| Frontend | Next.js 16 App Router, React 19, TypeScript, Tailwind CSS |
| Backend | Next.js Server Actions, Supabase Auth, Supabase SSR, Cloudflare Turnstile |
| Data | PostgreSQL, Row Level Security, database views, functions, and triggers |
| Internationalization | next-intl with typed and localized navigation |
| UI | Lucide icons, responsive layouts, motion preferences, custom FC archetype assets |
| Quality | ESLint, strict TypeScript, PGlite database tests, smoke tests |
| Deployment | Vercel and Supabase |

## Architecture and security

- The application uses the Next.js App Router with Server Components and Server Actions.
- Authentication, PostgreSQL data, and Row Level Security are provided by Supabase.
- Directory reads use restricted database views instead of exposing base tables directly.
- Sensitive mutations are validated on the server and protected by ownership and state-transition rules.
- Contact details are filtered according to profile settings and connection state.
- OAuth callbacks use PKCE, while provider credentials and administrative access remain server-side.
- Turnstile tokens are validated server-side before email/password registration or sign-in proceeds.
- Persistent action limits are tracked per account and action, with database triggers protecting direct writes from interface bypasses.
- Reports, connection uniqueness, cooldowns, and archetype limits are also enforced at the database level.

## Internationalization

JoinClubs uses English as its default language and Brazilian Portuguese as its second locale. Adding another language only requires registering the locale and providing its message file.

| Language | Prefix | Examples |
| --- | --- | --- |
| English | `/en` | `/en/players`, `/en/teams`, `/en/privacy` |
| Brazilian Portuguese | `/pt` | `/pt/jogadores`, `/pt/times`, `/pt/privacidade` |

The language switcher preserves the current route, query parameters, and hash while storing the chosen locale for future visits.

## Local development

### Requirements

- Node.js 20.9 or newer
- npm
- A Supabase project

### Setup

```bash
git clone https://github.com/kiellzz/joinclubs.git
cd joinclubs
npm install
```

Copy `.env.example` to `.env.local`, add the required Supabase credentials, and install the database schema from the `supabase` directory. Then start the development server:

```bash
npm run dev
```

The application will be available at [http://localhost:3000](http://localhost:3000).

### Environment variables

```dotenv
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
SUPABASE_SECRET_KEY=
NEXT_PUBLIC_SITE_URL=http://localhost:3000
NEXT_PUBLIC_TURNSTILE_SITE_KEY=
TURNSTILE_SECRET_KEY=
SHOW_COMMUNITY_STATS=false
```

Server secrets must never use the `NEXT_PUBLIC_` prefix.

## Deployment

The production application runs at [joinclubs.vercel.app](https://joinclubs.vercel.app/pt) on Vercel with Supabase. The complete deployment sequence, environment-variable list, authentication URLs, migration safety notes, and Turnstile setup are documented in [DEPLOYMENT.md](./DEPLOYMENT.md).

## Verification

```bash
npm run typecheck
npm run lint
npm run test:db
npm run test:reset
npm run test:archetypes
npm run test:notifications
npm run build
```

With the local development server running, `npm run test:smoke` verifies localized pages, redirects, OAuth callback handling, metadata files, and image optimization.

The project includes strict TypeScript checks, linting, embedded PostgreSQL tests, notification-routing tests, smoke tests, and production build verification.

## Project status

JoinClubs is live in public beta and remains under active development.

---

<div align="center">

Built by [@kiellzz](https://github.com/kiellzz)

</div>
