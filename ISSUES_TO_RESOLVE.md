# Issues to resolve before v2.6.0 branch is merged

Tracking side effects from the Home-tab / Production restructure. Address each before merging to `main`.

## 1. Broken `/production/*` links in content pages

The legacy `production/` content was moved to `_legacy/production/` to make room for the new Production section. The old URLs (`/production/templates/*`, `/production/applications/*`, `/production/interfaces/*`, `/production/overview`) now 404. The following files still link to them:

| File | Links |
|------|-------|
| `deploy/introduction.mdx` | 4 links to `/production/applications/{text-to-sql,research-agent,knowledge-agent}` and `/production/applications` |
| `deploy/interfaces/slack/overview.mdx` | 2 links to `/production/templates/overview` |
| `deploy/interfaces/discord/overview.mdx` | 2 links to `/production/templates/overview` |
| `deploy/interfaces/whatsapp/overview.mdx` | 2 links to `/production/templates/overview` |
| `deploy/interfaces/telegram/overview.mdx` | 1 link to `/production/templates/overview` |
| `agent-os/interfaces/telegram/introduction.mdx` | 1 link to `/production/templates/overview` |
| `TBD/2_6_remove/index.mdx` | 1 link to `/production/overview` (file path suggests it's queued for removal anyway) |

**Resolution:** The Deploy tab is being restructured in v2.6.0 — these links should be repointed or removed as part of that work. The `agent-os/` and `TBD/` links need a separate pass.

## 2. Dead redirect destinations in `docs.json`

14 entries in the `redirects` block still point to `/production/*` destinations that now 404. Example:

```
/production/aws/ci-cd → /production/templates/customize-aws/ci-cd   (target now 404)
```

All 14 have source `/production/aws/*` and destination `/production/templates/customize-aws/*`.

**Resolution:** Either update each destination to `/_legacy/production/...` (preserves the redirect chain to dead content — not useful), or delete the 14 entries (cleanest). Recommend delete.

## 3. Orphan `_legacy/production/*` pages still buildable

Mintlify will continue to build and serve every `.mdx` under `_legacy/production/` at `/_legacy/production/...` URLs, even though nothing navigates there. They're reachable to anyone who guesses the URL and will show up in search indexing.

**Resolution:** Either add an `exclude` pattern to `docs.json` (if Mintlify supports it in this version), delete the `_legacy/` tree once the Production section is fleshed out, or move content into `docs.json`'s `navigation` behind a hidden tab.

## 4. Untracked working tree state

`features/` and `tutorials/` were untracked before this branch's work. Both directories now hold branch-specific content. Once the Home tab structure is approved:

- Commit `tutorials/scout/*`
- Commit `production/demo-os/*` (moved from `features/demo-os/*`)
- Remove the empty `features/` directory if it still exists

## 5. Production section stubs need real content

All 8 new top-level Production pages and all Demo OS feature pages currently contain only frontmatter and "Coming soon." Each should become a 1-pager that introduces the topic and links into the SDK / AgentOS / Deploy tabs.

**Priority pages (user-facing):** `production/overview.mdx`, `production/deploy.mdx`, `production/interfaces.mdx`.
