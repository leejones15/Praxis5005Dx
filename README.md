# Praxis 5005 Science Diagnostic

A self-service diagnostic tool for pre-service teachers preparing for the Praxis 5005 Elementary Education: Science subtest. Built as a static site for GitHub Pages — no server required.

## What It Does

- Assembles a **35-question diagnostic** from a 140-item bank covering Earth Science, Life Science, and Physical Science
- Provides a **personalized feedback report** with proficiency levels, domain breakdowns, subtopic flags, and study recommendations
- Supports **3–4 retakes** with different questions each time and tracks progress across attempts
- Logs anonymized results to a Google Sheet for instructor analysis

## Setup

### 1. Enable GitHub Pages

1. Go to your repository **Settings → Pages**
2. Under "Source," select **Deploy from a branch**
3. Choose **main** branch, root folder
4. Save — your site will be live at `https://leejones15.github.io/Praxis5005Dx/`

### 2. Set Up Data Logging (Optional)

Follow the instructions in [SETUP.md](SETUP.md) to create a Google Sheet and Apps Script endpoint for collecting results.

Then update the `APPS_SCRIPT_URL` variable in `index.html` with your endpoint URL.

### 3. Link from Canvas

Add an **External URL** module item in Canvas pointing to your GitHub Pages URL.

## Files

| File | Purpose |
|------|---------|
| `index.html` | The complete application (HTML + CSS + JS in one file) |
| `item-bank.json` | 140 diagnostic items with metadata |
| `SETUP.md` | Google Apps Script setup instructions |
| `README.md` | This file |

## How It Works

**For students:** Click the link in Canvas → enter E-Number (optional) → take the 35-question diagnostic → receive a feedback report with strengths, growth areas, and study recommendations.

**For instructors:** Results are logged to a Google Sheet with anonymized student IDs, scores by domain and subtopic, and item-level miss data. This supports individual progress tracking, cohort-level gap analysis, and item analysis for bank improvement.

## Technical Details

- Pure client-side application — no server, no database, no build step
- Form assembly follows a psychometric blueprint ensuring consistent domain/subtopic coverage across retakes
- E-Numbers are SHA-256 hashed client-side before any data is transmitted
- Progress tracking uses browser localStorage
- Data logging uses a Google Apps Script web app endpoint
- Charts rendered with native HTML Canvas (no external libraries)

## Item Bank Structure

The 140 items are distributed across three domains:

- **Earth Science**: 56 items (5 subtopics)
- **Life Science**: 44 items (6 subtopics)
- **Physical Science**: 40 items (4 subtopics)

Each item is tagged with difficulty level (Foundational / Intermediate / Applied) and an optional inquiry skill tag (Experimental Design, Data Interpretation, Science-Technology-Society, or Unifying Processes).
