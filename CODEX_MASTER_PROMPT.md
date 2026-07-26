# Codex Master Project Prompt

## Build and Automate a Zero-Upfront-Cost Technology Commerce Business

You are my senior software engineer, e-commerce automation architect, product researcher, SEO specialist, content creator, and business operations assistant.

Your mission is to create a complete automated technology-product commerce system that minimizes upfront costs and does not require me to purchase inventory before receiving customer money.

Do not merely provide instructions. Build the working project files, scripts, database, dashboards, scheduled workflows, documentation, tests, and configuration templates.

## 1. Primary Business Objective

Build a technology-product business targeting customers in the United States.

Prioritize business models in this order:

1. Affiliate marketing
2. Digital technology products
3. Print-on-demand products
4. Marketplace or supplier arrangements that charge only after customer payment is available
5. Traditional dropshipping only when sufficient cleared funds are available

The system must never automatically place a supplier order using money that is not available. Do not create debt, use credit, overdraft an account, or commit me to paid services.

## 2. Financial Safety Engine

Use this rule:

```text
AVAILABLE_FULFILLMENT_BALANCE =
cleared customer payouts
- refunds reserve
- taxes reserve
- transaction fees
- outstanding supplier obligations
```

A dropshipping order may be submitted only when:

```text
AVAILABLE_FULFILLMENT_BALANCE >= supplier product cost + shipping cost + safety buffer
```

If funds are insufficient:

- Do not place the order.
- Mark it as `Waiting for cleared funds`.
- Notify the administrator.
- Explain the amount required.
- Never use a personal credit card automatically.
- Never borrow money or create an overdraft.
- Never hide fulfillment delays.

Defaults:

- Safety buffer: $10 per order or 10% of supplier cost, whichever is greater
- Refund reserve: 15% of cleared revenue

Make these values configurable.

## 3. Affiliate-First Launch

Because there is no money available to advance supplier payments, begin with an affiliate product-discovery website.

The initial system must:

- Display useful technology products.
- Link customers to legitimate merchants or affiliate partners.
- Clearly disclose affiliate relationships.
- Never collect payment for affiliate products.
- Never claim ownership, manufacturing, or shipping of affiliate products.
- Track outbound product clicks.
- Track conversions when legally and technically available.
- Generate comparison pages, buying guides, product guides, SEO pages, and social content.
- Maintain an affiliate-link database.
- Detect and remove broken or expired links.

Do not violate merchant terms, scrape prohibited content, copy protected descriptions, steal images, or reuse reviews without authorization.

## 4. Shopify Integration Layer

Build the system so Shopify can be connected later using:

- Shopify Admin API
- Shopify Storefront API
- Product creation
- Collections
- Inventory synchronization
- Price synchronization
- Orders
- Fulfillment status
- Tracking updates
- Product archiving
- Tags
- SEO metadata
- Metafields
- Webhooks

Use environment variables:

```text
SHOPIFY_STORE_DOMAIN
SHOPIFY_ADMIN_ACCESS_TOKEN
SHOPIFY_STOREFRONT_TOKEN
SHOPIFY_API_VERSION
SHOPIFY_WEBHOOK_SECRET
```

Default to:

```text
SHOPIFY_MODE=mock
ALLOW_SHOPIFY_WRITES=false
```

Live writes require both:

```text
SHOPIFY_MODE=live
ALLOW_SHOPIFY_WRITES=true
```

## 5. Supplier Architecture

Create modular adapters for possible future integrations such as Zendrop, Spocket, Syncee, CJdropshipping, AutoDS, and other approved U.S.-warehouse suppliers.

Each adapter should support:

- Authentication
- Product search
- U.S. warehouse filtering
- Shipping cost and delivery estimates
- Inventory and supplier cost
- Order submission
- Tracking retrieval
- Cancellation requests
- Rate-limit handling
- Error handling
- Audit logs

Never pretend an integration exists when no official API or authorized access is available. When an API is unavailable, create a manual CSV import and approval workflow instead.

## 6. Product Acceptance Rules

Only approve physical products that:

- Ship from a U.S. warehouse
- Normally arrive within seven business days
- Come from a verifiable supplier
- Have stable inventory
- Are not counterfeit
- Use authorized images and product data
- Have known product and shipping costs
- Have a reasonable return policy
- Produce a positive expected margin
- Are safe and appropriate for U.S. customers
- Do not make unsupported medical, safety, or performance claims
- Are not subject to an active recall

Reject counterfeit electronics, fake branded accessories, dangerous batteries, deceptive products, stolen images, unstable inventory, unknown shipping costs, and products requiring advance purchase when funds are unavailable.

## 7. Product Categories

Start with practical technology accessories:

- Mobile technology
- Home office
- Smart home
- Travel technology
- Car technology
- Creator technology

Examples include charging stands, cables, USB-C hubs, laptop stands, webcams, microphones, desk lighting, smart plugs, sensors, travel adapters, phone mounts, dash cameras, tripods, lighting accessories, and streaming accessories.

## 8. Product Scoring Engine

Score each product from 0 to 100:

- U.S. shipping speed: 15
- Supplier reliability: 15
- Product quality indicators: 15
- Estimated margin: 15
- Search demand: 10
- Social-content potential: 10
- Competition level: 5
- Return-risk score: 5
- Legal and branding safety: 5
- Inventory stability: 5

Rules:

- Below 60: reject
- 60-74: manual review
- 75-84: approved candidate
- 85-100: priority candidate

Never invent sales numbers, ratings, review counts, demand data, or shipping times. Mark missing information as unknown and reduce confidence.

## 9. Profit Calculator

For every product calculate:

- Retail price
- Supplier cost
- Supplier shipping
- Payment-processing estimate
- Platform-fee estimate
- Refund reserve
- Return-risk allowance
- Expected gross profit
- Expected gross margin
- Break-even price
- Recommended selling price
- Maximum discount
- Fulfillment cash required

Use:

```text
Expected gross profit =
retail price
- supplier cost
- shipping
- processing fees
- platform fees
- refund allowance
- return-risk allowance
```

Reject negative-profit products, unknown-cost products, unrealistic pricing, or margins below the configurable minimum. Default target gross margin: 30%.

## 10. Application Architecture

Preferred free/open-source stack:

- Next.js
- TypeScript
- React
- Tailwind CSS
- SQLite locally
- PostgreSQL-compatible schema
- Prisma ORM
- Node.js
- Zod
- Vitest or Jest
- Playwright
- GitHub Actions where useful

Build:

- Responsive public affiliate storefront
- Admin dashboard
- Product research dashboard
- Affiliate-link manager
- Supplier manager
- Content calendar
- SEO dashboard
- Financial safety dashboard
- Order-readiness dashboard
- Automation history
- Error and audit logs
- Settings
- Manual approval queue

The project must run locally without paid services.

## 11. Public Website

Create pages for Home, Best Technology Finds, Categories, Product Comparisons, Buying Guides, Deals, Smart Home, Mobile Technology, Home Office, Travel Technology, Car Technology, Creator Technology, Blog, About, Contact, Affiliate Disclosure, Privacy Policy, Terms, and Cookie Information.

Ensure mobile responsiveness, accessibility, honest disclosures, and no fake reviews, fake scarcity, fake discounts, or fabricated popularity claims.

## 12. Admin Dashboard

Include:

- Overview
- Product research
- Product approval
- Financial safety
- Content management
- Integrations
- Automation logs

Show integrations as Connected, Not connected, Configuration required, Error, Read-only, or Mock mode.

## 13. Product Content Generation

Generate original content based only on verified facts:

- Product title
- Summary
- Benefits
- Use cases
- Specifications
- Compatibility
- Limitations
- Included items
- Shipping estimate
- Return-policy summary
- Disclosure
- FAQ
- SEO title
- Meta description
- URL slug
- Image alt text
- Internal links
- Social hooks
- Video script
- Email subject ideas

Do not copy merchant text or make unsupported claims.

## 14. SEO Automation

Create systems for:

- Keyword clusters
- Keyword-to-page mapping
- Duplicate-content detection
- Internal links
- Missing metadata
- Broken links
- Duplicate titles
- Thin-page detection
- Structured data
- XML sitemap
- robots.txt
- Canonical URLs
- Content update dates
- Weekly SEO reports

## 15. Content Automation

Generate:

- Buying guides
- Product comparisons
- Technology tips
- Setup tutorials
- Gift guides
- Product-use ideas
- Troubleshooting articles
- Weekly roundups

For each approved product create three TikTok/Reels concepts, three YouTube Shorts concepts, three Pinterest concepts, one Facebook post, one Instagram caption, one email idea, and one blog idea.

Do not auto-publish initially. Put content in a review queue.

## 16. Email System

Build draft templates for welcome emails, weekly finds, comparisons, price alerts, back-in-stock alerts, educational tips, and disclosure reminders.

Default:

```text
EMAIL_SEND_MODE=draft
ALLOW_AUTOMATIC_EMAIL=false
```

Live sending requires explicit configuration, consent tracking, and unsubscribe support.

## 17. Automation Schedule

Create scripts and scheduler definitions for:

### Daily Product Research
- Review approved sources
- Find candidate products
- Validate merchant and supplier information
- Score products
- Reject incomplete or unsafe products
- Add qualified products to review

### Daily Link Check
- Check affiliate links
- Detect redirects, unavailable products, price changes, and stock changes

### Daily Inventory Check
- Check inventory, cost, shipping, and delivery estimates when supplier APIs are connected

### Daily Financial Safety Check
- Recalculate cleared funds, reserves, obligations, and fulfillment eligibility

### Weekly SEO Audit
- Find broken links, missing metadata, duplicate content, and weak internal linking

### Weekly Content Batch
- Build a seven-day content calendar from approved products

### Monthly Business Review
- Summarize traffic, clicks, conversions, revenue, costs, profit, weak products, strong categories, and next actions

## 18. Automation Levels

Create three levels:

1. Research Only
2. Approval Required
3. Approved Automation

Default to Level 1. Never silently enable Level 3.

## 19. Human Approval Requirements

Require approval before:

- Publishing products
- Changing retail prices
- Submitting supplier orders
- Issuing refunds
- Sending marketing email
- Publishing social content
- Connecting payments
- Starting paid plans or trials
- Deleting products or customer data
- Creating large discounts
- Switching from mock mode to live mode

Create a detailed approval log.

## 20. Free-Tool Requirement

Use free and open-source tools wherever possible.

Do not activate paid plans automatically. When a feature requires payment:

- Mark it optional
- Provide a free alternative
- Disable it by default
- Explain the limitation
- Never enter billing information
- Never begin a paid-converting trial without explicit approval

## 21. Environment Variables

Create `.env.example` with placeholders only:

```text
NODE_ENV
DATABASE_URL
APP_URL
ADMIN_EMAIL
ADMIN_PASSWORD_HASH
AUTOMATION_LEVEL
AFFILIATE_MODE
SHOPIFY_MODE
SHOPIFY_STORE_DOMAIN
SHOPIFY_ADMIN_ACCESS_TOKEN
SHOPIFY_STOREFRONT_TOKEN
SHOPIFY_API_VERSION
SHOPIFY_WEBHOOK_SECRET
ALLOW_SHOPIFY_WRITES
ALLOW_AUTOMATIC_EMAIL
EMAIL_SEND_MODE
EMAIL_PROVIDER_API_KEY
SUPPLIER_API_KEY
SUPPLIER_API_SECRET
REFUND_RESERVE_PERCENT
TAX_RESERVE_PERCENT
MINIMUM_MARGIN_PERCENT
FULFILLMENT_SAFETY_BUFFER
AVAILABLE_CLEARED_FUNDS
LOG_LEVEL
```

Never commit real secrets. Add `.env` to `.gitignore`.

## 22. Database Models

Create models for users, products, candidates, sources, merchants, affiliate programs, affiliate links, suppliers, supplier products, inventory, pricing, shipping, scoring, approvals, content, schedules, automation runs, errors, Shopify sync, customer orders, supplier orders, payouts, cleared funds, reserves, fulfillment decisions, audit logs, integrations, and settings.

Preserve financial history instead of overwriting critical values.

## 23. Testing

Create tests for:

- Profit calculations
- Reserve calculations
- Fulfillment balance
- Product scoring
- Rejection rules
- Shopify mock integration
- Supplier mock integration
- Affiliate-link validation
- Approval requirements
- Environment validation
- Duplicate detection
- Unsafe automatic-order prevention
- Insufficient-funds blocking
- Content validation
- API error handling

Include tests proving:

1. An order cannot be submitted when cleared funds are insufficient.
2. Pending customer payments are not treated as cleared funds.

## 24. Documentation

Create:

- README.md
- SETUP.md
- FREE_TOOLS.md
- SHOPIFY_CONNECTION.md
- SUPPLIER_CONNECTION.md
- AFFILIATE_SETUP.md
- AUTOMATION.md
- FINANCIAL_SAFETY.md
- SECURITY.md
- PRIVACY.md
- DEPLOYMENT.md
- TROUBLESHOOTING.md

Write setup instructions for a beginner with exact commands and honest notes about what requires accounts, API keys, approval, or payment.

## 25. Delivery Phases

### Phase 1
- Inspect repository
- Create architecture and database
- Build public affiliate site and admin dashboard
- Add mock products and tests
- Run locally

### Phase 2
- Build product research, scoring, affiliate links, content pipeline, scheduling, and reports

### Phase 3
- Add Shopify mock integration, supplier interfaces, financial safety engine, fulfillment decision engine, and approval workflow

### Phase 4
- Add optional real integrations only where official access is available
- Keep external writes disabled by default

### Phase 5
- Run tests, lint, type checking, and production build
- Fix errors
- Produce completion report

## 26. Completion Report

At the end provide:

- What was built
- What was tested
- Test results
- Files created
- Commands to start
- Features working in mock mode
- Features requiring credentials
- Features requiring manual approval
- Features that could not be automated
- Security risks
- Financial risks
- Recommended first actions
- Exact next step for the owner

Do not claim the system is fully automatic unless all integrations are connected and tested.

## 27. First Action

Begin immediately by inspecting the current repository.

If it is empty:

1. Initialize the project.
2. Create the folder structure.
3. Install only necessary free dependencies.
4. Create the database schema.
5. Build the minimum working affiliate storefront.
6. Build the administration dashboard.
7. Add mock data.
8. Add the financial safety engine.
9. Add tests.
10. Run the application.
11. Fix all errors.
12. Show the completed results.

Do not stop after producing a plan. Implement the project.

When external credentials are missing, create safe mock adapters and continue.

## Codex Start Instruction

Start with Automation Level 1. Build and test the complete local affiliate-first version. Do not activate paid services, Shopify writes, supplier ordering, email sending, or automatic publishing. Continue using mock integrations whenever credentials are unavailable.
