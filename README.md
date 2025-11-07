#Hedge Pensions Trust Name & ID Matcher

This is a simple, no-backend, browser-based web tool to compare two Excel sheets. It's designed to find IDs from a "master" list for a "name" list, even when names are slightly misspelled.

The tool is built as a single index.html file and runs entirely in your browser. No data ever leaves your computer.

#Core Features

Compares Two Lists: Takes a "Name List" (with names) and a "Master List" (with names and IDs).

Fuzzy Matching: Uses Fuse.js to find matches even with misspellings or typos.

Adjustable Sensitivity: A slider lets you control how "fuzzy" (lenient) or "exact" the match should be.

Results Table: Displays a clear table of the original names, the found ID, the name it matched against, and a match score.

Export to Excel: Download the final matched results as a new Excel (.xlsx) file.

Client-Side Only: All processing is done in your browser. Files are never uploaded to a server, ensuring 100% privacy.

#How to Use

Open the Tool: https://ekafui07.github.io/Hedge-ID-Finder/ file in any modern web browser (like Chrome, Firefox, or Edge).

Upload Files:

List 1: Upload your "Name List" (the one you want to find IDs for).

List 2: Upload your "Master List" (the one that contains the names and IDs).

Adjust Sensitivity: Use the slider to set the match tolerance.

0.00 is an exact match (no misspellings allowed).

0.50 is very loose.

A good starting point is 0.20 - 0.30.

Compare: Click the "Compare Files" button.

Review & Download: The results will appear in the table. Click the "Download Results" button to save them as an Excel file.

