# Assignment 02 — Requirements

**v1.0 — 2026-11-06**

## A. Daily notes and outliner
- Automatically create or open a daily page.
- Create, edit, delete, indent, outdent, reorder nested bullets.
- Basic Markdown and navigation between dates.
- Each bullet is an independently addressable record.

**Example page (illustrative)**

```text
November 6, 2026
- ON Labs
  - Discuss assessment engine architecture
  - Finalize database schema
- Product Development
  - Review Career Vault
- Personal
  - Follow up on pending tasks
```

## B. Structured knowledge

| Node type | Example |
|---|---|
| Text | General note |
| Task | Complete database schema |
| Meeting | Product architecture discussion |
| Idea | New product concept |
| Decision | Select PostgreSQL |
| Link | Reference to another note |

Each node has a stable identifier, parent-child relationship, type, content, ordering.

## C. AI assistant (implement at least three)
- **Summarization:** concise summary from a long daily note.
- **Structured extraction:** tasks, owners, dates, decisions, follow-ups.
- **Tagging and classification:** categories such as Product, Engineering, Meeting, Ideas, Tasks, Personal.

Example input: "Discussed with the engineering team. Finish the assessment database schema by Friday. Rahul will handle backend APIs."

AI suggestions must be reviewable and editable before they change stored data. Preserve the original note.

## D. Search and retrieval
- Keyword search across notes.
- Filter by date, node type, tags.
- Bonus: semantic search.

## E. Local-first behaviour
- Persist locally in IndexedDB or equivalent.
- Create, edit, delete, browse offline.
- Data survives refresh and browser restart.
- Queue pending changes; sync when connectivity returns.
- Show online/offline and sync status.

AI may need internet. Core note-taking must not.

## Database (mandatory)

| Entity | Purpose |
|---|---|
| users / workspaces | Identity and data container |
| daily_notes | Daily page metadata |
| nodes | Hierarchical content |
| node_types | Node classifications |
| tags / node_tags | Tagging, many-to-many |
| ai_jobs | AI requests and status |
| ai_outputs | Generated summaries and extractions |
| sync_operations | Pending or tracked mutations |
| devices | Registered sync clients |

Provide ER diagram, schema, indexes, constraints, sample queries. Explain hierarchy, ordering, deletion, AI-output provenance, local/remote sync.

## AI architecture

```ts
interface AIProvider {
  summarize(input: string): Promise<string>;
  extractStructuredData(input: string): Promise<StructuredExtraction>;
  classify(input: string): Promise<string[]>;
}
```

- Validate AI output against a defined schema.
- Handle provider failures and timeouts.
- Preserve original user content; user reviews before applying.
- Avoid duplicate processing where practical.
- Provider credentials stay on the server, never in the frontend.
- A mock provider is acceptable if clearly documented.

## Sync and offline scenarios
- Create and edit offline, refresh, verify persistence.
- Reconnect and sync pending changes.
- Open the same account in another browser or device; verify updates.
- Explain handling of simultaneous edits and deletion conflicts.
- Document retry, duplicate-operation, and cursor or version behaviour.

A full CRDT is not required. A clearly explained basic strategy is enough.

## API scope
- Create and fetch daily notes.
- Create, update, delete nodes.
- Search; filter by date, type, tag.
- Generate summary, extraction, tags.
- Push pending sync changes; pull remote changes.
