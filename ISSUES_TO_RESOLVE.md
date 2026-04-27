# Items before v2.6.0 PR is ready

Punch list to clear before merging to `main`. Update as work lands.

## 1. Awaiting lock-in (work done, just commit)

- [ ] **SDK introduction migration** — `sdk/introduction.mdx` (new) + `docs.json` (sidebar `"introduction"` → `"sdk/introduction"`, two redirects: `/introduction → /` and `/sdk → /sdk/introduction`) + delete `introduction.mdx`. One commit.
- [ ] **Home tab sidebar restructure** — `docs.json` changes: rename "Get Started" → "Welcome", split tutorials into "Tutorials" group, drop "Tutorial:" prefix from sub-groups, wire in "Blank Canvas". One commit.
- [x] Dash tutorial polish — `75cd7fd6`
- [x] Coda tutorial polish — `7f9814b0`
- [x] Blank Canvas pages — `f7f71392`

## 2. In flight

- [ ] **Runtime polish** — 11 modified pages (`runtime/{overview,serve-as-api,storage,context,human-approval,observability,security-and-auth,interfaces,scheduling,deploy,build-a-product}.mdx`). Under review.
- [ ] **Demo OS polish** — 12 modified pages (`demo-os/{overview,rag,knowledge,memory,learning,mcp,context-providers,session-state,human-in-the-loop,multi-agent-teams/text-to-sql,multi-agent-teams/investment}.mdx`). Quick cleanup pass.

## 3. Investigate before commit

- [ ] `_snippets/connect-agent-os-ui.mdx` modified — verify intent or revert.
- [ ] `tutorials/scout/{connect-slack,deploy-to-railway,setup}.mdx` have unstaged paragraph reorders — verify or revert.
- [ ] `videos/agentos-api-scroll.mp4` untracked — commit or move.

## 4. Broken assets (referenced from committed pages)

- [ ] `first-agent.mdx` references `/videos/agentos-connect-workbench.mp4` and `/videos/agentos-chat-workbench.mp4` — add files or remove embeds.
- [ ] `runtime/serve-as-api.mdx` references `/images/runtime/agentos-openapi.png` — add or remove.

## 5. Pre-existing dead links (out of scope, not blocking)

These sit in `deploy/*` and `_legacy/production/*`. Not introduced by this branch.

| File | Dead target |
|------|-------------|
| `deploy/interfaces/{slack,discord,whatsapp,telegram}/overview.mdx` | `/production/templates/overview` (×7) |
| `deploy/introduction.mdx` | `/production/applications/{text-to-sql,research-agent,knowledge-agent}` and `/production/applications` |
| `_legacy/production/{overview,interfaces,templates}/*.mdx` | Various `/production/*` |
