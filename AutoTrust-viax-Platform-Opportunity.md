# AutoTrust -- viax Platform Opportunity Outline

**Prospect:** AutoTrust
**Model:** Dealer co-op, automotive vertical
**Current offering:** F&I package deals to member dealers
**Expansion goal:** Unified platform for dealer lifecycle -- onboarding, purchasing, services, marketplace, reporting
**Date:** March 10, 2026

---

## The Problem viax Solves Here

AutoTrust today is running a co-op on manual processes and disconnected systems. As they expand beyond F&I into broader dealer services, they need a platform that:

- Onboards new dealers without friction
- Consolidates purchasing across all supplier programs into one view
- Presents a single application surface for multiple services (F&I, parts, warranty, etc.)
- Gives dealers and AutoTrust leadership visibility into performance by location, tier, and program
- Enables AutoTrust to push targeted offers to dealers based on quota attainment and supplier goals

viax's headless commerce and product catalog architecture is a direct fit: AutoTrust is the "enterprise" managing a network of "distributors" (dealers), which is exactly the viax B2B model.

---

## Proposed Platform Capabilities

### 1. Dealer Onboarding

- Guided enrollment workflow: dealer submits business info, license, location, tier selection
- Approval queue for AutoTrust administrators
- Automated provisioning: dealer account created, catalog access granted, reporting initialized
- Document collection built in (W-9, dealer agreements, insurance certs)
- Status tracking: dealer sees where they are in the process

**viax fit:** Party management + entitlement model handles dealer account creation and catalog scoping natively.

---

### 2. Global Purchasing (Co-Op Buying)

- Unified product catalog: all supplier programs, parts, accessories, and services in one place
- Co-op negotiated pricing applied automatically based on dealer membership tier
- Purchase flow: dealer selects program → cart → checkout → order dispatched to supplier
- Purchase history and spend tracking per dealer
- Order status updates from suppliers back to dealer portal

**viax fit:** Core headless commerce -- product catalog, pricing, cart, order management. Multi-supplier catalog is a standard viax pattern.

---

### 3. Common Application for F&I and Services

- Single intake form that feeds multiple service applications (finance, insurance, warranty, etc.)
- Dealer fills out once; data routes to the correct providers automatically
- Application status tracking across all providers in one place
- Reduces re-entry: dealer data stored and pre-populated for future applications
- Integration hooks to carrier/lender APIs for status callbacks

**viax fit:** Business Interaction model maps to application workflow. Party data model stores dealer profile reusably across all applications.

---

### 4. Dealer Marketplace

- Curated catalog of add-on products and services beyond core F&I
- Suppliers can list offerings; AutoTrust controls what appears per tier
- Dealers browse, compare, and purchase directly
- Featured placements based on supplier co-op agreements and quota incentives
- Upsell/cross-sell logic: dealers like you also added...

**viax fit:** Product catalog with entitlement-scoped visibility, relationship-based upsell, supplier-configured pricing.

---

### 5. Reporting and Analytics

**Dealer-level:**
- Spend by category (F&I, parts, services)
- Program participation vs. available programs (gap analysis)
- Application status dashboard
- Purchase history and order tracking

**Co-op-level (AutoTrust admin):**
- Aggregate spend and volume by dealer, region, and tier
- Supplier quota attainment: which dealers are on track vs. at risk
- New dealer pipeline: onboarding funnel, time-to-active
- Top performing locations vs. laggards
- Supplier program adoption rates

**viax fit:** Order data model feeds reporting natively. Dealer/location hierarchy maps to party relationships.

---

### 6. Targeted Offer Pushing (Quota-Driven Campaigns)

- AutoTrust or suppliers configure rules: push this offer to dealers below 60% quota attainment
- Dealers receive targeted notifications in the portal and via email
- Offer acceptance tracked back to supplier program
- Supports AutoTrust's supplier relationships: hit volume commitments by activating the right dealers at the right time

**viax fit:** Promotional and pricing layer on top of catalog + party segmentation.

---

## Platform Architecture Summary

```
AutoTrust Admin Portal         Dealer Portal
  - Manage dealers               - Onboarding workflow
  - Approve onboarding           - Browse & purchase catalog
  - Configure catalog/offers     - F&I application hub
  - View aggregate reporting     - My orders & status
  - Push targeted offers         - My reporting

              viax Platform (headless)
  Party Mgmt | Product Catalog | Orders | Pricing | Entitlements

              Supplier/Provider Integrations
  F&I Carriers | Finance Cos | Parts Vendors | Warranty Providers
```

---

## Key Discovery Questions (Meeting Prep)

1. How many dealers are in the co-op today, and what is the growth target?
2. Who are the primary suppliers -- F&I carriers, parts vendors, or both?
3. Is this dealer-facing, AutoTrust admin-facing, or both with separate views?
4. What is the current tech stack? Any existing portals, ERPs, or CRMs in play?
5. Is the co-op buying model volume-based (hit X, get Y price) or flat negotiated rates?
6. What is the #1 pain point today -- onboarding speed, data re-entry, lack of reporting visibility?
7. Timeline and budget posture -- are they looking to pilot one use case or go full platform?
