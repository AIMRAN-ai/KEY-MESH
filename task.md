# KeyMesh v2.0 — Task Tracker

## Phase 1: Extended Integration Adapters (Rust Backend)

### New Models & Types
- [x] Extend `IntegrationAppInfo` model with `integration_types`, `capabilities`, `health_score`, `category`
- [x] Add `IntegrationCapabilities` struct
- [x] Add `ShellEnvVisibility` struct
- [x] Add `ConfigurationConflict` struct

### New Adapters
- [x] `integrations/gemini_cli.rs` — Gemini CLI detection
- [x] `integrations/codex_cli.rs` — Codex CLI detection
- [x] `integrations/jetbrains.rs` — JetBrains (IntelliJ, PyCharm, WebStorm) detection
- [x] `integrations/zed.rs` — Zed editor detection
- [x] `integrations/neovim.rs` — Neovim detection + AI plugin heuristic
- [x] `integrations/visual_studio.rs` — Visual Studio detection
- [x] `integrations/terminal.rs` — Shell/terminal env visibility matrix

### Registration
- [x] Update `integrations/mod.rs` — register all new adapters
- [x] Update `commands/integration_cmds.rs` — add shell env scan command
- [x] Update `lib.rs` — register new Tauri commands
- [x] Cargo build verification (Passed)

## Phase 2: Configuration Engine & Apply System (Rust Backend)

### New Models
- [x] `models/apply.rs` — ApplyPreview, ApplyResult, ApplyTarget
- [x] `models/conflict.rs` — ConfigurationConflict, CredentialResolution
- [x] Extend `models/health.rs` — SystemHealthReport, HealthIssue

### New Engines
- [x] `engine/apply_engine.rs` — Apply config to integrations (with dry-run preview)
- [x] `engine/conflict_engine.rs` — Detect credential conflicts, resolve precedence
- [x] `engine/sync_engine.rs` — "Configure All" multi-target sync
- [x] `engine/health_engine.rs` — System-wide health score computation

### New Commands
- [x] `commands/apply_cmds.rs` — apply, preview, sync
- [x] `commands/conflict_cmds.rs` — detect, resolve
- [x] `commands/health_cmds.rs` — system health scan
- [x] Update `lib.rs` with Phase 2 commands
- [x] Cargo build verification (Passed)

## Phase 3: Frontend — Integration Hub & Pages

### New Services
- [x] `services/apply.ts` — apply/preview/sync
- [x] `services/health.ts` — system health
- [x] `services/conflict.ts` — conflict detection
- [x] `services/shell.ts` — shell env scanning

### New Types
- [x] `types/apply.ts`
- [x] `types/health.ts`
- [x] `types/conflict.ts`
- [x] `types/integration.ts`

### New/Rebuilt Pages
- [x] Rebuild `IdeIntegration.tsx` → `IntegrationHub` (categorized grid, live badges, health bars)
- [x] `ConfigureAll.tsx` — multi-step wizard with progress
- [x] `SystemDoctor.tsx` — full-machine health scan page
- [x] `ConflictResolver.tsx` — credential conflict viewer
- [x] `ShellManager.tsx` — shell env visibility matrix

### Updated Pages
- [x] `Dashboard.tsx` — live data from health engine, real counts
- [x] `Sidebar.tsx` — grouped navigation
- [x] `App.tsx` — new routes

### Updated Services
- [x] `services/integration.ts` — all 12 adapters registered

## Final Verification
- [x] `cargo check` passes
- [x] `npm run build` verification
