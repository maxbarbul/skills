---
name: get-web-page
description: Fetches any web page and converts it to Markdown using a CLI that writes content to stdout. Use when a user asks to read, summarize, inspect, or archive a URL as Markdown instead of raw HTML, or mentions url-to-markdown.
---

# Get Web Page

## Quick start

Prerequisite:
- `npm` is installed and available in PATH.

Command:
```bash
npx -y url-to-markdown-cli-tool {URL}
```

Behavior:
- Reads the target URL.
- Outputs Markdown to stdout.

Example:
```bash
npx -y url-to-markdown-cli-tool https://example.com
```

## Workflows

### 1. Fetch page as markdown

- Validate URL is absolute (`http://` or `https://`).
- Run:
	- `npx -y url-to-markdown-cli-tool {URL}`
- Capture stdout as the canonical page content.

### 2. Save markdown to file (optional)

- Redirect stdout when persistence is needed:
	- `npx -y url-to-markdown-cli-tool {URL} > page.md`
- Use the saved file for downstream analysis or summarization.

### 3. Failure handling

- If command is not found or fails, verify `npm`/`npx` is installed.
- If URL fetch fails, retry with a reachable URL and confirm network access.
- If output is empty, rerun once and inspect stderr for transient fetch errors.

## Usage notes

- Prefer Markdown output over HTML for LLM-friendly parsing.
- Treat stdout as source of truth unless file redirection is explicitly requested.
- Do not alter page content beyond the conversion performed by the tool.
