# @riotprompt/riotplan-renderer

Render RiotPlan plans to various output formats (Markdown, JSON, HTML).

## Installation

```bash
npm install @riotprompt/riotplan-renderer
```

## Usage

```typescript
import { renderPlan, renderToMarkdown, renderToJson, renderToHtml } from "@riotprompt/riotplan-renderer";
import { loadPlan } from "@riotprompt/riotplan";

const plan = await loadPlan("./my-plan");

// Generic render
const result = renderPlan(plan, { format: "markdown" });

// Format-specific
const markdown = renderToMarkdown(plan, { useTaskList: true });
const json = renderToJson(plan, { pretty: true });
const html = renderToHtml(plan, { theme: "dark" });
```

## Formats

- **Markdown** - Clean documentation format
- **JSON** - Structured data export
- **HTML** - Styled web view with light/dark themes

## License

MIT

<!-- v1.0.0 -->

