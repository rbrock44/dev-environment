# Workspaces

VS Code multi-root workspace files. Paths are relative (`../../<repo>`), so they assume every
repo sits as a sibling under `C:\workspace`. Open one with **File → Open Workspace from File**,
then accept the extension recommendations prompt.

## home-page.code-workspace

The home page and everything feeding it.

| Folder | Stack |
| --- | --- |
| `home-page` | Angular |
| `home-page-api` | Kotlin / Spring Boot (Gradle) |
| `home-page-media-scraper` | Kotlin (Gradle) |
| `home-page-media-file` | data only — `media.txt` |

Mixed Angular + Kotlin, so this one pulls in the Kotlin and Gradle extensions alongside the
Angular language service.

## cleaning-schedule.code-workspace

| Folder | Stack |
| --- | --- |
| `cleaning-schedule` | Angular |
| `home-page-api` | Kotlin / Spring Boot (Gradle) |

`home-page-api` is here because it is the backend — `CleaningScheduleController.kt` and
`CleaningScheduleService.kt` live in it. The `home-page` **frontend** has no cleaning-schedule
code, so it is deliberately not in this workspace.

Two related repos are not included because they are not cloned locally —
[cleaning-schedule-database](https://github.com/rbrock44/cleaning-schedule-database) (the h2
backup) and
[cleaning-schedule-backup-sync](https://github.com/rbrock44/cleaning-schedule-backup-sync)
(syncs the h2 database from `home-page-api` into it). Clone them next to the others and add a
folder entry if you want the full picture.

## websites.code-workspace

All 16 sites listed in the `directory` app, plus `directory` itself at the top.

All Angular except **Connect 4**, which is React + Vite — its folder name says so, since the
distinction matters when running commands across the workspace.

Two entries in `directory` are not included because they are not cloned locally:
[lost](https://github.com/rbrock44/lost) and
[drive-status](https://github.com/rbrock44/drive-status) (the latter is commented out in
`directory` anyway).

## Extensions

Common to all three:

| Extension | Why |
| --- | --- |
| `angular.ng-template` | Angular language service |
| `github.vscode-github-actions` | every repo deploys via Actions |
| `editorconfig.editorconfig` | `.editorconfig` is present in several repos |
| `github.copilot` / `github.copilot-chat` | picks up `.github/copilot-instructions.md` |
| `anthropic.claude-code` | picks up `CLAUDE.md` |

Kotlin workspaces add `fwcd.kotlin`, `vscjava.vscode-gradle`, and `vscjava.vscode-java-pack`
(the Kotlin language server needs a JDK toolchain to resolve Gradle dependencies).

The websites workspace adds `dbaeumer.vscode-eslint` (configured in `auction-advisor`,
`connect-4`, `scorekeeping-by-rounds`), `esbenp.prettier-vscode` (`blog`, `puzzles`), and
`yzhang.markdown-all-in-one` for the blog's markdown posts. These only apply to the repos that
actually configure them — the extensions stay quiet elsewhere.

## Settings

Each workspace sets Git Bash as the default terminal, matching the IntelliJ terminal config in
`../ide/intellij/options/terminal.xml`, and excludes build output (`node_modules`, `dist`,
`.angular`, `build`, `out`, `.gradle`) from the file tree and search. With 16 Angular repos
open at once, leaving `node_modules` searchable makes find-in-files unusable.
