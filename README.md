# QC Property Intelligence

**Quebec Tax Sale Property Intelligence Platform**

A powerful web application designed to provide actionable insights into Quebec's property tax sales market. This app aggregates data from municipal sources, provides interactive maps, AI-powered analysis, and tools for investors and professionals to identify opportunities in tax sale properties.

## About the Project

This project was built following and improving upon the "Quebec Tax Sale App Builder Guide" shared in a previous Grok conversation. Key improvements include:

- Modern, type-safe full-stack architecture with Next.js 15 and TypeScript
- Server-side rendering and React Server Components for performance
- Integrated AI analysis using xAI's Grok models for property summaries, risk assessment, and investment potential (with appropriate disclaimers)
- Robust scraping framework with Playwright for handling dynamic municipal websites
- Geospatial database support with PostGIS ready
- Comprehensive CI/CD pipeline with GitHub Actions
- Responsive, accessible UI with shadcn/ui and Tailwind
- Emphasis on data privacy, ethical scraping, and legal compliance

## Key Features

- **Interactive Map**: Visualize tax sale properties across Quebec municipalities using Leaflet/OpenStreetMap.
- **Smart Search & Filters**: Filter by city, estimated value, redemption period, property type, risk score, etc.
- **Property Profiles**: Detailed pages with historical data, comparable sales, tax history, and AI-generated insights.
- **Alerts & Notifications**: Set up custom alerts for new listings in specific areas or matching criteria.
- **Analytics Dashboard**: Trends, success rates of tax sale investments, market heatmaps.
- **Data Export**: Download reports in PDF, CSV, or Excel.
- **Admin Tools**: For managing data ingestion jobs and user management.

## Tech Stack

- **Framework**: Next.js 15 (App Router) with TypeScript
- **Styling**: Tailwind CSS + shadcn/ui components
- **Maps**: Leaflet.js with React-Leaflet
- **Database**: PostgreSQL (with PostGIS extension recommended for geospatial queries)
- **ORM**: Prisma or Drizzle ORM
- **Authentication**: Auth.js (NextAuth v5)
- **Scraping & Jobs**: Playwright (Node.js) or Python scripts triggered via API routes or external workers (e.g. Trigger.dev or GitHub Actions scheduled)
- **AI Integration**: xAI Grok API (or OpenAI compatible) for natural language property analysis and recommendations
- **State Management**: TanStack Query (React Query) for client-side data fetching
- **Forms**: React Hook Form + Zod validation
- **Deployment**: Vercel (frontend + serverless functions) or self-hosted with Docker
- **Testing**: Jest + React Testing Library, Playwright for E2E
- **CI/CD**: GitHub Actions for lint, type check, test, build, and preview deployments

## Project Structure (Improved)

```
qc-property-intelligence/
├── app/                  # Next.js App Router
│   ├── (auth)/           # Auth related routes
│   ├── dashboard/        # Protected dashboard
│   ├── properties/       # Property listing and detail pages
│   ├── map/              # Interactive map view
│   ├── api/              # API routes for data, scraping jobs, AI
│   ├── layout.tsx
│   └── page.tsx          # Landing page
├── components/           # Reusable UI components (shadcn/ui based)
├── lib/                  # Utilities, db client, AI client, scraper utils
├── prisma/               # Prisma schema and migrations
├── public/               # Static assets
├── scripts/              # Python or Node scripts for data ingestion/scraping
├── .github/workflows/    # CI/CD pipelines
├── .env.example
├── next.config.js
├── package.json
├── README.md
└── tailwind.config.ts
```

## Data Sources

- Municipal websites and open data portals (e.g., Ville de Montréal "Ventes pour taxes impayées", Ville de Québec, other cities)
- Registre foncier du Québec (land registry) for property details
- Quebec government open data (donneesquebec.ca or similar)
- Historical tax sale results for training ML models or analytics

**Note on Scraping**: Always respect robots.txt, implement rate limiting, use official APIs where available, and comply with terms of service and applicable laws (including privacy laws like PIPEDA and Quebec's Act Respecting the Protection of Personal Information in the Private Sector).

## Getting Started (Local Development)

1. Clone the repo
   ```bash
   git clone https://github.com/BoabNick/qc-property-intelligence.git
   cd qc-property-intelligence
   ```

2. Install dependencies
   ```bash
   npm install
   ```

3. Set up environment variables
   ```bash
   cp .env.example .env.local
   # Edit .env.local with your database URL, Grok API key, etc.
   ```

4. Set up database (Prisma)
   ```bash
   npx prisma migrate dev
   npx prisma generate
   ```

5. Run the development server
   ```bash
   npm run dev
   ```

## Deployment

- **Vercel**: Connect the GitHub repo to Vercel for automatic deployments on push to main.
- **Database**: Use Vercel Postgres, Neon, or Supabase.
- **Scheduled Jobs**: Use Vercel Cron Jobs or external service like Trigger.dev or GitHub Actions for periodic scraping.

## Improvements Made Over Basic Guide

- **Performance**: Leveraged Next.js 15 React Server Components and streaming for faster page loads.
- **Type Safety**: Full TypeScript coverage reduces runtime errors.
- **Developer Experience**: Prettier, ESLint, and suggested Husky hooks.
- **AI-First**: Deep integration with Grok for "what does this property mean for an investor?" style insights.
- **Production Ready**: Error boundaries, loading states, accessibility (ARIA), SEO optimizations.
- **Ethical & Legal**: Built-in disclaimers, audit logs for data access, clear attribution to data sources.
- **Extensibility**: Modular scraper design so new municipalities can be added easily.
- **Testing & CI**: Automated checks on every PR to maintain quality.

## Roadmap / Future Improvements

- [ ] Implement actual scraper for major Quebec cities
- [ ] Add user authentication and personalized alerts
- [ ] Property valuation model using historical data + AI
- [ ] Mobile app companion (React Native or PWA)
- [ ] Advanced analytics with charts (Recharts or Tremor)
- [ ] Integration with Registre foncier API if/when available
- [ ] Multi-language support (English/French)

## Contributing

Contributions are welcome! Please open an issue or PR. For major changes, discuss first.

## License

MIT (or choose appropriate)

## Disclaimer

This app is for informational and research purposes only. It does not constitute legal, financial, or investment advice. Tax sales involve significant risks, including redemption rights, title issues, and property condition. Always conduct your own due diligence and consult qualified professionals. Data may be incomplete or inaccurate.

## Acknowledgments

Built with assistance from Grok (xAI) based on the Quebec Tax Sale App Builder Guide.