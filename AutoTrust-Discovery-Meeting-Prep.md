# AutoTrust Discovery Meeting -- POC Scoping

**Date:** March 11, 2026
**Objective:** Get the specifics we need to build a compelling POC that shows AutoTrust what their platform looks like on viax.
**POC Focus:** Dealer onboarding + co-op purchasing, with a preview of marketplace.
**Audience:** Business stakeholders + technical architect

---

## What We Need to Walk Out With

By end of this meeting, we should have clear answers on:

- The dealer data model (who is a "dealer" -- single location? franchise group? both?)
- One real onboarding workflow we can replicate in the POC
- One real purchasing scenario with actual product categories and pricing logic
- Enough supplier context to mock a realistic catalog
- The technical architect's requirements for platform fit (integration patterns, scale, multi-tenancy)
- Agreement on POC scope and timeline to deliver it

---

## Section 1: Dealer Structure and Identity

This is foundational. Every other feature depends on how we model "dealer" in viax.

**What we need to understand:**

- What defines a dealer in the co-op? Is it a single rooftop (location), a dealership group, or both?
- Do multi-location dealers exist? If so, does each location have independent purchasing and reporting, or does the parent group see everything?
- How are dealers tiered today? What determines the tier -- volume, tenure, product mix, geography?
- How many dealers are active today? How many do you expect in 12 months?
- Is there a dealer identifier you use today (a member ID, account number)?

**Why this matters for the POC:**
We need to model the party hierarchy correctly. A flat dealer list vs. a parent-child dealer group with location rollups is a completely different data model. Getting this wrong means the reporting and pricing logic won't ring true.

---

## Section 2: Dealer Onboarding

This is the first thing a dealer touches. It sets the tone for the entire platform experience.

**What we need to understand:**

- Walk us through what happens today when a new dealer joins. Who initiates it? What information do you collect? How long does it take end-to-end?
- What documents are required (W-9, insurance certs, dealer license, agreements)? Are these uploaded somewhere or emailed around?
- Who approves a new dealer? Is it a single approver or does it route through multiple people (compliance, finance, regional manager)?
- What happens after approval -- what does the dealer get access to? Is there a welcome sequence, or do they just get credentials?
- What are the failure modes? Where do dealers get stuck or drop off today?
- Are there different onboarding paths for different dealer types or tiers?

**Why this matters for the POC:**
We want to show a real onboarding flow, not a generic form. If we can replicate their actual steps -- with their actual fields and documents -- the POC feels like *their* platform, not a template.

---

## Section 3: Co-Op Purchasing

This is where the money moves. It needs to feel familiar but dramatically better.

**What we need to understand:**

- What do dealers actually buy through the co-op today? Give us concrete categories (F&I products, parts, accessories, training, services).
- How many suppliers are in the program? Are we talking 5 or 50?
- How does pricing work? Is it volume-based (hit X units, unlock Y price), flat negotiated rates per tier, or a mix?
- Does pricing change per dealer based on their tier, location, or history?
- What does the purchase flow look like today? Phone call? Email? Portal? Spreadsheet order form?
- Once a dealer places an order, what happens? Who fulfills it -- AutoTrust or the supplier directly?
- How does the dealer know the order status? Is there any tracking today?
- Are there minimum order quantities, approval thresholds, or budget caps per dealer?

**Why this matters for the POC:**
We need two or three real product categories with realistic pricing logic to build a catalog that feels authentic. If we show generic "Product A, Product B" it won't land. We also need to know whether orders route to AutoTrust or directly to suppliers -- that changes the order management model.

---

## Section 4: Marketplace Preview

We're not building a full marketplace in the POC, but we want to show the vision. These questions help us mock it credibly.

**What we need to understand:**

- Beyond core co-op purchasing, what additional products or services do you want dealers to discover?
- Is the marketplace concept about giving suppliers a self-service way to list offerings, or is it AutoTrust-curated?
- Would different dealers see different marketplace offerings based on tier, region, or purchase history?
- Is there a revenue model here -- does AutoTrust take a margin on marketplace transactions?
- Are there any suppliers already asking for this kind of channel?

**Why this matters for the POC:**
We'll show a marketplace view in the POC with a handful of curated offerings to demonstrate the "what could be." These answers let us pick products that resonate instead of making them up.

---

## Section 5: Reporting and Visibility

Reporting is often where executive buy-in happens. "I can finally see what's going on."

**What we need to understand:**

- What does AutoTrust leadership want to see that they can't see today? What's the dashboard they wish they had?
- At the dealer level, what do dealers care about -- their spend, their status, their savings vs. street price?
- Is quota attainment tracked today? Where does that data live (spreadsheet, CRM, supplier portal)?
- Do you report to suppliers on dealer performance? If so, what do those reports look like?
- Is there a regional or territory structure we should reflect in the reporting hierarchy?

**Why this matters for the POC:**
We won't build a full reporting suite in the POC, but we can show a few key views that demonstrate the data model supports the visibility they need. Knowing their dream dashboard helps us pick the right metrics to surface.

---

## Section 6: Integration Landscape

This is for the technical architect. We need to understand what exists today so we can show how viax connects.

**What we need to understand:**

- What systems are in play today? Any existing portals, CRMs (Salesforce, HubSpot), ERPs, or custom-built tools?
- How do suppliers interact with AutoTrust today -- APIs, EDI, email, spreadsheets, portals?
- Is there a single source of truth for dealer data, or is it scattered?
- Are there any systems that absolutely must integrate with the new platform from day one?
- What does the IT team look like -- internal developers, outsourced, or is this the first platform investment?

**For the technical architect specifically:**

- viax is headless and API-first. The POC will demonstrate a custom frontend consuming viax APIs. The same APIs that power the POC power production.
- Multi-tenancy is native -- AutoTrust is the tenant, dealers are scoped within it, catalog visibility and pricing are entitlement-driven.
- The data model is extensible. Party, Product, Order, and BusinessInteraction are core entities that map directly to dealer, catalog item, purchase, and application.
- Integration is via REST/GraphQL APIs. Supplier integrations can be event-driven (webhooks, message queues) or batch (file-based, scheduled sync).
- We're not asking them to rip and replace. viax can sit alongside existing systems and become the orchestration layer over time.

---

## Proposed POC Scope

Based on what we know, here's what we'd propose building. We'll refine this based on tomorrow's answers.

**In scope:**

- Dealer onboarding flow (application, document upload, approval, account activation)
- Co-op product catalog with two or three real categories and tier-based pricing
- Purchase flow (browse, cart, checkout, order confirmation)
- Dealer dashboard (my orders, my status, my catalog)
- AutoTrust admin view (dealer pipeline, order activity, catalog management)
- Marketplace teaser (curated add-on products, browse and detail view)

**Out of scope for POC (but demonstrated as viax capability):**

- Live supplier integrations (we'll simulate with mock data)
- Full reporting suite (we'll show a few key views)
- F&I application routing (complex workflow, better as a Phase 2 conversation)
- Targeted offer campaigns (depends on quota data availability)
- Email/notification system (we'll describe the architecture)

---

## Meeting Flow Suggestion

| Time | Topic | Goal |
|------|-------|------|
| 0:00 - 0:05 | Recap and agenda | Align on what we're here to nail down |
| 0:05 - 0:20 | Dealer structure and onboarding | Map the real workflow and data model |
| 0:20 - 0:40 | Co-op purchasing deep dive | Get product categories, pricing logic, order flow |
| 0:40 - 0:50 | Marketplace and reporting vision | Understand the dream state |
| 0:50 - 0:55 | Technical architecture Q&A | Address platform fit for the architect |
| 0:55 - 1:00 | POC scope agreement and next steps | Confirm what we're building and timeline |

---

## Open Items From First Meeting

Things we flagged but didn't resolve:

- **F&I application flow complexity** -- Is AutoTrust a broker (stays in the middle) or an aggregator (connects and steps back)? This determines whether the common application is a form-routing exercise or a full workflow engine. Defer to Phase 2 discussion but worth asking about to size the opportunity.
- **Quota data source** -- Targeted offers depend on knowing which dealers are underperforming. If that data doesn't exist in a clean format today, the campaign feature needs a data-entry or import story first.
- **Supplier self-service** -- Does AutoTrust want suppliers managing their own catalog entries and pricing, or is AutoTrust the gatekeeper? Changes the admin surface significantly.
