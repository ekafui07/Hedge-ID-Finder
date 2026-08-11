# Hedge ID Finder

**Hedge Pensions Smart Matcher + Schedule Generator**

A browser-based Excel matching tool for pension workflows. It compares a **Name List** (records missing IDs) against a **Master List** (records with IDs), then generates a match audit file and a submission-ready schedule — all client-side, with no backend and no file uploads.

🔗 **Live app:** https://ekafui07.github.io/Hedge-ID-Finder/

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [File Requirements](#file-requirements)
- [Getting Started](#getting-started)
- [Usage Guide](#usage-guide)
- [Output Files](#output-files)
- [Matching Behavior](#matching-behavior)
- [Troubleshooting](#troubleshooting)
- [Privacy](#privacy)
- [Templates](#templates)

---

## Overview

A landing page (`index.html`) guides users and links to the full matcher app (`app.html`). The app:

1. Loads two Excel files (`.xlsx` / `.xls`)
2. Lets you map the correct columns for each file
3. Uses fuzzy matching (Fuse.js) to find IDs for name records
4. Auto-accepts high-confidence matches using a configurable threshold
5. Prompts manual review for lower-confidence candidates
6. Shows a full results table with status and confidence
7. Exports two downloadable output files

## Features

| Feature | Description |
|---|---|
| Two-file matching | Name List vs. Master List |
| Flexible column mapping | Choose which columns represent first/other/last names and ID |
| Fuzzy name matching | Handles misspellings, name order differences, and partial variations |
| Confidence threshold slider | Controls when a match is auto-accepted |
| Manual review modal | Resolve uncertain matches interactively |
| "Not Found" review | Re-check unresolved rows after the first pass |
| Dual export | Match audit file + branch/date-formatted submission file |
| Privacy-first | All processing happens in-browser |

## File Requirements

### Name List (missing IDs)
- **Required:** First Name, Last Name, Basic Salary, 2nd Tier
- **Optional:** Other Name

### Master List (contains IDs)
- **Required:** ID Column, First Name, Last Name
- **Optional:** Other Name

> **Note:** The same name appearing twice with two different pension IDs in the Master List is normal and expected — not a data error.

## Getting Started

### Option A — Use the hosted app
Open: https://ekafui07.github.io/Hedge-ID-Finder/

### Option B — Run locally
1. Clone or download this repository
2. Open `index.html` in a modern browser and click **"Open Matcher"** to launch the app (`app.html`)

No install, no build step, no server process required.

## Usage Guide

1. **Upload files** — Name List and Master List
2. **Map columns** — select the right fields for names and IDs (the run button enables once all required fields are mapped)
3. **Set output metadata** — Branch / Management Unit, Region, Cycle Date, Investment Date
4. **Set confidence threshold** — default 80%; higher = stricter auto-matching, lower = more auto-matches but potentially less accurate
5. **Run comparison** — progress bar updates as rows are processed
6. **Resolve uncertain matches** — for rows below threshold, choose the correct candidate or skip as `NOT FOUND`
7. **Review results** — check summary stats (auto matched / manually matched / not found), filter/search the table, optionally re-run **Review Not Found**
8. **Download outputs** — Match Results and Submission File

## Output Files

### Match Results
- Name List Name
- Found ID
- Master List Name
- Confidence
- Status (`Auto`, `Manual`, `Not Found`)

### Submission File
- Branch
- Membership ID
- First Name / Other Names / Surname
- Cycle Date / Investment Date
- Basic Salary / 2nd Tier / 3rd Tier fields
- Management Unit / Region

Rows marked `NOT FOUND` are included so they can be corrected later.

## Matching Behavior

- Name text is normalized before matching (case/punctuation cleanup)
- Multiple name permutations are tested (e.g., first-last vs. last-first)
- The best score from full-name and weighted first/last-name search is used
- Confidence is shown as a percentage in results

## Troubleshooting

| Issue | Fix |
|---|---|
| "Run Comparison" stays disabled | Confirm both files are uploaded and all required column mappings are selected |
| Too many wrong auto matches | Increase the confidence threshold |
| Too many manual prompts | Lower the threshold slightly |
| Unexpected empty values in output | Re-check salary/tier mappings and input data quality |

## Privacy

All processing happens in the browser. Your spreadsheets never leave your machine.

## Templates

Available in the repository root:
- `ID_Template.xlsx` — example ID/metadata template
- `LIST_TEMPLATE.xlsx` — example Name List template

Open the landing page (`index.html`) and use the **"Download ID Template"** / **"Download List Template"** buttons to save the sample files.

If published via GitHub Pages, `index.html` is the landing page users see first; `app.html` contains the full matcher app.
