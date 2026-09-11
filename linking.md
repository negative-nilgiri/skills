---
name: linking
description: Apply repository-aware file linking rules whenever producing links or references to local project files for use outside the local filesystem, and use same-message heading links to improve navigation within long, structured Markdown responses. Never expose local absolute paths.
---

# File Linking Rules

Never expose local absolute paths such as `/Users/negativenigiri/...`.

## Rules

1. Determine the Git repository containing the file.
2. If the file is committed and available remotely:
   - If the intended reference is to the version on `main`, use:
     `https://github.com/<owner>/<repo>/blob/main/<path>`
   - If the file is committed on another branch:
     - Prefer a commit permalink when the reference should remain stable:
       `https://github.com/<owner>/<repo>/blob/<commit_sha>/<path>`
     - Use the current branch URL when intentionally referring to the evolving version on that branch:
       `https://github.com/<owner>/<repo>/blob/<branch>/<path>`
3. If the file is not committed or is not available remotely, use its path relative to the repository root.
4. Never include the local repository prefix or a `/Users/...` path in the resulting reference.

## Examples

### Committed on `main`

Local file:

`/Users/negativenigiri/Documents/stxr_monorepo/knowledge-base/docs/issues/records/ISS-07HF7-static-mkt-info.md`

Link:

`https://github.com/stxr-prop/knowledge-base/blob/main/docs/issues/records/ISS-07HF7-static-mkt-info.md`

### Committed on a feature branch

Local file:

`/Users/negativenigiri/Documents/stxr_monorepo/prototypes/data-feeds-code-generator/notes/dynamic_filtering.md`

Prefer a stable commit permalink when the reference should survive branch deletion or branch movement:

`https://github.com/stxr-prop/<repo>/blob/<commit_sha>/notes/dynamic_filtering.md`

If intentionally referring to the current branch version, use:

`https://github.com/stxr-prop/<repo>/blob/datafeeds-codegen/notes/dynamic_filtering.md`

### Not committed

Local file:

`/Users/negativenigiri/Documents/stxr_monorepo/prototypes/data-feeds-code-generator/prompts/e2e_prototype.md`

Link:

`prompts/e2e_prototype.md`

# Navigable Conversation Messages

The session viewer supports navigation within individual Markdown messages:

- Messages containing at least two headings automatically receive an **Outline** control.
- Standard fragment links such as `[Architecture](#architecture)` resolve to headings inside the current message.
- Heading anchors are scoped by the viewer, so headings such as `Summary` may safely appear in multiple messages.
- Do not generate viewer-specific IDs or explicit HTML anchors.
- Use ordinary Markdown headings and fragment links.
- Same-message fragment links navigate only within the current message. Do not treat them as durable references to another message or session.
- Do not generate a table of contents. The viewer already provides an outline.

## Cross-section References

Leverage same-message heading links naturally in long, structured responses.

When one part of a response refers to details, evidence, caveats, trade-offs, instructions, or conclusions contained under another heading in the same message, make the reference a Markdown fragment link when doing so improves navigation.

Prefer this:

```markdown
The importer behavior is explained under
[Synchronization](#synchronization).

## Synchronization

...
```

over this:

```markdown
The importer behavior is explained under the Synchronization section.
```

Do not add links mechanically. Use them when they save the reader from searching through a substantial response or when the referenced section is not immediately adjacent.

Use meaningful link text that identifies the destination section.

## Fragment Format

Use heading fragments that match the viewer's Markdown heading anchors:

- Use lowercase.
- Replace spaces with hyphens.
- Omit heading punctuation.
- Do not invent custom IDs.

Examples:

```markdown
## Data Flow
[Data flow](#data-flow)

## Trade-offs
[Trade-offs](#trade-offs)

## Error Handling & Retries
[Error handling & retries](#error-handling-retries)
```