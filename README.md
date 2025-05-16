# Website Scraper

[![smithery badge](https://smithery.ai/badge/@tolik-unicornrider/mcp_scraper)](https://smithery.ai/server/@tolik-unicornrider/mcp_scraper)

A command-line tool and MCP server for scraping websites and converting HTML to Markdown.

## Features

- Extracts meaningful content from web pages using Mozilla's [Readability](https://github.com/mozilla/readability) library (the same engine used in Firefox's Reader View)
- Converts clean HTML to high-quality Markdown with TurndownService
- Securely handles HTML by removing potentially harmful script tags
- Works as both a command-line tool and an MCP server
- Supports direct conversion of local HTML files to Markdown

## Installation

### Installing via Smithery

To install Website Scraper for Claude Desktop automatically via [Smithery](https://smithery.ai/server/@tolik-unicornrider/mcp_scraper):

```bash
npx -y @smithery/cli install @tolik-unicornrider/mcp_scraper --client claude
```

### Manual Installation
```bash
# Install dependencies
npm install

# Build the project
npm run build

# Optionally, install globally
npm install -g .
```

## Usage

### CLI Mode

```bash
# Print output to console
scrape https://example.com

# Save output to a file
scrape https://example.com output.md

# Convert a local HTML file to Markdown
scrape --html-file input.html

# Convert a local HTML file and save output to a file
scrape --html-file input.html output.md

# Show help
scrape --help

# Or run via npm script
npm run start:cli -- https://example.com
```

### MCP Server Mode

This tool can be used as a Model Context Protocol (MCP) server:

```bash
# Start in MCP server mode
npm start
```

## Code Structure

- `src/index.ts` - Core functionality and MCP server implementation
- `src/cli.ts` - Command-line interface implementation
- `src/data_processing.ts` - HTML to Markdown conversion functionality

## API

The tool exports the following functions:

```typescript
// Scrape a website and convert to Markdown
import { scrapeToMarkdown } from './build/index.js';

// Convert HTML string to Markdown directly
import { htmlToMarkdown } from './build/data_processing.js';

async function example() {
  // Web scraping
  const markdown = await scrapeToMarkdown('https://example.com');
  console.log(markdown);
  
  // Direct HTML conversion
  const html = '<h1>Hello World</h1><p>This is <strong>bold</strong> text.</p>';
  const md = htmlToMarkdown(html);
  console.log(md);
}
```

## License

ISC 