# APIReference
## Condensed Fusion API reference - 10/12/2025

# Fusion 360 API – Condensed HTML Reference

This repository contains a **condensed, offline reference** of the Autodesk Fusion 360 API help,
decompiled from the official `FusionAPI.chm` file and reorganized for easier use with tools like
Cursor and local documentation search.

> **Note:** This is an unofficial, derived reference for personal / development use.
> All API content is © Autodesk. Do not redistribute without respecting Autodesk’s terms.

---

## What’s in this repo?

### `HTML_Condensed/`

This folder contains the **flattened HTML pages** for the Fusion 360 API:

- Each **main page** (e.g. `AccessibilityAnalyses.htm`, `ExtrudeFeature.htm`) has had its
  associated sub-pages (e.g. `_count.htm`, `_item.htm`, `_objectType.htm`, etc.) merged into it.
- The goal is to have **one HTML file per API object**, containing:
  - Overview / description
  - Methods and properties
  - C++ syntax and examples (Python examples have been intentionally ignored)
  - Return / property value info
  - Parameter tables (where applicable)

This makes each page self-contained and much easier to index or convert.

### `HTML_Condensed/Enumerators/`

This subfolder contains **enumerator / types pages** only:

- Any page whose base filename ends with `Types` (e.g. `FeatureTypes.htm`, `ObjectTypes.htm`)
  is treated as an **enum reference** and moved into this folder.
- These typically list valid enum values used by various Fusion API methods and properties.

---

## How these files were created (pipeline)

1. The original `FusionAPI.chm` (Fusion 360 API offline help) was **decompiled** into HTML.
2. A script scanned the decompiled HTML:
   - **Main pages** = files whose base name does *not* contain `_`
   - **Sub-pages** = files whose base name starts with `MainBase_...`
3. For each main page:
   - The script opened its sub-pages and extracted:
     - Description
     - C++ example code (only from the C++ tab)
     - Return / Property value text
     - Parameter tables
   - This information was appended to the main page as a `Members Detail (C++)` section.
4. Files whose base name ended with `Types` were moved into `HTML_Condensed/Enumerators/`.

The result: a smaller, cleaner set of HTML files better suited for code-assistant tools and
offline reference.

---

## Intended use

This repo is designed to be used as:

- A **personal Fusion 360 API reference**, especially for C++ development.
- A **documentation source for AI/code assistants** (e.g. Cursor), by:
  - Hosting the repo on GitHub (or similar),
  - Pointing the assistant’s “Docs” feature to these HTML files or to converted Markdown.

Typical use cases:

- Looking up exact C++ method signatures, parameters, and return types.
- Browsing enums in `HTML_Condensed/Enumerators/` to find valid values.
- Feeding the condensed docs into an embedding / RAG index for smarter API-aware suggestions.

---

## Using this with Cursor (example)

If you are using Cursor:

1. Host this repo on GitHub (private or public).
2. Either:
   - Add selected HTML files or a generated Markdown bundle as **Docs** in Cursor, or
   - Point Cursor’s Docs feature at the repository URL.
3. Add a project rule such as:

   > “When working with Fusion 360 (`adsk::fusion`, `adsk::core`, `adsk::cam`), always consult the Fusion 360 API docs from this repo and prefer C++ examples.”

This encourages Cursor to pull accurate signatures and enums from the condensed docs instead of guessing.

---

## Notes & Disclaimer

- This project is **not** affiliated with or endorsed by Autodesk.
- All original API documentation content belongs to Autodesk.
- This repository exists solely to make the Fusion 360 API docs more convenient to reference and
  integrate into personal tooling.
- If you plan to share or redistribute this repository, review Autodesk’s license/terms
  for the Fusion 360 API documentation and comply accordingly.
