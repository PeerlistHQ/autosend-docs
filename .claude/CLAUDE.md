# CLAUDE.md - AutoSend Documentation Guidelines

This file provides context and guidelines for Claude Code when working on the AutoSend documentation.

## Project Overview

AutoSend is a developer and marketer-friendly email platform for sending transactional and marketing emails. This repository contains the Mintlify-powered documentation site.

### Key Product Areas

- **Transactional Emails**: API-driven emails (magic links, verifications, order confirmations) with template support and variable substitution
- **Marketing Emails**: Campaign management, contact lists, segments, and sender configuration
- **Email Automations**: Contact-triggered sequences with visual workflow builder, timing controls, and entry/exit conditions
- **Contact Management**: Import, segmentation, custom fields, and bulk operations via API
- **Webhooks**: Real-time event notifications for email delivery, opens, clicks, bounces, and unsubscribes

### Key Terminology

- **Sender**: A verified email address/domain used to send emails
- **Suppression**: Email addresses blocked from receiving emails
- **Unsubscribe Groups**: Categories allowing recipients to opt out of specific email types
- **Custom Fields**: User-defined contact attributes for segmentation

## Documentation Standards

### File Format

- All documentation pages are MDX files with YAML frontmatter
- Configuration is in `docs.json`
- Reusable content lives in `snippets/` directory

### Frontmatter Requirements

Every MDX file must include:

```yaml
---
title: "Page Title"
description: "Brief description for SEO (40-160 characters)"
sidebarTitle: "Sidebar Label"  # Optional, use when sidebar needs shorter text
---
```

### Writing Voice

- Use **second-person** ("you", "your") to address the reader directly
- Be concise and action-oriented
- Prioritize clarity over cleverness

### Content Structure

- Use H2 (`##`) for major sections
- Use H3 (`###`) for subsections
- Include prerequisites at the start of procedural content
- Add troubleshooting sections at the end of complex topics

### Components to Use

```mdx
<!-- Step-by-step tutorials -->
<Steps>
  <Step title="Step Title" titleSize="h3">
    Content here...
  </Step>
</Steps>

<!-- Grid layouts -->
<Columns cols={2}>
  <Card title="Title" icon="envelope" iconType="duotone" href="/path">
    Description
  </Card>
</Columns>

<!-- Multi-language code examples -->
<CodeGroup>
  ```bash cURL
  curl -X POST ...
  ```
  ```javascript NodeJS
  fetch(...)
  ```
</CodeGroup>

<!-- Alerts -->
<Note>Informational highlight</Note>
<Info>Additional context</Info>
<Warning>Important warning</Warning>

<!-- Images -->
<Frame>
  <img src="/images/path.png" alt="Descriptive alt text" />
</Frame>
```

### Code Examples

- Always provide multiple language examples (cURL, JavaScript, Python at minimum)
- Use realistic placeholder values
- Add `expandable` attribute for long code blocks
- Include example responses for API endpoints

### Links and Variables

- Use snippet variables for internal paths: `APP_PATHS.apiKey`
- Use snippet variables for external URLs: `AUTOSEND_PATHS.dashboard`
- Never hardcode URLs that exist in snippets
- Import from snippets: `import { APP_PATHS } from '/snippets/appPaths.mdx'`

### Images

- Store in `/images/` with descriptive subdirectory names
- Always include meaningful alt text
- Wrap in `<Frame>` component

## Protected Files

Do NOT modify these files without explicit approval:

- `docs.json` - Main configuration
- `snippets/*.mdx` - Shared variables and components
- `api-reference/mails/mails-api.json` - OpenAPI specification
- `api-reference/contacts/contacts-api.json` - OpenAPI specification

## Creating New Pages

Always ask before creating new MDX files. When approved:

1. Follow the existing directory structure
2. Add the page to navigation in `docs.json`
3. Use consistent frontmatter format
4. Import required snippets

## Git Workflow

### Commit Convention

Use conventional commits:

- `docs:` - Documentation content changes
- `fix:` - Bug fixes (typos, broken links, formatting)
- `feat:` - New documentation pages or sections
- `refactor:` - Restructuring without content changes
- `chore:` - Maintenance tasks

Examples:
```
docs: add webhook retry documentation
fix: correct API endpoint in send mail example
feat: add Supabase integration guide
```

### Commit Rules

- Never use `--no-verify` flag
- Never disable pre-commit hooks
- Make frequent, atomic commits
- Write clear, descriptive commit messages

## Working with Claude

### Expectations

- Ask clarifying questions rather than making assumptions
- Search existing documentation before creating new content
- Check for consistency with existing patterns
- Never fabricate API endpoints, features, or capabilities

### Before Making Changes

1. Read relevant existing files to understand current patterns
2. Check `snippets/` for reusable variables
3. Verify component usage matches existing pages
4. Ensure changes align with the product's actual capabilities

## Local Development

Preview changes locally:

```bash
npx mintlify dev
```

This starts a local server at `http://localhost:3000`.
