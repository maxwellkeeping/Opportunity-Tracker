# Opportunity Tracker

## Project Overview

A single-page web application called the **Opportunity Portfolio Tracker** for Ontario government portfolio managers. It acts as a **linking and reference layer** that associates annual planning Opportunities to infrastructure deployment requests (managed in a custom Ontario intake tool) and projects (managed in Planview). Neither external system has a direct API at this time — this tool stores references and links, not replicated data.

The only simulated live integration is the CMDB (Solutions/CIs), which has an available API.

## Tech Stack

- **HTML, CSS, vanilla JavaScript only** — no frameworks, no build tools, no dependencies
- Everything in a single `index.html` file — must open directly in a browser without any setup

## Development Setup

Open `index.html` directly in a browser. No server required.

## Key Features

Five views navigable via a top nav bar:
1. **Opportunity Registry** — table of all Opportunities with filtering, inline status editing, and row detail modal
2. **Infrastructure Requests** — references to intake tool records, linked to Opportunities, amber highlight for unlinked
3. **Projects** — references to Planview records, linked to Opportunities, amber highlight for unlinked
4. **Solutions (CMDB)** — CI records simulating CMDB API data, many-to-many relationship with Opportunities
5. **Leadership Dashboard** — summary cards, charts (pure CSS/SVG), Overdue to Start + Missing Start Date lists

## Project Structure

Single file: `index.html`

Mock data defined as JavaScript objects at the top:
- `clusters` — 8 Ontario I&IT clusters
- `opportunities` — 10–15 opportunities across clusters
- `infrastructureRequests` — references to external intake tool records
- `projects` — references to Planview records
- `configurationItems` — simulated CMDB CI data
- `opportunityCIs` — many-to-many join table

## Notes

- Light theme, muted blue/grey palette, professional Ontario government internal tool aesthetic
- Build in phases (see brief): skeleton → View 1 → Views 2&3 → View 4 → View 5 → cross-view nav
- Pause and confirm after each phase before proceeding
- Cross-view navigation: clicking linked item counts navigates to the relevant view filtered to that record
- `plannedStartDate` may be null on Opportunities (triggers Missing Start Date list on dashboard)
- Opportunities with past `plannedStartDate` and status "Identified" or "In Planning" trigger Overdue to Start list
- `opportunityId: null` on requests/projects means unlinked → amber highlight
- Cluster names are from public info — may need correction before stakeholder demo
- This is a prototype for stakeholder demo only; all data is fictional
