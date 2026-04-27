# Hedge Pensions Smart Matcher + Schedule Generator

Hedge ID Finder is a browser-based Excel matching tool for pension workflows.
It compares a **Name List** (records missing IDs) against a **Master List** (records with IDs), then helps you generate:

1. A match audit file (who matched, confidence, and status)
2. A submission-ready schedule file in the required column layout

The app is a single `index.html` file and runs fully client-side in your browser. No backend is required and files are not uploaded to a server.

## What the App Does

1. Loads two Excel files (`.xlsx` / `.xls`)
2. Lets you map the correct columns for each file
3. Uses fuzzy matching (Fuse.js) to find IDs for name records
4. Auto-accepts high-confidence matches using a configurable threshold
5. Prompts manual review for lower-confidence candidates
6. Shows a full results table with status and confidence
7. Exports two downloadable outputs

## Core Features

- **Two-file matching:** Name List vs Master List
- **Flexible column mapping:** You choose which columns represent first/other/last names and ID
- **Fuzzy name matching:** Handles misspellings, name order differences, and partial variations
- **Confidence threshold slider:** Controls when a match is auto-accepted
- **Manual review modal:** Resolve uncertain matches interactively
- **Not Found review:** Re-check unresolved rows after the first pass
- **Dual export:**
  - `Match_Results.xlsx` (audit/matching output)
  - Branch/date-formatted submission file (ready for upload/use)
- **Privacy-first:** Processing happens in-browser

## File Requirements

### 1) Name List (missing IDs)
Required mapped columns:
- First Name
- Last Name
- Basic Salary
- 2nd Tier

Optional mapped column:
- Other Name

### 2) Master List (contains IDs)
Required mapped columns:
- ID Column
- First Name
- Last Name

Optional mapped column:
- Other Name

## How to Run

### Option A: Use the hosted app
Open:
https://ekafui07.github.io/Hedge-ID-Finder/

### Option B: Run locally
1. Clone or download this repository
2. Open `index.html` directly in a modern browser (Chrome, Edge, Firefox)

No install, no build step, and no server process is required.

## How to Use (Step-by-Step)

1. **Upload files**
	- Upload Name List
	- Upload Master List

2. **Map columns**
	- Select the right fields for names and IDs
	- Ensure all required fields are selected (button will enable when valid)

3. **Set output metadata**
	- Branch / Management Unit
	- Region
	- Cycle Date
	- Investment Date

4. **Set confidence threshold**
	- Use the slider (default: 80%)
	- Higher value = stricter auto-match
	- Lower value = more auto-matches, but potentially less accurate

5. **Run comparison**
	- Click **Run Comparison**
	- Progress bar updates while rows are processed

6. **Resolve uncertain matches (if prompted)**
	- For rows below threshold, choose the correct candidate or skip as `NOT FOUND`

7. **Review results**
	- Check summary stats: Auto matched, Manually matched, Not found
	- Filter/search table by name, ID, or status
	- Optionally run **Review Not Found** to try unresolved rows again

8. **Download output files**
	- **Match Results**: Matching audit output
	- **Download Submission File**: Schedule-formatted file for downstream submission

## Output Files

### A) Match Results file
Contains:
- Name List Name
- Found ID
- Master List Name
- Confidence
- Status (`Auto`, `Manual`, `Not Found`)

### B) Submission file
Contains schedule columns such as:
- Branch
- Membership ID
- First Name / Other Names / Surname
- Cycle Date / Investment Date
- Basic Salary / 2nd Tier / 3rd Tier fields
- Management Unit / Region

Rows with `NOT FOUND` are included so they can be corrected later.

## Matching Behavior Notes

- Name text is normalized before matching (case/punctuation cleanup)
- Multiple name permutations are tested (e.g., first-last vs last-first)
- The best score from full-name and weighted first/last-name search is used
- Confidence is shown as a percentage in results

## Troubleshooting

- **"Run Comparison" stays disabled**
  - Confirm both files are uploaded
  - Confirm all required column mappings are selected

- **Too many wrong auto matches**
  - Increase threshold (stricter)

- **Too many manual prompts**
  - Lower threshold slightly

- **Unexpected empty values in output**
  - Re-check salary/tier mappings and input data quality

## Privacy

All processing is done in the browser. Your spreadsheets remain on your machine.

