# Papercuts

Small, non-blocking friction encountered while working in this repository. Log it in the moment; review and fix entries in a separate, user-requested cleanup pass.

This is not a completed-work log or a bug tracker. Never include secrets, credentials, personal data, or raw customer payloads.

## Open

- [ ] `2026-07-12T21:38:25Z` — `codex` — While validating a Cloudflare self-hosted deployment, the Workers control plane intermittently returned HTML `521`/`522`/`523` responses to tail, dashboard, and trigger-deploy API requests. The Worker upload still completed, but Wrangler exited non-zero after the trigger step. Surface partial deployment success more clearly and document retry guidance for transient control-plane failures.
- [ ] `2026-07-12T21:26:16Z` — `codex` — While following the in-app Codex MCP setup command, the Homebrew `codex` launcher failed because its packaged platform binary was missing (`ENOENT`), while the Codex desktop-bundled CLI worked. Document the desktop CLI fallback or repair the global launcher so `codex mcp add` works as shown.
- [ ] `2026-07-12T21:17:29Z` — `codex` — While deploying to a new Cloudflare account, Wrangler uploaded the build and then failed with API code `10063` because no `workers.dev` subdomain existed; opening Workers & Pages once creates it. Add this first-account prerequisite before the deploy command to avoid a late failure after migrations, build, and asset upload.
- [ ] `2026-07-12T21:08:12Z` — `codex` — While following the manual Cloudflare self-hosting guide on a new account, R2 bucket creation failed with API code `10042` because R2 must first be enabled in the dashboard. Add this prerequisite before the resource-creation commands so first-time deployers do not hit an avoidable stop.
- [ ] `2026-07-12T21:00:22Z` — `codex` — While retrying first-time dependency installation, the older global pnpm launcher could not auto-switch to the repository-pinned pnpm `10.30.1` because its managed binary was missing and Corepack was unavailable. Document a no-global-change fallback such as running the pinned pnpm version through `npx`.
- [ ] `2026-07-12T21:00:02Z` — `codex` — While installing dependencies from a clean fork of `main`, `pnpm install --frozen-lockfile` failed because the committed overrides configuration does not match the lockfile. Regenerate and commit the lockfile, or document that first-time setup currently requires `pnpm install --no-frozen-lockfile`.
- [ ] `2026-07-10T21:09:27Z` — `codex` — While building the TanStack/Cloudflare badseo app, Wrangler reported an EPERM writing its debug log under the user preferences directory even though the build succeeded. Set `WRANGLER_LOG_PATH` to a writable temporary path in sandboxed build commands or make the logging failure non-fatal and quiet.
- [ ] `2026-07-10T17:53:20Z` — `codex` — While validating `.greptile/`, both `pnpm exec prettier --check` and the existing `pnpm format:check` attempted to reconcile `node_modules` and aborted because no TTY was available. Calling `node_modules/.bin/prettier` performed the non-installing check successfully; the agent/CI path needs a stable way to run package scripts without an interactive modules purge.
- [ ] `2026-07-10T18:12:35Z` — `codex` — While validating referenced files in zsh, using `path` as a loop variable overwrote zsh's special `path` array and made commands such as `git`, `jq`, and `sed` appear missing later in the same shell. Use a neutral name such as `file_path` in shell loops.

## Resolved

Move fixed entries here, mark them checked, and append the resolving date or commit.
