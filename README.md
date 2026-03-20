# ReciTAC-JSON
This repo hosts static data files for GitHub Pages.

GitHub Pages serves the site from `public/`.
Put files under `public/data/`.
Subfolders are preserved.
The deploy workflow publishes that folder and generates `data/index.json` so the page can auto-discover hosted files recursively.
