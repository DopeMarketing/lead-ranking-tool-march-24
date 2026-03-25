# Lead Ranking Tool

Intelligent lead scoring and ranking system that aggregates data from multiple marketing channels to prioritize sales opportunities.

## What This Does

This tool automatically imports leads from HubSpot and scores them based on engagement across email, social media, and advertising platforms. It ranks prospects by conversion probability and triggers automated follow-up sequences for high-scoring leads.

**Built for:** Personal use by marketing teams and sales professionals

## Tech Stack

- **Frontend:** Next.js 15, TypeScript, Tailwind CSS
- **Backend:** Supabase (PostgreSQL + Auth)
- **Integrations:** HubSpot, Meta Ads, TikTok Ads, Google Ads, Twilio, ActiveCampaign, Zapier, Google Analytics, ChatGPT, Claude
- **Deployment:** Vercel

## Prerequisites

- Node.js 18+
- npm or yarn
- Supabase CLI
- Git

## Local Setup

1. **Clone the repository**
   bash
   git clone <repository-url>
   cd lead-ranking-tool
   

2. **Install dependencies**
   bash
   npm install
   

3. **Set up environment variables**
   bash
   cp .env.example .env.local
   
   Fill in the required environment variables (see table below)

4. **Start Supabase**
   bash
   supabase start
   

5. **Run the development server**
   bash
   npm run dev
   

6. **Open your browser**
   Navigate to [http://localhost:3000](http://localhost:3000)

## Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `NEXT_PUBLIC_SUPABASE_URL` | Supabase project URL | Yes |
| `NEXT_PUBLIC_SUPABASE_ANON_KEY` | Supabase anonymous key | Yes |
| `SUPABASE_SERVICE_ROLE_KEY` | Supabase service role key (server-side) | Yes |
| `HUBSPOT_API_KEY` | HubSpot private app access token | Yes |
| `HUBSPOT_CLIENT_ID` | HubSpot OAuth client ID | Yes |
| `HUBSPOT_CLIENT_SECRET` | HubSpot OAuth client secret | Yes |
| `META_ACCESS_TOKEN` | Meta (Facebook/Instagram) API access token | Yes |
| `TIKTOK_ACCESS_TOKEN` | TikTok Ads API access token | Yes |
| `GOOGLE_ADS_CLIENT_ID` | Google Ads API client ID | Yes |
| `GOOGLE_ADS_CLIENT_SECRET` | Google Ads API client secret | Yes |
| `GOOGLE_ADS_REFRESH_TOKEN` | Google Ads API refresh token | Yes |
| `TWILIO_ACCOUNT_SID` | Twilio account SID | Yes |
| `TWILIO_AUTH_TOKEN` | Twilio auth token | Yes |
| `ACTIVECAMPAIGN_API_URL` | ActiveCampaign API base URL | Yes |
| `ACTIVECAMPAIGN_API_KEY` | ActiveCampaign API key | Yes |
| `OPENAI_API_KEY` | OpenAI (ChatGPT) API key | Yes |
| `ANTHROPIC_API_KEY` | Anthropic (Claude) API key | Yes |
| `ZAPIER_WEBHOOK_SECRET` | Zapier webhook verification secret | Yes |
| `GOOGLE_ANALYTICS_PROPERTY_ID` | Google Analytics 4 property ID | Yes |
| `NEXTAUTH_SECRET` | NextAuth.js secret key | Yes |
| `NEXTAUTH_URL` | Application base URL | Yes |

## Database Setup

The database schema is automatically applied when you run `supabase start`. The following tables are created:

- `users` - User authentication and profiles
- `organizations` - Company/team data
- `user_organizations` - User-organization relationships
- `leads` - Lead contact information and metadata
- `lead_scores` - Historical scoring data
- `lead_activities` - Engagement tracking
- `scoring_rules` - Configurable scoring criteria
- `follow_up_sequences` - Automated email sequences
- `follow_up_executions` - Sequence execution tracking
- `integration_configs` - API connection settings
- `sync_jobs` - Data synchronization status
- `reports` - Generated report data
- `ai_analyses` - AI-powered lead insights

## Deploy to Vercel

1. **Connect your repository to Vercel**
   - Import your project in the Vercel dashboard
   - Connect your GitHub/GitLab repository

2. **Configure environment variables**
   - Add all environment variables from the table above
   - Use production values for API keys and database URLs

3. **Deploy**
   - Vercel will automatically deploy on every push to main
   - Database migrations run automatically via Supabase

## Project Structure


├── app/                    # Next.js 15 app directory
│   ├── (auth)/            # Authentication routes
│   ├── (dashboard)/       # Protected dashboard routes
│   ├── api/               # API routes and webhooks
│   └── globals.css        # Global styles
├── components/            # Reusable UI components
├── lib/                   # Business logic and utilities
├── db/                    # Database access layer
├── actions/               # Server actions
├── types/                 # TypeScript type definitions
├── hooks/                 # Custom React hooks
├── supabase/              # Database schema and migrations
└── public/                # Static assets


## Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run start` - Start production server
- `npm run lint` - Run ESLint
- `npm run type-check` - Run TypeScript compiler
- `supabase start` - Start local Supabase
- `supabase stop` - Stop local Supabase
- `supabase status` - Check Supabase status

## Support

This is a personal project. For questions or issues, please refer to the documentation or create an issue in the repository.