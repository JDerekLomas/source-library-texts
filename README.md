# Source Library Texts

Machine-readable OCR transcriptions and English translations of historical texts from the Western esoteric tradition.

**Website:** [sourcelibrary.org](https://sourcelibrary.org)

## What is this?

This repository contains the full text of every book processed by [Source Library](https://sourcelibrary.org) — a digital library of alchemical, Hermetic, Kabbalistic, Rosicrucian, and early scientific manuscripts. Each book has:

- **OCR text** — AI-transcribed text from the original page images (Latin, German, Greek, Hebrew, Arabic, etc.)
- **English translation** — AI-generated scholarly translation (or modernization for Early Modern English texts)
- **Metadata** — author, year, language, processing model, and provenance

## Why git?

Every time a book is re-processed with improved AI models or prompts, the text files are updated and a new commit is created. Git provides:

- **Full version history** — see exactly how OCR and translations have improved over time
- **Diffs** — compare any two versions of a text
- **Collaboration** — submit corrections via pull requests
- **Citation stability** — tag specific versions for scholarly reference
- **Machine access** — clone the entire corpus for computational analysis

## Repository structure

```
books/
  {book-id}/
    metadata.json       # Book metadata and processing info
    ocr.txt             # Original-language OCR text (all pages)
    translation.txt     # English translation (all pages)
```

Each text file uses page markers (`--- Page N ---`) to separate content by physical page.

## Using this data

### Clone the full corpus
```bash
git clone https://github.com/JDerekLomas/source-library-texts.git
```

### Read a specific book
```bash
cat books/{book-id}/translation.txt
```

### See how a text changed between OCR versions
```bash
git log --oneline books/{book-id}/ocr.txt
git diff HEAD~1 books/{book-id}/ocr.txt
```

### Search across all translations
```bash
grep -r "philosopher's stone" books/*/translation.txt
```

## Processing models

Texts are processed using Google's Gemini AI models:
- **OCR:** `gemini-3-flash-preview` with language-specific prompts (Latin, German Fraktur, etc.)
- **Translation:** `gemini-3-flash-preview` with scholarly translation prompts
- **Prompt version:** tracked in each book's `metadata.json`

## License

Individual books carry their own licenses (typically CC0 or CC-BY from their source institutions). See each book's `metadata.json` for specific license information.

The repository structure and tooling are MIT licensed.

## Related

- [Source Library](https://sourcelibrary.org) — the web application
- [MCP Server](https://www.npmjs.com/package/@source-library/mcp-server) — programmatic access via Claude, Cursor, etc.
- [API](https://sourcelibrary.org/developers) — REST API documentation
