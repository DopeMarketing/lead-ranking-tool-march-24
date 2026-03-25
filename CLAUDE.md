# CLAUDE.md - Lead Ranking Tool Development Guide

## Project Overview
A lead scoring and ranking system that integrates with HubSpot, social media platforms, and marketing tools to automatically score leads based on multi-channel engagement data. The system uses AI to predict conversion probability and triggers automated follow-up sequences for high-scoring prospects.

## Tech Stack
- **Framework:** Next.js 15 (App Router)
- **Database:** Supabase (PostgreSQL + Auth + RLS)
- **Language:** TypeScript (strict mode)
- **Styling:** Tailwind CSS
- **Deployment:** Vercel
- **Integrations:** HubSpot, Meta Ads, TikTok Ads, Google Ads, Twilio, ActiveCampaign, Zapier, Google Analytics, ChatGPT, Claude

## Folder Structure

app/
├── (auth)/                 # Auth routes: login, signup, forgot-password
├── (dashboard)/            # Protected routes: dashboard, leads, scoring, etc.
├── api/                    # API routes and webhook endpoints
│   ├── webhooks/          # External service webhooks
│   └── scoring/           # Internal scoring API
└── globals.css            # Global Tailwind styles

components/
├── ui/                    # Shadcn/ui components
├── auth/                  # Authentication components
├── dashboard/             # Dashboard-specific components
├── leads/                 # Lead management components
└── integrations/          # Integration configuration components

lib/
├── auth.ts               # Authentication utilities
├── scoring.ts            # Lead scoring algorithms
├── integrations/         # API clients for external services
├── ai/                   # ChatGPT/Claude integration
├── utils.ts              # General utilities
└── validations.ts        # Zod schemas

db/
├── queries/              # Database query functions
├── mutations/            # Database mutation functions
└── types.ts              # Database type definitions

actions/
├── auth.ts               # Authentication server actions
├── leads.ts              # Lead management server actions
├── scoring.ts            # Scoring server actions
└── integrations.ts       # Integration server actions

types/
├── database.ts           # Supabase generated types
├── integrations.ts       # External API types
└── app.ts               # Application-specific types

hooks/
├── use-auth.ts          # Authentication hooks
├── use-leads.ts         # Lead data hooks
└── use-integrations.ts  # Integration status hooks

supabase/
├── migrations/          # Database migrations
├── seed.sql            # Initial data
└── config.toml         # Supabase configuration


## Coding Conventions

### TypeScript
- Strict mode enabled
- Use interfaces for object shapes
- Use type unions for specific values
- Export types from dedicated type files

### React/Next.js
- Server Components by default
- Use Client Components only when needed (interactivity, hooks, browser APIs)
- Prefer Server Actions over API routes for mutations
- Use `use server` directive for server actions

### Data Access
- Database queries ONLY in `/db` directory
- Use Supabase client with Row Level Security
- Never expose service role key to client
- Business logic in `/lib` and `/actions`

### Security
- No API keys or secrets in client components
- All environment variables prefixed appropriately
- Use RLS policies for data access control
- Validate inputs with Zod schemas

## Current State: Scaffold Complete

The following has been built in this scaffold:

✅ **Database Schema** (13 tables)
- Users, organizations, leads, scoring system
- Integration configurations and sync tracking
- Follow-up sequences and AI analysis storage

✅ **Authentication System**
- Supabase Auth with role-based access
- Owner, Analyst, Reviewer roles configured
- Protected route middleware

✅ **Route Structure** (17 routes)
- Public: landing, pricing, auth pages
- Protected: dashboard, leads, scoring, integrations
- API: webhooks and internal endpoints

✅ **Integration Stubs**
- HubSpot, Meta, TikTok, Google Ads API clients
- Twilio, ActiveCampaign, Zapier webhooks
- ChatGPT/Claude AI integration setup

✅ **UI Foundation**
- Tailwind CSS configuration
- Shadcn/ui component library
- Responsive design system

## What to Build Next: v1 Features

### 1. HubSpot CRM Integration
- Real-time lead import with automatic sync
- Contact deduplication logic
- Webhook handling for CRM updates

### 2. Multi-Channel Scoring Engine
- Email engagement scoring (opens, clicks)
- Social media interaction tracking
- Form submission data weighting
- Configurable scoring rules interface

### 3. Lead Ranking Dashboard
- Conversion probability display
- Source channel filtering
- Lead list with sortable scores
- Visual score distribution charts

### 4. Automated Follow-up System
- Configurable score thresholds
- Email sequence builder
- Trigger execution tracking
- Personalization token system

### 5. Cross-Platform Engagement Tracking
- Facebook/Instagram interaction aggregation
- TikTok engagement data collection
- Google Ads interaction tracking
- Unified lead profile views

### 6. AI-Powered Lead Analysis
- Communication pattern analysis
- Intent signal detection
- Lead quality predictions
- Automated insights generation

## Never Touch Rules

🚫 **Never modify without explicit instruction:**
- `.env` files (security risk)
- Migration files in `/supabase/migrations/`
- RLS policies without security review
- Service role key usage patterns

🚫 **Never commit:**
- Environment variables with real values
- API keys or secrets
- Local Supabase configuration
- Personal data or test credentials

## How to Work on This Project

### Before Starting Any Session
1. **Read this file completely** - Always start here
2. **Check the current branch** - Ensure you're on the right branch
3. **Review recent commits** - Understand what was last worked on
4. **Run the project locally** - Ensure everything works

### During Development
1. **Focus on one feature at a time** - Don't mix concerns
2. **Write TypeScript first** - Types before implementation
3. **Test as you go** - Run the app frequently
4. **Follow the folder structure** - Keep code organized

### Before Committing
1. **Run build check:** `npm run build`
2. **Fix any TypeScript errors**
3. **Test the feature works end-to-end**
4. **Use conventional commits:** `feat:`, `fix:`, `refactor:`, etc.

### Commit Strategy
- **Small, focused commits** - One logical change per commit
- **Clear commit messages** - Explain what and why
- **Commit frequently** - Don't let changes pile up
- **Document technical debt** - Add to TECHNICAL_DEBT.md

### Working with Integrations
- **Start with mock data** - Don't require real API keys initially
- **Build incrementally** - One integration at a time
- **Handle rate limits** - Implement proper backoff
- **Log everything** - Detailed logging for debugging

### AI Integration Guidelines
- **Sanitize inputs** - Never send sensitive data to AI
- **Handle failures gracefully** - AI services can be unreliable
- **Cache responses** - Avoid redundant API calls
- **Monitor costs** - Track API usage and expenses

Remember: This is Claude Code development - work iteratively, test frequently, and document everything for the next session.