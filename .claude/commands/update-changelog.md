# Update Knowledge Graph Changelog

You are updating the Brain vault changelog to track recent modifications to the knowledge graph.

## Your Task

1. **Identify Recent Changes** - Review the session history to identify:
   - New notes created
   - New connections/links added between existing notes
   - Significant edits to note content
   - Focus only on changes made during THIS session

2. **Read Existing Changelog** - Read `$VAULT_BASE_PATH/CHANGELOG.md` to see the current state

3. **Append New Entry** - Add a new dated entry at the TOP of the changelog with:
   - Date and session identifier
   - List of changes in format: `- [ACTION] Note Title: Brief description (→ Connected to: [[Other Note]])`
   - Keep each entry to 1-2 sentences maximum
   - Use action verbs: CREATED, CONNECTED, UPDATED, LINKED

## Format Example

```markdown
## 2025-10-24 - Session [Brief Description]

- CONNECTED [[Container Resource Limits]] → [[Pod QoS Classes]]: Resource limits determine QoS tier assignment, which controls eviction priority during node pressure.
- CONNECTED [[GitOps]] → [[Infrastructure as Code]]: GitOps operationalizes IaC by treating Git as single source of truth for declarative infrastructure.
- CONNECTED [[Observability]] ↔ [[Incident Response]]: Observability enables rapid incident response; incidents reveal observability gaps.
- CONNECTED [[Blue-Green Deployment]] → [[Zero-Downtime Migration]]: Blue-green pattern provides instant rollback capability while maintaining service availability.
- CONNECTED [[Service Mesh]] → [[Circuit Breaking]]: Service mesh implements circuit breaking at infrastructure level, eliminating application-level complexity.
```

## Important Guidelines

- Only document changes from THIS session
- Be concise - max 2 sentences per change
- Use bidirectional arrows (↔) for mutual connections, directional (→) for one-way
- Group related changes together
- Focus on WHAT was connected and WHY it matters (the insight)
- If no changelog exists, create it with a header explaining its purpose

## Output

After updating, show the user:
1. Number of changes logged
2. The new entry you added
3. Confirmation that CHANGELOG.md was updated
