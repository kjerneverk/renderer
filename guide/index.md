# RiotPlan Renderer Guide

## Overview

The `@riotprompt/riotplan-renderer` package provides functions to render RiotPlan plans to various output formats including Markdown, JSON, and HTML.

## Installation

```bash
npm install @riotprompt/riotplan-renderer
```

## Usage

### Basic Rendering

```typescript
import { renderPlan } from "@riotprompt/riotplan-renderer";
import { loadPlan } from "@riotprompt/riotplan";

const plan = await loadPlan("./my-plan");

// Render to Markdown
const mdResult = renderPlan(plan, { format: "markdown" });
console.log(mdResult.content);

// Render to JSON
const jsonResult = renderPlan(plan, { format: "json" });
console.log(jsonResult.content);

// Render to HTML
const htmlResult = renderPlan(plan, { format: "html" });
console.log(htmlResult.content);
```

### Format-Specific Rendering

```typescript
import { 
    renderToMarkdown, 
    renderToJson, 
    renderToHtml 
} from "@riotprompt/riotplan-renderer";

// Markdown with options
const markdown = renderToMarkdown(plan, {
    includeMetadata: true,
    useTaskList: true,
    includeFeedback: true,
});

// JSON with options
const json = renderToJson(plan, {
    pretty: true,
    indent: 4,
    includeStepContent: true,
});

// HTML with options
const html = renderToHtml(plan, {
    theme: "dark",
    includeStyles: true,
    fullDocument: true,
});
```

## Output Formats

### Markdown

The Markdown renderer produces clean, readable markdown suitable for documentation.

**Options:**
- `includeMetadata` - Include plan metadata section
- `includeStepDetails` - Include step descriptions
- `includeFeedback` - Include feedback records
- `includeEvidence` - Include evidence records
- `useTaskList` - Use `- [x]` task list format for steps
- `includeToc` - Include table of contents

### JSON

The JSON renderer produces structured JSON suitable for data processing.

**Options:**
- `pretty` - Pretty print with indentation
- `indent` - Indentation level (default: 2)
- `includeStepContent` - Include full step file content
- `includeFeedback` - Include feedback records
- `includeEvidence` - Include evidence records
- `fields` - Only include specific fields

### HTML

The HTML renderer produces styled HTML suitable for viewing in a browser.

**Options:**
- `fullDocument` - Include full HTML document structure
- `title` - Custom document title
- `includeStyles` - Include inline CSS
- `theme` - Color theme: "light" or "dark"
- `includeStepDetails` - Include step descriptions
- `includeFeedback` - Include feedback section
- `includeEvidence` - Include evidence section

## Examples

### Export to File

```typescript
import { writeFile } from "node:fs/promises";
import { renderToHtml } from "@riotprompt/riotplan-renderer";

const html = renderToHtml(plan, { theme: "dark" });
await writeFile("plan-report.html", html);
```

### Create JSON Export

```typescript
import { renderToJson } from "@riotprompt/riotplan-renderer";

const json = renderToJson(plan, {
    fields: ["metadata", "status", "steps"],
    pretty: true,
});
```

### Generate Task List

```typescript
import { renderToMarkdown } from "@riotprompt/riotplan-renderer";

const taskList = renderToMarkdown(plan, {
    useTaskList: true,
    includeMetadata: false,
});
```

